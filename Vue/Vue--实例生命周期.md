# Vue实例生命周期



* 首先这是官网的图示

   <img src="https://cn.vuejs.org/images/lifecycle.png" style="zoom: 25%;" />

* 有许多钩子函数 可以在生命周期中调用

    | 钩子函数      | 描述                                                         |
    | ------------- | ------------------------------------------------------------ |
    | beforeCreate  | 在实例初始化之后，数据观测（data observer）和 event/watch事件配置之前被调用 |
    | created       | 在实例创建完成后立即被调用，在这一步实例已经完成了：数据观测、属性和方法的运算和 event/watch事件的回调，但是$el属性目前不可见。 |
    | beforeMount   | 在挂载开始之前被调用                                         |
    | mounted       | 在挂载成功后被调用，el被新创建的vm.$el替换                   |
    | beforeUpdate  | 数据更新之前调用                                             |
    | update        | 数据更新完成时调用，组件dom已经更新                          |
    | beforeDestory | 组件销毁前调用                                               |
    | destoryed     | 组件销毁后调用                                               |

   

* 小例子

    

  ```javascript
    <template>
            <el-table
                :data="tableData"
                stripe
                style="width: 100%">
              <el-table-column
                  prop="id"
                  label="id"
                  width="180">
              </el-table-column>
              <el-table-column
                  prop="fname"
                  label="文件名"
                  width="180">
              </el-table-column>
              <el-table-column
                  prop="operation"
                  label="操作">
                <template slot-scope="scope">
                  <el-button @click="handleClick(scope.row)" type="text" size="small">下载</el-button>
                </template>
              </el-table-column>
            </el-table>
          </template>
  <script>
  export default {
    data() {
      return {
        tableData: [{
          date: '2016-05-02',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄'
        }]
      };
    },
    mounted() {
    this.getFileList();
  },
    methods: {
      async getFileList() {
        let res = await this.$http.get('/list');
        this.tableData = res.data.data;
      }
    }
  }
  </script>
  ```

  

------

结合代码理解钩子函数

```html
<template>
  <div>
    <p>{{ message }}</p>
  </div>
</template>
<script type="text/javascript">
  export default {
    data(){
      return{
        message : "钩子函数小测试"
      }
    },
    beforeCreate(){
      console.group('beforeCreate 创建前状态 ------------>');
      console.log("%c%s", "color:red" , "el     : " + this.$el); //undefined
      console.log("%c%s", "color:red","data   : " + this.$data); //undefined
      console.log("%c%s", "color:red","message: " + this.message)
    },
    created() {
      console.group('created 创建完毕状态 ------------>');
      console.log("%c%s", "color:red","el     : " + this.$el); //undefined
      console.log("%c%s", "color:red","data   : " + this.$data); //已被初始化
      console.log("%c%s", "color:red","message: " + this.message); //已被初始化
    },
    beforeMount() {
      console.group('beforeMount 挂载前状态 ------------>');
      console.log("%c%s", "color:red","el     : " + (this.$el)); //已被初始化
      console.log("%c%s", "color:red","data   : " + this.$data); //已被初始化
      console.log("%c%s", "color:red","message: " + this.message); //已被初始化
    },
    mounted() {
      console.group('mounted 挂载结束状态 ------------>');
      console.log("%c%s", "color:red","el     : " + this.$el); //已被初始化
      console.log(this.$el);
      console.log("%c%s", "color:red","data   : " + this.$data); //已被初始化
      console.log("%c%s", "color:red","message: " + this.message); //已被初始化
    },
    beforeUpdate() {
      console.group('beforeUpdate 更新前状态 ------------>');
      console.log("%c%s", "color:red","el     : " + this.$el);
      console.log(this.$el);
      console.log('真实dom结构：' + document.getElementById('app').innerHTML);
      console.log("%c%s", "color:red","data   : " + this.$data);
      console.log("%c%s", "color:red","message: " + this.message);
    },
    updated() {
      console.group('updated 更新完成状态 ------------>');
      console.log("%c%s", "color:red","el     : " + this.$el);
      console.log(this.$el);
      console.log('真实dom结构：' + document.getElementById('app').innerHTML);
      console.log("%c%s", "color:red","data   : " + this.$data);
      console.log("%c%s", "color:red","message: " + this.message);
    },
    beforeDestroy() {
      console.group('beforeDestroy 销毁前状态 ------------>');
      console.log("%c%s", "color:red","el     : " + this.$el);
      console.log(this.$el);
      console.log("%c%s", "color:red","data   : " + this.$data);
      console.log("%c%s", "color:red","message: " + this.message);
    },
    destroyed() {
      console.group('destroyed 销毁完成状态 ------------>');
      console.log("%c%s", "color:red","el     : " + this.$el);
      console.log(this.$el);
      console.log("%c%s", "color:red","data   : " + this.$data);
      console.log("%c%s", "color:red","message: " + this.message)
    }
  }
</script>
```

