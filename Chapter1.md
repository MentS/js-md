### JavaScript 的实现

Javascript 的实现通常包括 三个部分 ECMAScript, 文档对象模型(DOM), 浏览器对象模型(BOM)

#### ECMAScript

规定了语言的 语法，类型，语句，关键字， 保留字， 操作符， 对象 各个方面内容的语言描述

#### DOM

文档对象模型是针对 XML 但经过扩展用于 HTML 的应用程序编程 **接口**。 DOM 会把整个页面映射为一个多层节点结构(树形结构)， XML 和 HTML 页面中的每个组成部分都是某种类型的 节点，节点包含着不同的类型的数据。 DOM 是一个语言和平台无关的接口，允许脚本动态的访问和更新文档的内容。

#### DOM 级别

##### DOM1 级

DOM1 级由 DOM 核心(DOM Core)和 DOM HTML 组成。DOM 核心规定了如何映射基于 XML 的文档结构，简化对文档的访问和操作。
DOM HTML 在 DOM 核心的基础上加以扩展，添加了对 HTML 的对象和方法。

##### DOM2 级

DOM2 级在 DOM1 级上扩充了鼠标和用户界面事件，范围，遍历(迭代 DOM 的方法)等细分模块，通过对象接口增加对 CSS 的支持。
DOM2 级引入下列新模块，给出了众多新类型的接口定义

1.  DOM 视图(DOM Views)： 定义了跟踪不同文档视图的接口
2.  DOM 事件(DOM Events)： 定义了事件金额事件处理接口
3.  DOM 样式(DOM Style)： 定义基于 CSS 为元素应用样式的接口
4.  DOM 遍历和范围(DOM traversal and Range)：定义了遍历和操作文档树的接口

##### DOM3 级

DOM3 级进一步扩展 DOM， 引入了统一的方式加载和保存文档的反法，在 DOM 加载和保存模块中定义(DOM Load and Save),新增 DOM 验证(DOM Validation)模块。同时对 DOM 核心进行了扩展 支持 XML

```javascript
// DOM事件绑定
<a id="app" onclick="alert('1')" />;

var app = document.querySelector("#app");
app.onclick = function() {
  alert("2");
};

// alert('2')
// add  onclick

app.onclick = function() {
  alert("3");
};

// alert('3')
// DOM 1 级 绑定多个事件，最后一个会覆盖前面的 只执行最后一个事件
// addEventListener 可以绑定多个事件依次执行
```

#### BOM

浏览器对象模型把针对浏览器的 Javascript 扩展算作 BOM 的部分

1.  弹出窗口
2.  移动、缩放、和关闭浏览器窗口
3.  提供浏览器详细信息的 navigator 对象
4.  提供浏览器所加载页面的详细信息的 location 对象
5.  提供用户显示器分辨率详细信息的 screen 对象
6.  对 cookie 的支持
7.  XMLHttpRequest 和 IE ActiveXObject 对象的支持

BOM 没有具体的标准，每个浏览器都有自己的实现
