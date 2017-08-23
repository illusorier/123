定位是CSS中非常基础和重要的一部分内容。

The CSS *position* property lets you control how and where a web 

The **position** CSS property chooses alternate rules for positioning elements

**static**是position属性的默认值。

The element is positioned according to the normal flow of the document.

The **top**, **right**, **bottom**, **left**, and **z-index** properties have no effect.

- **Absolute**: Absolute positioning lets you determine an

  绝对定位的元素会脱离普通文档流，其他元素就当它不存在一样。

  In addition, absolutely positioned elements are completely detached from the flow of the page

Don't try to apply both the *float* property and any type of positioning other than static or relative to the same style.

An absolutely positioned element is actually placed *relative* to the boundaries of its closest positioned ancestor.

An absolutely positioned element is actually s

绝对定位的元素会位于普通元素之上。

Absolutely positioned elements sit "above" your web page and can even reside

如果不设置*z-index*的值，元素会按照它们在HTML中的顺序排列，其中在HTML位于最后的元素层级最高。
   
By default, the elements are stacked following the order they're declared in the HTML.