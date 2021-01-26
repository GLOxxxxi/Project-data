# Vue--过滤器

1. 一个过滤器
   * 首先定义一个过滤器
   ```js
       filters:{
    	  capitalize:function(value) {
    		    if (!value) return '' //如果为空，则返回空字符串
    		    value = value.toString()
    		    return value.charAt(0).toUpperCase() + value.substring(1)
          }
      }
   ```
   
   * 在视图中使用
   
     ` {{ data|capitalize }}`

2. 多个过滤器
   
   * `{{ data|capitalize|capitalizeLastLetter }}`
   
3. 全局过滤器

   上面的例子里可以看到，过滤器是定义在Vue对象里的。 但是有时候，很多不同的页面都会用到相同的过滤器，如果每个Vue对象里都重复开发相同的过滤器，不仅开发量增加，维护负担也增加了。
   所以就可以通过全局过滤器的方式，只定义一次过滤器，然后就可以在不同的Vue对象里使用了。
   注册全局过滤器：

   ```js
   Vue.filter('capitalize', function (value) {
   	if (!value) return ''
   	value = value.toString()
   	return value.charAt(0).toUpperCase() + value.slice(1)
   })
   Vue.filter('capitalizeLastLetter', function (value) {
   	if (!value) return '' //如果为空，则返回空字符串
   	value = value.toString()
   	return value.substring(0,value.length-1)+ value.charAt(value.length-1).toUpperCase()
   })
   ```

   