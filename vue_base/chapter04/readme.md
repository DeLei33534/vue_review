## 一、v-bind 指令介绍

1. v-bind 指令主要用途是动态更新 HTML 元素上的属性，常用来动态绑定 class 类名或 style 样式
2. v-bind 语法糖
   ```
   <a v-bind:href= "url" >链接</a>
   <!-- 缩写为 -->
   <a :href= "url" >链接</a>
   ```

## 二、绑定 class 的方式

1. 对象语法
   1. 给 v-bind:class 设置对象
   2. 使用 v-bind 绑定的 class，可以与普通 class 共存
   3. 当绑定 class 的表达式过长，逻辑复杂时，可以为其绑定计算属性，一般应用于表达式条件多于两个的情况
   4. 示例: [demo01](https://github.com/DeLei33534/vue_review/blob/master/vue_base/chapter04/demo01.html)
2. 数组语法
3. 在组件上使用

## 三、绑定内联样式
