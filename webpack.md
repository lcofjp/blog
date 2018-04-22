## 基本概念

webpack：提供了对工程的模块化管理，每一个源文件和资源都可以作为一个模块，源文件通过require或者import进行对依赖的引入。webpack对这些依赖进行分析并构建依赖关系图，最终把入口文件以及其所有依赖进行打包输出。

- 入口，webpack依赖分析的入口，通常一个页面对应一个入口
- 输出，指定输出路径和文件名，每个入口对应一个输出
- loader，对模块进行处理
- 插件，功能强大，能完成各种各样的功能

## 入口

## 资源预取
```JavaScript
// 动态加载js模块
import(/* webpackPrefetch: true */ "xxx")
```

```html
<!-- 对以后可能用到的资源进行空闲时加载 -->
<link rel="prefetch" href="xxx.js">
<!-- 对接下来的页面预取 -->
<link rel="next" href="2.html">
```

[参考链接](https://medium.com/webpack/link-rel-prefetch-preload-in-webpack-51a52358f84c)

## 输出

- 文件名 filename：
  + [hash] 模块标识符的hash（module id的hash）
  + [chunkhash] chunk内容的hash （ExtractTextWebpackPlugin使用contenthash）
  + [name] 模块名称
  + [id] 模块标识符
  + [query] 模块的query，

## 统计信息

```JavaScript
stats: "normal" | "verbose" | "none" | "minimal"
```


## 使用插件进行扩展

相对于加载器来说，使用插件对webpack进行扩展会更灵活。

Pluginsk可以通过hooks拦截webpack的执行。webpack本身实现就是一组Plugins。在底层其依赖于[tapable](https://www.npmjs.com/package/tapable)插件接口来允许webpack以不同的方式应用插件。

