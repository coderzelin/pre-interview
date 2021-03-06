### HTML 基础

---

#### doctype 的作用是什么

DOCTYPE 是 html5 标准网页声明，并且必须声明在第一行，来告知浏览器的解析器用什么标准去解析这个文档，不同的标准会影响浏览器对 css，甚至是 js 的解析

DOCTYPE 有以下两种模式

- 怪异模式: 浏览器使用自己的怪异模式解析渲染页面(当没有声明 doctype 的时候默认就是怪异模式)
- 标准模式: 浏览器使用 w3c 标准解析渲染页面

### 这两种模式的区别

- 标准模式: 浏览器按照 html 和 css 定义去渲染
- 怪异模式: 会模拟旧的浏览器的行为

### HTML、XML、XHTML 有什么区别

- HTML(超文本标记语言) 在 html4.0 之前 HTML 先有实现再有标准，导致 html 非常混乱和松散
- XML(可扩展标记语言) 可以存储数据结构，可扩展，跟 JSON 相似，但是 JSON 较轻量高效，所以 xml 现在没有市场
- XHTML(可扩展超文本标记语言) 基于上面两者而来，W3C 为了解决 HTML 混乱问题而生，并基于此诞生了 HTML5，开头加入`<!DOCTYPE html>`的做法因此而来，如果不加就是兼容混乱的 HTML，加了就是标准模式

### 什么是 data-属性

HTML 的数据属性，用于将数据储存于标准的 HTML 元素中作为额外信息,我们可以通过 js 访问并操作它，来达到操作数据的目的。

### 你对语义化的理解

语义化就是使用恰当的标签，让页面具有良好的结构和含义
语义化的好处:

- 开发者友好，使用语义化的标签增强了可读性，可以清楚的看出网页的结构，便于团队的开发和维护
- 机器友好，利于 SEO，适合搜索引擎的爬虫爬取有效信息

### 有哪些常用的 meta 标签

meta 标签包括 name 和 content 属性，它提供 html 文档的元信息

- charset,用于描述 html 文档的编码格式
- http-equiv,相当于 http 的文件头作用
- viewport,移动端理想视口，开发人员可以控制视口的大小和比例

### src 和 href 的区别

- src 指向外部资源的位置，指向的内容会被嵌入到该标签的这个位置，在请求 src 的资源并将其下载到该文档内的时候，如 js 脚本，图片，frame 元素等，会暂停其他资源的下载和处理，直到该 src 资源加载，编译，执行。
- href 指向网络资源所在的位置，用来建立和当前元素或文档之间的连接，当浏览器识别到它他指向的文件时，就会并行下载资源，不会停止对当前文档的处理
