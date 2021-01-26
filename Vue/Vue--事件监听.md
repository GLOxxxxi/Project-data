# vue--事件监听

1. v-on事件监听
    `<button v-on:click="count">点击</button>`
2. v-on缩写为@
    `<button @click="count">点击</button>`
3. 事件修饰符
  * .stop 
    *  阻止冒泡 `<div id="me" v-on:click.stop="doc">`
  * .prevent  
    * 阻止提交，阻止页面刷新（`@click.prevent`或者`@click.prevent="jump"`）
  * .capture  
    * 优先触发 `<div id="father" v-on:click.capture="doc">`
  * .self  
    * 子元素无法触发，只能自己触发 `<div id="father" v-on:click.self="doc">`
  * .once 
    * 只能提交一次，触发之后不再监听，但是父层元素还能触发事件 `<div id="father" v-on:click.once="doc">`