## 一、Vue 计算属性

1. Vue 开发中，模板内的表达式可以用于简单的运算，解决一些容易的业务逻辑问题
2. 当业务逻辑更为复杂时，表达式会变得冗长臃肿，难以阅读与维护
3. 使用计算属性，可以很好的解决上述问题: [demo01](https://github.com/DeLei33534/vue_review/blob/master/vue_base/chapter03/demo01.html)
4. 实际开发中，所有的计算属性均以函数的形式，书写在 Vue 实例的 computed 属性选项内
5. 计算属性函数，最终会返回经过处理后的计算结果

## 二、计算属性的使用

1. 在计算属性中可以完成多种复杂的逻辑，包括运算、函数调用等
2. 计算属性最终返回的是计算的结果
3. 计算属性可以依赖多个 Vue 实例数据，当任一数据发生变化时，计算属性会重新执行，同时视图也会相应的进行更新: [demo02](https://github.com/DeLei33534/vue_review/blob/master/vue_base/chapter03/demo02.html)
4. 每一个计算属性都包含一个 getter 与一个 setter，分别用来读取与设置数值
5. 一般情况下，computed 预设只有 getter，即其默认属性为 getter，只能读取而无法改变值
6. 只有 getter 的情况下，get 可以省略不写，所以在声明一个计算属性时，可以直接使用默认的写法
7. 设置的 setter 会在手动修改计算属性值时触发，执行一些自定义操作[demo03](https://github.com/DeLei33534/vue_review/blob/master/vue_base/chapter03/demo03.html)
8. 计算属性的实用技巧[demo04]()
   1. 计算属性可以依赖其它属性
   2. 计算属性不仅可以依赖当前 Vue 实例的数据，也可以依赖其他实例的数据
9. 计算属性除了简单的文本插值外，还经常用于动态地设置元素的 class 样式名称以及 style 内联样式; 当使用组件开发时，计算属性也常用来动态传递 props

## 三、计算属性缓存

1. 计算属性基于其依赖的数据缓存
2. 只有当计算属性依赖的数据发生变化时，它才会重新获取值
3. 当使用 methods 定义的方法可以实现与计算属性相同的效果时，具体使用哪一种方式取决于是否需要缓存
4. 计算属性一般应用在遍历数组与进行大量计算的情况
5. 示例: [demo05](https://github.com/DeLei33534/vue_review/blob/master/vue_base/chapter03/demo05.html)
