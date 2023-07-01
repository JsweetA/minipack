> + 学习链接：https://juejin.cn/post/7146976516692410376?share_token=729eb5f3-f01f-4237-9c05-6e06e4c0131c
> + minipack：https://github.com/lzy19926

# minipack

### 打包原理

给予一个入口文件，然后利用文件读取模块将文件中的内容读取出来，并且扫描**import**把依赖收集起来，再去递归调用依赖中的文件，逐个将所有文件的内容，和依赖确定且收集。然后再打包到一起。

### HMR-热更新原理

在本地上开启一个websokect服务，建立服务端和客户端的双向通信，再利用监听文件的变化去重新加载变换了的模块。如果出现错误了，则会强制刷新。

+   [轻松理解webpack热更新原理 - 掘金 (juejin.cn)](https://juejin.cn/post/6844904008432222215)

### plugin-插件

插件就是利用 Webpack 暴露的钩子（hooks）来扩展和定制 Webpack 的功能。插件可以注册到特定的钩子上，在特定的时机执行自定义的逻辑代码。

+   自定义plugin：定义一个js方法或者js类，使他的原型或者类上拥有**apply方法**，然后在apply方法内给予调用的时机（暴露的钩子-hooks）
+   [揭秘webpack plugin | ChampYin's Blog](https://champyin.com/2020/01/12/揭秘webpack-plugin/)

### loader-加载器

由于webpack只识别js，所以需要利用loader来将一些不属于js的文件转换为文件，比如一些style-loader，scss-loader等等。其中可以设置两个函数**pitch和loader**

+   pitch：用于控制loader链的时机，此时是没有获取到对应文件的代码的。
+   loader：负责转换
+   [揭秘webpack loader | ChampYin's Blog](https://champyin.com/2020/01/28/揭秘webpack-loader/)

>   此时我有个疑问。关于plugin是否可以做loader的事情。理论上应该可以。但是loader是由匹配文件后缀去执行，可能做转换的方向更加完美，plugin只是在webpack上的钩子上调用，也许并不知道当前需要处理的数据或者内容是什么类型的内容。
