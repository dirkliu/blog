# webpack 构建工具
webpack 是一个现代的 JavaScript 应用程序的模块打包器(module bundler)。

![webpack
的理念](http://img.blog.csdn.net/20170511145746077?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbGl1cWkzMzI5MjIzMzc=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
当 webpack 处理应用程序时，它会递归地构建一个依赖关系图表(dependency graph)，其中包含应用程序需要的每个模块，然后将所有这些模块打包成少量的 bundle  

### webpack 几个重要概念：  
 * 入口（entry）   
 入口起点告诉 webpack 从哪里开始，并遵循着依赖关系图表知道要打包什么。它是app的第一个启动的文件。  
 * 出口 （output）    
 定义资源打包后的资源的路径和名称。
 * 加载器 （loaders）  
 loader 用于对模块的源代码进行转换。  
 webpack 把每个文件(.css, .html, .scss, .jpg, etc.) 都作为模块处理。然而 webpack 只理解 JavaScript。  
 webpack loader 会将这些文件转换为模块，而转换后的文件会被添加到依赖图表中。  ex: css-loader
 * 插件 （plugins）  
 利用webpack提供的一些底层的钩子，实现一些功能的定制。
 * 模块 （module）  
 webpack构建过程中的最小的一个资源单位，任何资源都可以作为一个模块
 * 块 （chunk）
 在code spliting（代码分离）中产生的资源，由module组成。
 * 代码分离  （code spliting） 
 代码分离是 webpack 中最引人注目的特性之一。你可以把你的代码分离到不同的 bundle 中，然后你就可以去按需加载这些文件
 ![webpack chunk和module的关系](http://img.blog.csdn.net/20161115172600571)
 * 配置项 （configuration）  
 webpack配置对象：根据不同的用法，有两种方式传递这个对象。CLI和node.js API  https://doc.webpack-china.org/api/node/
