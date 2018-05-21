
[cheerio github repository](https://github.com/cheeriojs/cheerio)

## 安装

`npm install cheerio`

## API

### 加载HTML

cheerio需要手动把html文档的内容传给它。

```javascript
const cheerio = require('cheerio')
const $ = cheerio.load('<html>...内容...</html>')
// load函数可以接受另外的参数，用于改变默认的解析选项
const $ = cheerio.load('<ul id="fruits">...</ul>', {
    normalizeWhitespace: true,
    xmlMode: true
});
```

### 选择器selectors

$(selector, [context], [root])

### 属性

.attr(name, value) // 获取或设置元素的属性

.prop(name, value) // 获取或设置元素的属性

.data(name, value) // 获取或设置元素的数据

.val([value]) // 获取或设置元素的值

.removeAttr(name) // 移除属性

.hasClass(className) // 判断是否具有特定类名

.addClass(className) // 增加类名

.removeClass([className]) // 移除指定类名，如果没指定类名则移除所有类名

.toggleClass(className, [switch]) // 切换类名

### 遍历

.find(selector | selection | node) // 获取满足条件的后代元素

.parent([selector]) // 获取元素的父元素

.parents([selector]) // 获取元素的所有祖先元素

.parentsUntil([selector] [,filter]) // 获取元素的祖先元素，直到selector（不包含selector）

.closest(selector) // 在元素本身以及元素祖先中，选择离元素最近且满足条件的元素

.next([selector]) // 选择元素的下一个兄弟节点，可以通过selector过滤掉不符合条件的

.nextAll([selector]) // 选择元素的所有后续兄弟节点

.nextUntil([selector], [filter]) // 选择后续兄弟节点直到遇到selector但不包含selector

.prev([selector]) // 选择元素的前一个兄弟节点

.prevAll([selector]) // 选择元素前面的所有兄弟节点

.prevUntil([selector], [filter]) // 选择元素前面的兄弟节点直到遇到selector但不包含selector

.slice(start, [end]) // 选择指定范围的元素

.siblings([selector]) // 选择元素的所有兄弟节点

.children([selector]) // 选择元素的所有子元素

.contents() // 获取元素的子节点，包含元素、文本和注释

.each(function(index, element)) // 遍历所有元素，return false终止遍历

.map(function(index, element)) //

.filter(selector | selection | element | function(index, element)) // 筛选元素

.not(selector | selection | element | function(index, elem)) // 排除符合selector的元素

.has(selector | element) // 选择符合selector是其后代的元素

.first() // 选择第一个元素

.last() // 选择最后一个元素

.eq(i) // 选择第i个元素

.get([i]) // 获得第i个cheerio对象对应的DOM元素，不指定i则获取全部

.index([selector | nodeOrSelection]) // 元素在所有selector中的索引

.end() // 结束最近的一次的过滤操作

.add(selector[, context])
.add(element | elements | html | selection) // 向元素中添加元素

.addBack([filter]) // 把栈上之前的一组元素追加到当前的元素组中

### 处理

略...



