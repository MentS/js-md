## JavaScript 的使用

向 HTML 页面中插入 Javascript 的主要方法就是使用 <script></script> 标签元素，有以下属性

1.  async: 可选。表示应该立即下载脚本，但不妨碍页面中的其他操作，比如下载其他资源或等待加载其他脚本。只对外部脚本文件有效。
2.  charset: 可选。表示通过 src 属性指定的代码字符集。大多数浏览器会忽略它的值
3.  defer: 可选。表示脚本可以延迟到文档完全解析和显示之后在执行。只对外部脚本有效。IE7 + 支持。
4.  language: 已废弃。用来表示编写代码使用的脚本语言
5.  src: 可选。表示包含执行代码的外部文件。
6.  type: 表示编写脚本语言的的内容类型通常是 text/JavaScript。

### <noscript> 元素

<noscript> 元素 用来让页面平稳的退化。当浏览器不支持 Javascript 时<noscript>i 里面的内容才会显示出来。
