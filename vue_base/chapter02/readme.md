## 一、Vue 实例与数据绑定

### 1.1、第一个 Vue 应用

1. Vue 最核心的功能：双向数据绑定([demo01](https://github.com/DeLei33534/vue_review/blob/master/vue_base/chapter02/demo01.html))
2. Vue 应用的创建

   1. 通过构造函数，创建 Vue 的根实例，启动 Vue 应用

   ```
    var app = new Vue({
        //选项
    })

    /*
     app变量存储Vue实例
     实例中几乎所有代码都是一个对象，写入实例的选项内
    */
   ```

   2. 选项 el 用于指定页面中已经存在的 DOM 元素，作为 Vue 实例的挂载点，可以使 HTMLElement，也可以是 CSS 选择器; 挂载成功后，可以通过 app.\$el 访问该元素

   ```
    <div id="app"></div>

    var app = new Vue({
        el:document.getElementById("app"),  //或app

        //可简写为 -- el:"#app",

        /*
          el:document.querySelector("div"),
        */
    })
   ```

   3. 选项 data 用于声明应用需要双向绑定的数据，实际开发中，会将所有后续会用到的数据，预先在 data 内进行声明

   ```
    //显式声明数据
    var app = new Vue({
        el:"#app",
        data:{
            a:2,
            b:3
        }
    })

    //Vue实例本身代理了data对象中的所有属性，可以通过如app.a，直接进行数据访问
    console.log(app.a);
    console.log(app.b);

    //将数据指向一个已有的变量
    var myData = {
        a:1,
        b:2
    }

    var app = new Vue({
        el:"#app",
        data:myData
        //俩者会默认建立双向绑定
        //修改属性，原数据也会随之更改，反之亦然
    })
    app.a = 2;
    console.log(myData.a) //2

    myData.b = 3;
    console.log(app.b) //3
   ```

   4. 在[demo01](https://github.com/DeLei33534/vue_review/blob/master/vue_base/chapter02/demo01.html)中，input 标签上应用了 v-model 指令(v-model="name")，它的作用是将 Vue 实例的 data 选项中的 name 数据，与标签 input 进行数据绑定

### 1.2、Vue 生命周期

1. 即每个 Vue 实例被创建时，经过的一系列初始化过程
2. 在初始化过程中，可以通过调用相应的生命周期钩子，在合适的时机执行所需的业务逻辑
3. Vue 的生命周期钩子，与之类似的有如 jQuery 中的 ready()方法
   ```
   $(document).ready(function(){
       // 等待所有DOM加载完成后
       // 才执行这里面的代码
   })
   ```
4. 常用的 Vue 生命周期钩子

   1. created: 调用时间为实例创建完成，但尚未挂载的时候; 一般用于需要对数据进行初始化处理的场合; 这个阶段完成了数据的观测处理等操作, \$el 还不能使用
   2. mounted: 调用时间为 el 刚刚挂载到实例后; 实际开发中，第一个业务逻辑通常在这里开始
   3. beforeDestroy: 一般在实例销毁前调用，主要用于解绑绑定监听的事件等

   ```
   // 钩子也是作为选项写入Vue实例中
   // 钩子的this指向调用它的Vue实例
   var app = new Vue({
       el:"#app",
       data:{
         a = 2
       },

       created:function(){
           console.log(this.a); // 2
       }

       mounted:function(){
           console.log(this.$el); // <div id="app"></div>
       }
   })
   ```

5. 实例: [demo02](https://github.com/DeLei33534/vue_review/blob/master/vue_base/chapter02/demo02.html)
   ![Vue 实例生命周期(官网)](https://cn.vuejs.org/images/lifecycle.png)

### 1.3、Vue 的简单应用

1. [插值与表达式](https://github.com/DeLei33534/vue_review/blob/master/vue_base/chapter02/demo03.html)
2. [过滤器](https://github.com/DeLei33534/vue_review/blob/master/vue_base/chapter02/demo04.html)

## 二、Vue 指令与事件
1. 数据驱动DOM是Vue的核心理念, 所以在正常开发流程中, 不要主动操作DOM; 用户只需要维护好数据, 通过数据驱动Vue来处理DOM
2. 指令(Directives)是Vue模板中最常用的一项功能，一般以"v-"作为前缀
3. 指令的主要功能，是当表达式的值改变时，将相应的行为应用到DOM上: [demo05](https://github.com/DeLei33534/vue_review/blob/master/vue_base/chapter02/demo05.html)
4. Vue内置了很多指令, 如之前接触过的:  v-if、v-html以及v-pre等; 指令的应用可以快速完成常见的DOM操作, 如循环渲染、显示与隐藏等; 首先需要掌握的两种重要的指令如下:
   1. [v-bind](https://github.com/DeLei33534/vue_review/blob/master/vue_base/chapter02/demo06.html): 基本用途是动态更新 HTML元素上的属性，比如id、class等
   2. [v-on](https://github.com/DeLei33534/vue_review/blob/master/vue_base/chapter02/demo07.html): 基本用途是用来绑定事件监听器, 便于用户完成一些交互操作

## 三、Vue 语法糖
1. 语法糖是指在不影响代码功能的情况下, 添加某种更为简洁的语法实现同样的效果, 从而使程序开发更加方便
2. 语法糖可以简化代码的书写
3. Vue为v-bind和v-on指令, 都提供了语法糖, 或者说是缩写: 
   1. v-bind
   ```
   <a v-bind:href= "url" >链接</a>
   <!-- 缩写为 -->
   <a :href= "url" >链接</a>
   ```
   2. v- on
   ```
   <button v-on:click="handleClose">click me!</button>
   <!-- 缩写为 -->
   <button @click="handleClose">click me!</button>
   ```