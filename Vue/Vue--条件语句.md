# vue--条件语句

1. ### v-if
    `<div v-if="show"> 默认这一条是看得见的</div> `

    当"show"为true时显示，false不显示
    
2. ### v-else
  ```html
  <button v-on:click="moyiba"> 摸一把彩票 10%的几率，建议一边点击一边心里默数，多少次了,站长表示最多点了40次才中奖，妈蛋~ </button>
  <div v-if="show"> 中了500万！</div>
  <div v-else>谢谢惠顾！</div>
  ```

3. ### v-else-if

  ```html
  <button v-on:click="toutai"> 看看下辈子投胎是做什么的 </button>
  <div v-if="number>98"> 神仙</div>
  <div v-else-if="number>95"> 国家领导人</div>
  <div v-else-if="number>90"> 大富商</div>
  <div v-else-if="number>80"> 大企业主</div>
  <div v-else-if="number>70"> 演艺明星</div>
  <div v-else-if="number>60"> 小企业主</div>
  <div v-else-if="number>50"> 普通公务员</div>
  <div v-else-if="number>40"> 小个体户</div>
  <div v-else-if="number>30"> 血汗工厂工人</div>
  <div v-else-if="number>20"> 偏远山区农民</div>
  <div v-else> 流浪汉</div>
  ```