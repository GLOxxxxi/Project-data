# Vue--路由

### 1.路由的概念

路由相当于就是局部刷新。

### 2. 代码解释

```html
<div id="app">
    <div class="menu">
        <!--
            router-link 相当于就是超链
            to 相当于就是 href
        -->
        <router-link to="/user">用户管理</router-link>
        <router-link to="/product">产品管理</router-link>
        <router-link to="/order">订单管理</router-link>
    </div>
     
    <div class="workingRoom">
        <!--
            点击上面的/user,那么/user 对应的内容就会显示在router-view 这里
         -->
         <router-view></router-view>   
    </div>
 
</div>
<script>
    /*
    * 申明三个模板( html 片段 )
    */
    var user = { template: '<p>用户管理页面的内容</p>' };
    var second = { template: '<p>产品管理页面的内容</p>' };
    var order = { template: '<p>订单管理页面的内容</p>' };
    /*
    * 定义路由
    */
    var routes = [
        { path: '/', redirect: '/user'}, // 这个表示会默认渲染 /user，没有这个就是空白
        { path: '/user', component: user },
        { path: '/product', component: second },
        { path: '/order', component: order }
    ];
    /*
    * 创建VueRouter实例
    */
    var router = new VueRouter({
        routes:routes
    });
    /*
    * 给vue对象绑定路由
    */
    new Vue({
        el:"#app",
        router
    })
 
</script>
```



