# webpack项目搭建

## 什么是 webpack？

```
webpack是近期最火的一款模块加载器兼打包工具，它能把各种资源，例如JS（含JSX）、
coffee、样式（含less/sass）、图片等都作为模块来使用和处理。
我们可以直接使用require(XXX) 的形式来引入各模块，即使它们可能需要经过编译
（比如JSX和sass），但我们无须在上面花费太多心思，因为webpack有着各种健全
的加载器（loader）在默默处理这些事情，这块我们后续会提到。
你可以不打算将其用在你的项目上，但没有理由不去掌握它，因为以近期Github上各
大主流的（React相关）项目来说，它们仓库上所展示的示例已经是基于webpack来
开发的，比如React-Boostrap和Redux。
webpack的官网是 http://webpack.github.io/ ，文档地址是 http://webpack.github.io/docs/ ，想对其进行更详细了解的可以点进去瞧一瞧。

```

## webpack 的优势

其优势主要可以归类为如下几个：

  1. webpack是以commonJS的形式来书写脚本滴，但对AMD/CMD的支持也很全面，
  方便旧项目进行代码迁移。
  2. 能被模块化的不仅仅是JS了。
  3. 开发便捷，能替代部分grunt/gulp的工作，比如打包、压缩混淆、图片转base64等。
  4. 扩展性强，插件机制完善，特别是支持React热插拔（见react-hot-loader）的
  功能让人眼前一亮。

我们谈谈第一点。以AMD/CMD模式来说，鉴于模块是异步加载的，所以我们常规需要使用
define函数来帮我们搞回调：

```
define(['package/lib'], function(lib){
    function foo(){
        lib.log('hello world!');
    }
    return {
        foo: foo
    };
});

```
另外为了可以兼容commonJS的写法，我们也可以将define这么写：

```
define(function (require, exports, module){
    var someModule = require("someModule");
    var anotherModule = require("anotherModule");    
    someModule.doTehAwesome();
    anotherModule.doMoarAwesome();
    exports.asplode = function (){
        someModule.doTehAwesome();
        anotherModule.doMoarAwesome();
    };
});

```
