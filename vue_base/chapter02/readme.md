## 一、第一个 Vue 应用

1. Vue 最核心的功能：双向数据绑定([demo01](https://github.com/DeLei33534/vue_review/blob/master/vue_base/chapter02/demo01.html))
2. Vue应用的创建
   1. 通过构造函数，创建Vue的根实例，启动Vue应用
   ```
    var app = new Vue({
        //选项
    })

    /*
     app变量存储Vue实例
     实例中几乎所有代码都是一个对象，写入实例的选项内
    */
   ```
   2. 选项el用于指定页面中已经存在的DOM元素，作为Vue实例的挂载点，可以使HTMLElement，也可以是CSS选择器; 挂载成功后，可以通过app.$el访问该元素
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
   3. 选项data用于声明应用需要双向绑定的数据，实际开发中，会将所有后续会用到的数据，预先在data内进行声明
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
   4. 在[demo01](https://github.com/DeLei33534/vue_review/blob/master/vue_base/chapter02/demo01.html)中，input标签上应用了v-model指令(v-model="name")，它的作用是将Vue实例的data选项中的name数据，与标签input进行数据绑定

## 二、Vue生命周期
## 三、Vue的简单应用