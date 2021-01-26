# Vue--组件

### 1. 组件是什么

  只用做一个模板，然后照着这个模板，传递不同的参数就可以看到不同的产品展示了。

这个模板，就是组件。例如图中圈起来的模块:

![组件.png](http://ww1.sinaimg.cn/large/005K7ebXgy1gmm4xvojg5j30iq04fdg2.jpg)

### 2. 局部组件

* 在 Vue对象里增加 components：

```js
 components:{
	  'product':{
		  template:'<div class="product" >MAXFEEL休闲男士手包真皮手拿包大容量信封包手抓包夹包软韩版潮</div>'
	  }
```

* 在视图中如下调用

  `<product></product>`

* 可以重复调用

  `<product></product>`

  `<product></product>`

  `<product></product>`

  

### 3. 全局组件

和过滤器一样注册:

```js
Vue.component('product', {
	  template: '<div class="product" >MAXFEEL休闲男士手包真皮手拿包大容量信封包手抓包夹包软韩版潮</div>'
	})
```

### 4. 参数

前面的例子中模板是固定的，不利于真正的生产开发，于是设置参数

设置参数name, 并且在组件里使用这个name:

```js
Vue.component('product', {
	  props:['name'],
	  template: '<div class="product" >{{name}}</div>'
	})
```

调用方法:

`<product name="MAXFEEL休闲男士手包真皮手拿包大容量信封包手抓包夹包软韩版潮"></product>`

当做自定义属性进行传值

### 5. 动态参数

所谓的动态参数，就是指组件内的参数可以和组件外的值关联起来
如效果所示，在组件外的input输入数据，就可以传递到组件内了
关键是这一行，name表示组件内的属性name, outName就是组件外的

```html
<div id="div1">
	组件外的值：<input v-model="outName" ><br>
    <product v-bind:name="outName"></product>
</div>
 
<script>
Vue.component('product', {
	  props:['name'],
	  template: '<div class="product" >{{name}}</div>'
	})

new Vue({
  el: '#div1',
  data:{
	  outName:'产品名称'
  }
})
</script>
```

### 6. 自定义事件

增加自定义事件和在一个Vue对象上增加 methods 是一样的做法
先来个methods:

```js
  methods:{
	  increaseSale:function(){
		  this.sale++
	  }
  }
```

然后在组件里:

`v-on:click="increaseSale"`

### 7. 遍历json数组

大部分时候是拿到一个 json 数组，然后遍历这个 json 数组为多个组件实例。

1. 首先准备产品数组

   ```json
     products:[
               {"name":"MAXFEEL休闲男士手包真皮手拿包大容量信封包手抓包夹包软韩版潮","sale":"18"},
               {"name":"宾度 男士手包真皮大容量手拿包牛皮个性潮男包手抓包软皮信封包","sale":"35"},
               {"name":"唯美诺新款男士手包男包真皮大容量小羊皮手拿包信封包软皮夹包潮","sale":"29"}
               ]
   ```

   

2. 然后在视图里通过 v-for 遍历 products

   ` <product v-for="item in products" v-bind:product="item"></product>`

3. 接着修改组件，让接受的参数为 v-bind:product 里的这个 product，显示和方法里也通过 product.xxx 来调用。

   ```js
   Vue.component('product', {
   	  props:['product'],
   	  template: '<div class="product" v-on:click="increaseSale">{{product.name}} 销量: {{product.sale}} </div>',
   	  methods:{
   		  increaseSale:function(){
   			  this.product.sale++
   		  }
   	  }
   	})
   ```

   

### 8. 复杂的实现

 template 部分因为比较复杂，就不好写在一个 单引号 ' ' 里维护起来，所以就直接写在html里，然后通过html dom 获取出来，这样编写起来略微容易一点。

```html
 
<div id="tempalate" style="display:none">
    <div class="product" v-on:click="increaseSales">
        <div class="price">
                    ¥ {{product.price}}
        </div>
        <div class="productName">
            {{product.name}}
        </div>
        <div class="sale"> 月成交 {{product.sale}} 笔</div>
        <div class="review"> 评价 {{product.review}} </div>
    </div>
</div>
 
<div id="div1">
    <product v-for="item in products" v-bind:product="item"></product>
</div>
  
<script>
var tempalateDiv=document.getElementById("tempalate").innerHTML;
var templateObject = {
    props: ['product'],
    template: tempalateDiv,
      methods: {
            increaseSales: function () {
                this.product.sale = parseInt(this.product.sale);
              this.product.sale += 1
              this.$emit('increment')
            }
          }
 
}
 
Vue.component('product', templateObject)
 
new Vue({
  el: '#div1',
  data:{
      products:[
                {"name":"MAXFEEL休闲男士手包真皮手拿包大容量信封包手抓包夹包软韩版潮","price":"889","sale":"18","review":"5"},
                {"name":"宾度 男士手包真皮大容量手拿包牛皮个性潮男包手抓包软皮信封包","price":"322","sale":"35","review":"12"},
                {"name":"唯美诺新款男士手包男包真皮大容量小羊皮手拿包信封包软皮夹包潮","price":"523","sale":"29","review":"3"},
                ]
  }
})
</script>

```

