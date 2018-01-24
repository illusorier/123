DOM操作应当是JS在浏览器端最原始和重要的应用了。

如今的前端开发往往依赖于各种框架，为了提高开发效率，在DOM操作方面，它们往往做了些封装。

因此造成对于原生DOM操作感到陌生的现象。

> 前端开发围绕HTML展开。

**DOM是什么**？

The DOM (Document Object Model) is an API that represents and interacts with any HTML or XML document.

The DOM is one of the most-used APIs on the Web because it allows code running in a browser to access and interact with every node in the document.

DOM was not originally specified - it came about when browsers began implementing JavaScript.

This legacy DOM is sometimes called DOM 0.

此外，DOM本身也不是ECMAScript语法的一部分。

DOM可以将任何HTML或XML文档描绘成一个由多层节点构成的结构。

允许开发人员添加、移除和修改页面的某一部分。

节点分为几种不同的类型，我们可以用面向对象中继承的概念去理解它们之间的关系。

所有页面标记则表现为一个以特定节点为根节点的树形结构。

文档节点是每个文档的根节点。

    <html>
      <head>
        <title>My Document</title>
      </head>
      <body>
        <h1>Header</h1>
        <p>Paragraph</p>
      </body>
    </html>
    
在这个例子中，文档节点只有一个子节点，即<html>元素，我们称之为**文档元素**。

在HTML页面中，文档元素始终都是<html>元素。

IE，Firefox，Safari，Chrome和Opera都非常完善地实现了DOM。

Any HTML document is a tree structure.

When browser parses a document, it builds a content tree and then uses it to display the document.

**我们利用DOM可以做什么**？

说到最常见的DOM应用，恐怕就要数取得特定的某个或某组元素的引用，然后再执行一些操作了。

取得元素的操作可以使用document对象的几个方法来完成，如document.getElementById(), document.getElementByTagName()等等。

The DOM is an API that allows access to and modification of the current document.

It allows manipulation of document Node and Element.

The W3C's DOM Level 1 Core is a powerful object model for changing the content tree of documents.


    <html>
      <head>
        <title>My Document</title>
      </head>
      <body>
        <h1>Header</h1>
        <p>Paragraph</p>
      </body>
    </html>
    
![](../assets/DOMTree.jpg)

Each box in the tree above is a node in the tree.
 
The line above a node expresses a parent-child relationship: the node on top is the parent, and the node on the bottom is the child.

Two children of the same parent are therefore siblings.

DOM was 

> 尽管DOM作为API已经非常完善了，但为了实现更多的功能，仍然会有一些标准或专有的扩展。

选择符API

## Document

JavaScript通过Document类型表示文档。

在浏览器中，document对象时HTMLDocument

`HTMLDocument` is an abstract interface of the DOM which provides access to special properties and methods not present by the default

The `Document` interface represents any web page loaded in the browser and serves as an entry point into the 

The Document interface describes the common properties and methods for any kind of document.Depending on the document's type(e.g. HTML,XML,SVG,...),a larger API is available:

作为HTMLDocument的一个实例，document对象还有一些标准的Document对象所没有的属性。

这些属性提供了document对象所表现的网页的一些信息。

其中第一个属性就是title，包含着<title>元素中的文本——显示在浏览器窗口的标题栏或标签页上。

##### Document.createElement()


- Document.getElementsByClassName()
- 

This method creates the HTML element specified by tagName.

##### Document.createTextNode()

Creates a new Text node.

    var text = document.createTextNode(data)
    
text is a Text node.

data is a string containing the data to be put in the text node.

## 专有扩展

##### children属性

这个属性是HTMLCollection的实例，

##### contains()方法

在实际开发中，

> DOM1级主要

DOM2级样式(DOM Level 2 Style):定义了如何以编程方式来访问和改变CSS样式信息。

在HTML中定义样式的方式有3种：通过`<link/>`元素包含外部样式表文件、使用`<style/>`元素定义嵌入式样式，以及使用style特性定义针对特定元素的样式。

任何支持style属性的HTML元素在JavaScript中都有一个对应的style属性。

这个style属性(对象)是CSSStyleDeclaration的实例，包含着通过HTML的style属性指定的所有样式信息，但不包含与外部样式表或嵌入样式表经层叠而来的样式

CSSStyleDeclaration represents a collection of CSS property-value pairs.

It is used in a few APIs:

- HTMLElement.style
- CSSStyleDeclaration is also a **read-only** interface to the result of window.getComputedStyle().

以下的属性和方法并不属于"DOM2级样式"规范。

DOM中没有规定如何确定页面中元素的大小

有些元素(例如<html>元素)，即使没有执行任何代码也能自动地添加滚动条


