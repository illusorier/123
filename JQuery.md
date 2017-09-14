## The jQuery Object

JQuery Object是JQuery当中的一个核心概念。

如何创建一个JQuery Object?

When the jQuery function is invoked with a CSS selector, it will return a JQuery object wrapping any element(s) that match this selector.

        // heading就是一个JQuery Object
        var heading = $( "h1" );
        
`JQuery( selector [,content] )`

`JQuery( html [,ownerDocument] )`: Creates DOM elements on the fly from the provided string of raw HTML.

If a string is passed as the parameter to `$()`, JQuery examines the string to see if it looks like HTML. If not, the string is interpreted as a selector. 

切入点：JQuery和原生的对比

元素的遍历：

`.children( [selector] )`: Get the children of each element in the set of matched elements.

Given a JQuery object that represents a set of DOM elements, the `.children()` method allows us to search through the children of these elements in the DOM tree and construct a new jQuery object from the matching elements.

The `.children()` method differs from `.find()` in that `.children()` only travels a single level down the DOM tree.

Note also that like most jQuery methods, `.children()` does not return text nodes; to get *all* children including text and comment nodes, use `.content()`

原生中有两种方法获取某元素的子元素，也分别对应是否返回文本和注释节点。


`.find()`

如何获取某元素的属性？

`.attr()`: Get the value of an attribute for the first element in the set of 

如何获取以及设置某元素的样式？

`.css()`: Get the value of a computed style property for the first element in the set of matched elements or set one or more CSS properties for every matched element.

`.css( propertyName )`, `.css( propertyName, value )`

DOM相关的操作

`.wrap()`: Wrap an HTML structure around each element in the set of matched elements.

`.before()`

`.after()`



