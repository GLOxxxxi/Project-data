# vue--循环语句

1. ### v-for 循环语句
  ```html
  <table align="center" >
        <tr class="firstLine">
            <td>name</td>
            <td>hp</td>
        </tr>
        <tr v-for="hero in heros">
            <td>{{hero.name}}</td>
            <td>{{hero.hp}}</td>
        </tr>
    </table>
  ```
2. ### index用法
  ```html
  <table align="center" >
        <tr class="firstLine">
            <td>number</td>
            <td>name</td>
            <td>hp</td>
        </tr>
        <tr v-for="hero,index in heros">
            <td>{{index+1}}</td>
            <td>{{hero.name}}</td>
            <td>{{hero.hp}}</td>
        </tr>
    </table>
  ```
3. ### 纯数字遍历
  ```html
<div v-for="i in 10">
     {{ i }}
</div>
  ```