In the visual formatting model, each element in the document tree generates zero or more boxes according to the box model.

The layout of these boxes is governed by:

-
-
-
-

The `display` property, specifies a box's type.

display属性决定了元素的盒子类型

In CSS 2.2, 

### Block-level elements

**Block-level elements** are elements which generate a block-level box.

块级元素会产生块级盒子

Values of the `display` property that make an element block-level element: `block`, `list-item`, and `table`.

**Block-level boxes** are boxes that participate in a BFC.

If a block container box has a block-level box inside it, then we force it to have only block-level boxes inside it.

        <div>
            Some text
            <p>More text</p>
        </div>
        
### Inline-level elements

行内元素

The following values of the `display` property make an element inline-level: `inline`, `inline-table`, and `inline-block`.

Inline-level elements generate *inline-level boxes*, which are boxes that participate in an IFC.

In CSS, a **replaced element** is an element whose representation is outside the scope of CSS.

In other words, these are external objects whose representation is independent of the CSS formatting model.

In a BFC, boxes are laid  out one after the other, vertically, beginning at the top of a containing block.

## Positioning schemes

In CSS 2.2, a box may be laid out according to three *positioning schemes*:

定位体系

An element is called *out of flow* if it is floated, absolutely positioned, or is the root element.

## Inline formatting contexts

IFC的形成条件

An inline formatting context is established by a block container box that contains no block-level boxes.

在IFC中，盒子依次水平排列

In an inline formatting context, boxes are laid out horizontally, one after the other, beginning at the top of a containing block.

The boxes may be aligned vertically in different ways.

The rectangular area that contains the boxes that form a line is called a **line box**.

Any text that is directly contained inside 

        <p>Some <em>emphasized</em> text</p>
        
普通文档流