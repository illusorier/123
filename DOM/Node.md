从面向对象的角度：

## Node

DOM1级定义了一个Node接口，该接口将由DOM中的所有节点类型实现。

JavaScript中的所有节点类型都继承自Node类型。

因此所有节点类型都共享着相同的基本属性和方法。

每个节点都有一个nodeType属性，用于表明节点的类型。

节点类型由12个数值常量来表示，任何节点类型必居其一

比较常见的有：

- Node.ElEMENT_NODE(1)
- Node.TEXT_NODE(3)
- Node.COMMENT_NODE(8)
- Node.DOCUMENT_NODE(9)
- Node.DOCUMENT_TYPE_NODE(10)

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

#### Node.innerText

`Node.innerText` is a property that represents the "rendered" text content of a node and its descendants.

### Methods

#### Node.appendChild() 

Inserting Elements with appendChild(..)

adds a node to the end of the list of children of a specified parent node.

If the given child 

#### Node.cloneNode()

#### Node.childNodes

在DOM当中有几种方法获得某节点的子节点，相应的返回结果不同。

*childNodes* includes all child nodes, including non-element nodes like text and comment nodes.

To get a collection of only elements, use ParentNode.children instead.

### Element

除了Document类型之外，Element类型就要算是Web编程中最常用的类型了。

**Element** is the most general base class from which all objects in a 

The `Element` interface represents an object of a Document.This interface describe methods and properties common to all kinds of elements.For example,the HTMLElement interface is the base interface for HTML elements, while the SVGElement interface is the basis for all SVG elements.

#### Element.attributes

The `Element.attributes` property returns a live 

It is a `Node`

#### Element.innerHTML

This property provides a simple way to completely replace the contents of an element.

Unlike innerText, innerHTML lets you work with HTML rich text and does not automatically encode and decode text. 

        el.innerText = '<p>Hello World</p>';
        
        el.innerHTML = '<p>Hello World</p>';
        
上面两行代码分别执行后，浏览器中显示的内容是不一样的。

#### Element.getBoundingClientRect()

该方法用于返回元素的大小和其相对于视口的位置。

This methods returns the size of an element and its position relative to the viewport.

Properties other than *width* and *height* are relative to the top-left of the viewport.

#### Element.clientHeight

#### Element.scrollHeight

The `Element.scrollHeight` read-only property is a measurement of the height of an element's content, including content not visible on the screen due to overflow.



#### Element.scrollTop

The `Element.scrollTop` property gets or sets the number of pixels that an element's content is scrolled vertically.

### HTMLElement

The `HTMLElement` interface represents any HTML element.

Some elements directly implement this interface,others implement it via an interface that inherits it.

