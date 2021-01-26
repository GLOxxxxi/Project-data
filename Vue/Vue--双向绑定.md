# Vue--双向绑定

1. ### v-model 双向绑定
  ```html
  <div id="div1">
     
    hero name: <input v-model="name" >
    <button @click="doClick" >提交数据</button>
     
  </div>
    
  <script>
  
   new Vue({
      el: '#div1',
      data:{
        name:"teemo"
      },
      methods:{
          doClick:function(){
              alert(this.name);
          }
      }
    })
    
  </script>
  ```
2. ### 多种风格数据的绑定
  ```html
  <style>
table tr td{
    border:1px solid gray;
    padding:10px;
     
}
table{
    border-collapse:collapse;
    width:800px;
    table-layout:fixed;
}
tr.firstLine{
    background-color: lightGray;
}
</style>
  
<div id="div1">
    
    <table align="center" >
        <tr class="firstLine">
            <td>视图类型</td>
            <td>输入数据</td>
            <td>绑定到Vue上的数值</td>
        </tr>       
        <tr>
            <td>
                单行文本
            </td>
            <td>
                <input v-model="input" placeholder="输入数据">
            </td>
            <td>
                <p>{{ input }}</p>   
            </td>
        </tr>
        <tr>
            <td>
                多行文本
            </td>
            <td>
                <textarea v-model="textarea" placeholder="输入数据"></textarea>
            </td>
            <td>
                <p>{{ textarea }}</p>   
            </td>
        </tr>
        <tr>
            <td>
                单个复选框
            </td>
            <td>
                <input type="checkbox" id="checkbox" v-model="checked">
            </td>
            <td>
                <p>{{ checked }}</p>   
            </td>
        </tr>
        <tr>
            <td>
                多个复选框
            </td>
            <td>
                  <input type="checkbox" id="teemo" value="teemo" v-model="checkedes">
                  <label for="teemo">teemo</label>
                  <input type="checkbox" id="gareen" value="gareen" v-model="checkedes">
                  <label for="gareen">gareen</label>
                  <input type="checkbox" id="annie" value="annie" v-model="checkedes">
                  <label for="annie">annie</label>
            </td>
            <td>
                <p>{{ checkedes }}</p>   
            </td>
        </tr>
        <tr>
            <td>
                单选按钮
            </td>
            <td>
              <input type="radio" id="one" value="One" v-model="radio">
              <label for="one">One</label>
              <br>
              <input type="radio" id="two" value="Two" v-model="radio">
              <label for="two">Two</label>
            </td>
            <td>
                <p>{{ radio }}</p>   
            </td>
        </tr>
        <tr>
            <td>
                单选选择框
            </td>
            <td>
              <select v-model="selected" size="5">
                <option disabled value="">请选择</option>
                <option>AD</option>
                <option>AC</option>
                <option>ADC</option>
              </select>
            </td>
            <td>
                <p>{{ selected }}</p>   
            </td>
        </tr>
        <tr>
            <td>
                多选选择框
            </td>
            <td>
              (通过ctrl或者shift进行多选)<br>
              <select v-model="selecteds" multiple size="5">
                <option disabled value="">请选择</option>
                <option>AD</option>
                <option>AC</option>
                <option>ADC</option>
              </select>
            </td>
            <td>
                <p>{{ selecteds }}</p>   
            </td>
        </tr>
        <tr>
            <td>
                单个复选框
            </td>
            <td>
                默认值是true或者false,也可以修改为自定义的值<br>
                <input type="checkbox" id="toggle" true-value="yes" false-value="no" v-model="toggle">
            </td>
            <td>
                <p>{{ toggle }}</p>   
            </td>
        </tr>       
 
    </table>
  
</div>
     
<script>
   
new Vue({
      el: '#div1',
      data: {
          input:'',
          textarea:'',
          checked:'',
          checkedes:[],
          radio:'',
          selected:'',
          selecteds:[],
          toggle:'',
           
      }
    })
     
</script>
  ```
3. ### 修饰符
    vue.js 还提供了一些修饰符方便用户操作，常见的有
    - **.lazy**
    - **.number**
    - **.trim**
    
4. ### 修饰符 .lazy
    对于输入元素，默认的行为方式是一旦有数据变化，马上进行绑定。
但是加上.lazy之后，相当于监听change操作，只有在失去焦点的时候，才会进行数据绑定了
    
    ```html
     <td>
       <input v-model.lazy="input1" placeholder="输入数据">
     </td>
     <td>
       <p>{{ input1 }}</p>   
     </td>
    ```
    
    
    
5. ### 修饰符 .number
    有时候，拿到了数据需要进行数学运算， 为了保证运算结果，必须先把类型转换为number类型，而v-model默认是string类型，所以就可以通过.number方式确保获取到的是数字类型了。
  ```html
   <td>
     <input v-model.number="input1" type="number" placeholder="输入数据">
   </td>
   <td>
      <p>{{ input1 }}</p>  
   </td>
  ```
6. ### 修饰符 .trim
    trim 去掉前后的空白
  ```html
  <td>
     <input v-model.trim="input" placeholder="输入数据">
  </td>
  <td>
     <p>"{{ input }}"</p>  
  </td>
  ```