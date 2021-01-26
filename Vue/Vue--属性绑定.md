# Vue--属性绑定

1. ### v-bind 做属性绑定
  ```html
  <div id="div1">
    <a v-bind:href="page">http://12306.com</a>
</div>
    
<script>
  
new Vue({
      el: '#div1',
      data:{
          page:'http://12306.com'
      }
    })
    
</script>
  ```
2. ### v-bind:href 简写成 :href

  ` <a :href="page">http://12306.com</a>`