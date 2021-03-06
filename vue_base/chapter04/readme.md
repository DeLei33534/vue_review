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
   1. 当需要应用多个 class 时, 可以给:class 绑定一个数组, 直接应用一个 class 列表
   2. 可以使用三元表达式, 根据条件切换 class
   3. 当 class 存在多个条件时，为了避免繁琐的编写，可以在数组中嵌套对象写法
   4. 同对象语法一样, 也可以使用 data, computed 和 methods 三种方法
   5. 示例: [demo02](https://github.com/DeLei33534/vue_review/blob/master/vue_base/chapter04/demo02.html)
3. 在组件上使用
   1. 直接在自定义组件上使用 class 或:class，样式会作用到组件的根元素上
   2. 这种方法仅适用自定义组件的最外层, 为一个根元素的情况, 否则会失效, 甚至影响组件整体的加载效果
   3. 当不满足这种条件或需要给具体的子元素设置类名时, 应当使用组件的 props 来传递
   4. 这些特点同样适用于绑定内联样式 style 的情况
   5. 示例: [demo03](https://github.com/DeLei33534/vue_review/blob/master/vue_base/chapter04/demo03.html)

## 三、绑定内联样式

1. 使用 v-bind:style(:style)可以给元素绑定内联样式
2. 使用这种方式时, css 属性名称使用驼峰命名(camelCase)或短横分隔命名(kebab-case)
3. 为了便于阅读，一般使用 data 或 computed 对其进行优化
4. 应用多种样式时，可以使用数组语法(不常用)
5. 使用:style 时, Vue.js 会自动给特殊的 css 属性名称增加前缀, 比如 transform
6. 示例:[demo04](https://github.com/DeLei33534/vue_review/blob/master/vue_base/chapter04/demo04.html)
