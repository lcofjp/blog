
[cheerio github repository](https://github.com/cheeriojs/cheerio)

## 安装

`npm install cheerio`

## API

### 加载HTML

cheerio需要手动把html文档的内容传给它。

```javascript
const cheerio = require('cheerio')
const $ = cheerio.load('<html>...内容...</html>')
```
