# Vue--计算属性

1. 直接绑定数据计算

    `{{ rmb/exchange }}`
   
2. 利用**computed**绑定，计算过程放在**computed**中，页面显示结果

   页面上: `{{dollar}}`

    Javascript中:

    ```javascript
    computed:{
        dollar:function() {
          return this.rmb / this.exchange;
        }
      }
    ```

3. **methods** 也能达到一样的效果,调用的时候，要加上括号

    页面上: `{{ getDollar() }}`

    Javascript: 

    ```javascript
    methods:{
        getDollar:function() {
          return this.rmb / this.exchange;
        }
      }
    ```
4. **computed** 和 **methods** 的区别
    **computed** 是有缓存的，只要**rmb**没有变化，**dollar** 会直接返回以前计算出来的值，而不会再次计算。 这样如果是复杂计算，就会节约不少时间。而**methods**每次都会调用,浪费资源

