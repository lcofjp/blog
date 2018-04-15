
### 使用插件进行扩展

相对于加载器来说，使用插件对webpack进行扩展会更灵活。

Pluginsk可以通过hooks拦截webpack的执行。webpack本身实现就是一组Plugins。在底层其依赖于[tapable](https://www.npmjs.com/package/tapable)插件接口来允许webpack以不同的方式应用插件。

