## 一、Vue 计算属性

1. Vue 开发中，模板内的表达式可以用于简单的运算，解决一些容易的业务逻辑问题
2. 当业务逻辑更为复杂时，表达式会变得冗长臃肿，难以阅读与维护
3. 使用计算属性，可以很好的解决上述问题: [demo01](https://github.com/DeLei33534/vue_review/blob/master/vue_base/chapter03/demo01.html)
4. 实际开发中，所有的计算属性均以函数的形式，书写在 Vue 实例的 computed 属性选项内
5. 计算属性函数，最终会返回经过处理后的计算结果

## 二、计算属性的使用

1. 在计算属性中可以完成多种复杂的逻辑，包括运算、函数调用等
2. 计算属性最终返回的是计算的结果
3. 计算属性可以依赖多个 Vue 实例数据，当任一数据发生变化时，计算属性会重新执行，同时视图也会相应的进行更新: [demo02]()
4. 每一个计算属性都包含一个 getter 与一个 setter，分别用来读取与设置数值
5. 一般情况下，computed 预设只有 getter，即其默认属性为 getter，只能读取而无法改变值
6. 只有 getter 的情况下，get 可以省略不写