# webpack

webpack简析

**1.process.cwd()**

```
 path.join(process.cwd(),'dist');    

 解释：返回当前Node.js进程执行时的工作目录（如..../kr-admin-new/）

(process.cwd()):
/Users/songkk/kr-dev/Code/kr-admin-new   
(_dirname):当前模块的目录名
/Users/songkk/kr-dev/Code/kr-admin-new/webpack

 ```

**2.插件:**

```
require('html-webpack-plugin'); //生成html文件

require("webpack/lib/optimize/CommonsChunkPlugin");
// 提取公共模块

require("extract-text-webpack-plugin");// 默认的webpack
会将require("style.css")文件嵌入js文件中，使用该插件会将css从js中提取出来

require('clean-webpack-plugin'); //删除文件

require('copy-webpack-plugin'); //拷贝文件

copy文件需要通过插件"transfer-webpack-plugin"来完成。

happypack是webpack的一个插件，目的是通过多进程模型，来加速代码构建

```

**3.vendors:**

```
这个是给公共打包用的，比如说一个模块被很多的js中引用后，一旦加载每个js都会需
要加载这个包，那么这样就可以抽出来打成公共的，这样就可以调用一次，也就是打包一
次了。确实可以节省打包后的大小，模块就是CommonsChunkPlugin第三方库

```

**4. resolve (解析)**

```  
 extensions:  (数组)

 能够使用户在引入模块时不带扩展 (import File from '../path/to/file')    


 alias:(对象)

 创建 import 或 require 的别名，来确保模块引入变得更简单

```

**5.module:**

```
Loader:

loader可以将文件从不同的语言（如 TypeScript）转换为 JavaScript，或将内联图像
转换为dataURL。loader 甚至允许你直接在 JavaScript 模块中 import CSS文件！

webpack的升级使得module.loaders 现在转换为 module.rules
功能更强大的rules系统取代了老版本中的loader,但是老的moduler.loader写法依然是被
支持的，新的命名规则更加通俗易懂，非常建议使用新的module.rules。

```

**6.ESLint:**

```
是js中目前比较流行的插件化的静态代码检测工具。

```
