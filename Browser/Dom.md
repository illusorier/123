如今的前端开发往往依赖于各种框架。

反而对于原生的DOM操作感到陌生。

DOM应当是JS在浏览器端最基础和重要的应用了。

DOM是什么？

DOM可以将任何HTML或XML文档描绘成一个由多层节点构成的结构。

允许开发人员添加、移除和修改页面的某一部分。

节点分为几种不同的类型，我们可以用面向对象中继承的概念去理解它们之间的关系。

所有页面标记则表现为一个以特定节点为根节点的树形结构。

文档节点是每个文档的根节点，

IE，Firefox，Safari，Chrome和Opera都非常完善地实现了DOM。

Any HTML document is a tree structure.

When browser parses a document, it builds a content tree and then uses it to display the document.

我们利用DOM可以做什么？

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

> 尽管DOM作为API已经非常完善了，但为了实现更多的功能，仍然会有一些标准或专有的扩展。

## Document

JavaScript通过Document类型表示文档。

The `Document` interface represents any web page loaded in the browser and serves as an entry point into the 

The Document interface describes the common properties and methods for any kind of document.Depending on the document's type(e.g. HTML,XML,SVG,...),a larger API is available:


##### Document.createElement()


- Document.getElementsByClassName()
- 

This method creates the HTML element specified by tagName.

##### Document.createTextNode()

Creates a new Text node.

    var text = document.createTextNode(data)
    
text is a Text node.

data is a string containing the data to be put in the text node.

## Node

DOM1级定义了一个Node接口，该接口将由DOM中的所有节点类型实现。

JavaScript中的所有节点类型都继承自Node类型。

因此所有节点类型都共享着相同的基本属性和方法。

每个节点都有一个nodeType属性，用于表明节点的类型。

节点类型由12个数值常量来表示，任何节点类型必居其一

比较常见的有：

Node.ElEMENT_NODE(1)
Node.TEXT_NODE(3)
Node.COMMENT_NODE(8)
Node.DOCUMENT_NODE(9)
Node.DOCUMENT_TYPE_NODE(10)

A Node is an interface from which a number of DOM types inherit, and allows these various types to be treated similarly.

The following interfaces all inherit from Node: Document, Element, CharacterData (which Text,  Comment, and CDATASection inherit),

文档中所有的节点之间都存在这样或那样的关系。

节点间的各种关系可以用传统的家族关系来描述。

每个节点都有一个**childNodes**属性，其中保存着一个NodeList对象。

NodeList objects are collections of nodes such as those returned by properties such as Node.childNodes and document.querySelectorAll() method.

In some cases,the NodeList is a live collection,which means that changes in the DOM are reflected in the collection.

可以使用*Array.prototype.slice()*方法将NodeList对象转换为数组。

每个节点都有一个**parentNode**属性，该属性指向文档树中的父节点。

包含在childNodes列表中的所有节点都具有相同的父节点，因此它们的parentNode属性都指向同一个节点。

此外，包含在childNodes列表中的每个节点相互之间都是同胞节点。

通过使用列表中每个节点的previousSibling和nextSibling属性，可以访问同一列表中的其他节点。

父节点的firstChild和lastChild

因为关系指针都是只读的，所以DOM提供了一些操作节点的方法。

最常用的方法是*appendChild()*，用于向childNodes列表的末尾添加一个节点。

添加节点后，childNodes的新增

#### Node.nodeType

The read-only **Node.nodeType** property that represents the type of the node.

#### Methods

##### Node.appendChild() 

Inserting Elements with appendChild(..)

adds a node to the end of the list of children of a specified parent node.

If the given child 

##### Node.cloneNode()

##### Node.childNodes

在DOM当中有几种方法获得某节点的子节点，相应的返回结果不同。

*childNodes* includes all child nodes, including non-element nodes like text and comment nodes.

To get a collection of only elements, use ParentNode.children instead.

### Element

除了Document类型之外，Element类型就要算是Web编程中最常用的类型了。

**Element** is the most general base class from which all objects in a 

The `Element` interface represents an object of a Document.This interface describe methods and properties common to all kinds of elements.For example,the HTMLElement interface is the base interface for HTML elements, while the SVGElement interface is the basis for all SVG elements.

- Element.attributes
- 

##### Element.innerHTML

This property provides a simple way to completely replace the contents of an element.

##### Element.getBoundingClientRect()

该方法用于返回元素的大小和其相对于视口的位置。

This methods returns the size of an element and its position relative to the viewport.

Properties other than *width* and *height* are relative to the top-left of the viewport.

### HTMLElement

The `HTMLElement` interface represents any HTML element.

Some elements directly implement this interface,others implement it via an interface that inherits it.


## 专有扩展

##### children属性

这个属性是HTMLCollection的实例，

##### contains()方法

在实际开发中，

> DOM1级主要

DOM2级样式(DOM Level 2 Style):定义了如何以编程方式来访问和改变CSS样式信息。

在HTML中定义样式的方式有3种：通过`<link/>`元素包含外部样式文件、使用`<style>`元素定义嵌入式样式，

任何支持style属性的HTML元素在JavaScript中都有一个对应的style属性。

这个style属性(对象)是CSSStyleDeclaration的实例，包含着通过HTML的style属性指定的所有样式信息，但不包含与外部样式表或嵌入样式表经层叠而来的样式

CSSStyleDeclaration represents a collection of CSS property-value pairs.

It is used in a few APIs:

- HTMLElement.style
- CSSStyleDeclaration is also a **read-only** interface to the result of window.getComputedStyle().

以下的属性和方法并不属于"DOM2级样式"规范。

DOM中没有规定如何确定页面中元素的大小

有些元素(例如<html>元素)，即使没有执行任何代码也能自动地添加滚动条


