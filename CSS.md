
- 浏览器事件参考：<https://developer.mozilla.org/en-US/docs/Web/Events>
- 鼠标指针：<https://developer.mozilla.org/en-US/docs/Web/CSS/cursor> <http://csscursor.info/>

- `overflow-wrap/word-wrap`: word-wrap是IE的非正式的属性，标准化后命名为overflow-wrap。这个属性有两个主要属性：
  1. `normal`, 禁止拆分单词进行换行。如果单词显示超过边界，则另起一行进行显示，如果另起一行也不能显示，则单词溢出。
  1. `break-word`, 单词遇到超出边界则另起一行，如果一整行都不能显示，则把单词进行拆分后换行。
- `word-break`: 设置当单词遇到父元素边界时，是否拆分单词进行换行。这个属性的优先级高于overflow-wrap，主要属性值包括：
  1. `normal`, 英文单词不会被拆分，相关行为见overflow-wrap。
  1. `break-all`, 英文单词遇到边界溢出则被拆分换行。
  1. `keep-all`, 中英文都不会被拆分，尤其中文字间不会自动换行。
- `white-space`: 处理空白字符的方式，主要取值有三个：
  1. `normal`, 连续出现的空白字符被合并为1个空白字符，换行也被当做空格。
  1. `pre`, 保留所有空白字符的原始显示方式，连续出现的空白符不被合并，换行符就是换行符，与&lt;pre>类同。
  1. `nowrap`, 合并连续的空白符，换行被当做空格。遇到父元素边界不进行换行。
- `text-overflow`: 文字溢出父元素边界时的表现，此属性起作用的前提是，元素(block/inline-block)同时设置了white-space: nowrap; overflow: hidden; 改属性的主要取值如下：
  1. `clip`, 裁切掉溢出的部分
  1. `ellipsis`, 当有文字溢出时，在文字末尾显示...，并裁切掉溢出部分。
  1. `<string>`, 与ellipsis类似，但是显示指定的字符串
  
#### display的恢复

通过设置元素的style.display='none'来隐藏元素之后，可以通过赋值style.display=''来恢复元素样式表中的样式。（但不能恢复内联样式）

#### line-height 有无单位的区别

line-height属性值指定了单位后，后代元素会继承这个计算出来的行高，比如1.2em为24px，则后代元素的默认行高都是24px。

如果只指定了数值没有单位，则后代元素继承的就是这个数值，行高的计算是后代元素的本身字体大小乘以这个因子。

#### 在:before或者:after伪元素中，可以通过attr函数来获取其元素的属性值

#### 输入框的相关设置

* 设置placeholder颜色

```css
textarea::placeholder {
    color: #F0A531;
}
textarea::-webkit-input-placeholder {
    color: #F0A531;
}
textarea::-moz-placeholder {  /* Firefox 19+ */
    color: #F0A531;
}
textarea:-ms-input-placeholder {  
    color: #F0A531;
}
```
* 不允许改变大小

```css
textarea {
    resize: none;
}
```


