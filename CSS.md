理解CSS的入口：

When laying out a document, the browser's rendering engine represents each element as a rectangular box according to the standard **CSS box model**.

在浏览器的渲染引擎渲染一个文档的过程中，每一个元素都被视作一个矩形的盒子。

Every box is composed of four parts (or areas).

每个盒子都由四部分或四个区域组成。

If the `box-sizing` property is set to *content-box*

`box-sizing`是非常重要的一个CSS属性。

A **block** on a webpage is an HTML element that appears on a new line, underneath the preceding element and above the following element.

问题1：当你在空白页面中放入一个块级元素，比如div，不设置任何CSS，它的height和width属性的值分别为多少？

问题2：以下两段代码的结果有什么区别？

        div {
            width: 100%;
            padding: 10px;
        }
        
        div {
           padding: 10px;
       }
       
如何实现宽度自适应按钮，即让按钮的其相对位置是如何的？大小自适应于文字的个数(不使用button元素)？
       
问题3：什么是列表布局以及列表布局的实现方式？

所谓列表布局就是具有相同DOM结构、水平排列可以repeat出来的一列元素的布局方式

最古老的列表布局方式就是浮动布局。

元素内的文本节点属于匿名inline boxes。

问题4：当文本与图片位于同一行时，其相对位置是如何的？

![](./assets/css-1.png)

默认情况下，图片与文字混排应该是这个样子：图片与文字基线对齐，图片与文字在同一行上。

The `line-height` CSS property sets the amount of space used for lines, such as in text.

On block-level elements, it specifies the minimum height of line boxes within the element.

On non-replaced inline elements, it specifies the height that is used to calculate line box height.

`float`可以说是所有CSS属性中的“破坏之王”。