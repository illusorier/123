理解CSS的入口：

When laying out a document, the browser's rendering engine represents each element as a rectangular box according to the standard **CSS box model**.

在浏览器的渲染引擎渲染一个文档的过程中，每一个元素都被视作一个矩形的盒子。

Every box is composed of four parts (or areas).

每个盒子都由四部分或四个区域组成。

If the `box-sizing` property is set to *content-box*

`box-sizing`是非常重要的一个CSS属性。  

A **block** on a webpage is an HTML element that appears on a new line, underneath the preceding element and above the following element.

##### 问题1：当你在空白页面中放入一个块级元素，比如div，不设置任何CSS，它的height和width属性的值分别为多少？

##### 问题2：以下两段代码的结果有什么区别？

        div {
            width: 100%;
            padding: 10px;
        }
        
        div {
           padding: 10px;
       }
       
##### 问题3：如何实现宽度自适应按钮，即让按钮的其相对位置是如何的？大小自适应于文字的个数(不使用内置元素如span、button等等)？

一种方法是使用`display:inline-block`属性，另一种方法就是使用`float`属性。

浮动就是个带有方位的`display:inline-block`属性。

`display:inline-block`某种意义上的作用就是包裹(wrap)，而浮动也有类似的效果。

因此大多数类似于`display:block; float:left`这样的CSS都是不优雅的。

浮动最原始的意义就是用来让图片环绕文字。

`float`可以说是所有CSS属性中的“破坏之王”。

参考：

http://www.zhangxinxu.com/wordpress/2010/01/css-float%E6%B5%AE%E5%8A%A8%E7%9A%84%E6%B7%B1%E5%85%A5%E7%A0%94%E7%A9%B6%E3%80%81%E8%AF%A6%E8%A7%A3%E5%8F%8A%E6%8B%93%E5%B1%95%E4%B8%80/
       
##### 问题4：什么是列表布局以及列表布局的实现方式？

所谓列表布局就是具有相同DOM结构、水平排列可以repeat出来的一列元素的布局方式

最古老的列表布局方式就是浮动布局。

元素内的文本节点属于匿名inline boxes。

##### 问题5：当文本与图片位于同一行时，其相对位置是如何的？

![](../assets/css-1.png)

默认情况下，图片与文字混排应该是这个样子：图片与文字**基线**对齐，图片与文字在同一行上。

The `line-height` CSS property sets the amount of space used for lines, such as in text.

On block-level elements, it specifies the minimum height of line boxes within the element.

On non-replaced inline elements, it specifies the height that is used to calculate line box height.

**Replaced Element**: An element whose content is outside the scope of the CSS formatting modal, such as as image, embedded document, or applet.

For example, the content of the HTML IMG elements is often replaced by the image that is "src" attribute  designates.

在目前CSS的世界里中，所有的高度都是由两个CSS模型产生的，一个是box盒状模型，对应CSS为"height+padding+margin"，另外一个是line box模型，对应样式为"line-height"。

inline boxes(行内元素的box)的高度直接受`line-height`控制，整一行的实际高度由其中最高的inline box决定。

对span元素应用height属性是没有效果的，但对img元素则有效果。

- inline elements:

    respect left & right margins and padding, but not top & bottom
    
    cannot have a width and height set
    
    allow other elements to sit to their left and right. (在正常文档流的情况下)
    
    

###### 问题6：三栏自适应布局有哪些实现方式？

http://www.zhangxinxu.com/wordpress/2009/11/%E6%88%91%E7%86%9F%E7%9F%A5%E7%9A%84%E4%B8%89%E7%A7%8D%E4%B8%89%E6%A0%8F%E7%BD%91%E9%A1%B5%E5%AE%BD%E5%BA%A6%E8%87%AA%E9%80%82%E5%BA%94%E5%B8%83%E5%B1%80%E6%96%B9%E6%B3%95/

补充：如何通过flex来实现？

结合使用`flex-grow`和`flex-basis`。

补充：如何通过grid来实现？

结合使用`grid-template-columns`, `grid-column-start`和`grid-column-end`。

##### 问题7：如何实现比例固定图片自适应布局？

在默认的水平文档流方向下，CSS `margin` 和 `padding`属性的垂直方向的百分比值都是相对于containing block的宽度计算的，这个和`top`, `bottom`等属性的百分比值不一样

The `padding` CSS property sets the padding area on all four sides of an element.

It is a shorthand that sets all individual `paddings` at once.

`padding`是`padding-left`, `padding-right`, `padding-bottom`, and `padding-left`的简写。

        /* top | horizontal | bottom */
        padding: 1em 2em 2em;

对于绝大多数的布局，我们并不要求比例固定，但是有一种情况例外，那就是图片。

##### 问题8：居中问题

居中问题分为这么几类，垂直居中、水平居中和垂直水平都居中。

- 行内元素的水平居中问题：

    我们可以给行内元素的父元素设置*text-align*属性来对其进行居中。
    
    The *text-align* CSS property describes how inline content like text is aligned in its parent block element.
    
    *text-align* does not control the alignment of block elements, only their inline content.
    
- 行内元素的垂直居中问题：
    
    行内元素垂直居中问题分为两个部分：单行和多行。
    
    单行：`padding-top`. `padding-bottom`或者`height`, `line-height`。

- 绝对定位元素的居中实现：

    元素尺寸已知且固定
  
        .element {
            position: absolute;
            width: $some-width;
            height: $some-height;
            top: 50%;
            left: 50%;
            margin-top: - $some-height/2;
            margin-left: - $some-width/2;
        }
        
    基于CSS3可以使用`transform`代替`margin`。
   
        .element {
            position: absolute;
            width: $some-width;
            height: $some-height;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
        }
        
    利用`margin: auto`实现绝对定位元素的居中
    
        .element {
            position: absolute;
            width: $some-width;
            height: $some-height;
            top: 0;
            right: 0;
            bottom: 0;
            left: 0;
        }

##### 问题9：如何将一张图片设置为某页面的背景？

每张图片都有自己的尺寸和比例，若不作任何设置，图片则会以原始比例作为页面背景，显示的区域大小由屏幕尺寸决定，这显然不是我们想要的。

The `background-size` CSS property specifies the size of the background image.

The size of the image can be fully constrained or only partially in order to preserve its  intrinsic ratio.

        /* Keywords syntax */
        background-size: cover;
        background-size: contain;
        
        
In addition to the default value(`auto`), there are two keywords you can use with `background-size`: `cover` and `contain`.  

`contain`和`cover`都会保持图片原有的宽高比。

##### 问题10：Pure Css如何实现标签页的切换效果？


A block formatting context is created by one of the following:

- the root element or something that contains it

- floats (elements where `float` is not `none`)

- absolutely positioned elements

Though any of the above mentioned conditions can create a block formatting context, there will also be some other effects.

> 

#### Using a Block Formatting Context to Contain Floats


##### resize