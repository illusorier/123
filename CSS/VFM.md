In the visual formatting model, each element in the document tree generates zero or more boxes according to the box model.

盒子的布局规则

The layout of these boxes is governed by:

- box dimensions and type.

- positioning scheme (normal flow, float, and absolute positioning)

-

-

The following sections describe the types of boxes that may be generated in CSS 2.2.

The `display` property, specifies a box's type.

display属性决定了元素的盒子类型

In CSS 2.2, 

### Block-level elements

*Block-level elements* - those elements of the source document that are formatted visually as blocks (e.g., paragraph) - are elements which generate a block-level box.

块级元素就像段落一样，占据一整行

Values of the `display` property that make an element block-level element: `block`, `list-item`, and `table`.

块级盒子

*Block-level boxes* are boxes that participate in a BFC.

block container

块级容器和块级元素(盒子)并不是等价的概念。

In CSS 2.2, a block-level box is also a *block container* box unless it is a table box or the principal box of a replaced element.

Values of the 'display' property which make a non-replaced element generate a block container include 'block', 'list-item' and 'inline-block'.

Not all block container boxes are block-level boxes.

Anonymous block boxes

匿名块级盒子

If a block container box has a block-level box inside it, then we force it to have *only* block-level boxes inside it.

        <div>
            Some text
            <p>More text</p>
        </div>
        
### Inline-level elements

行内元素

*Inline-level elements* are those elements of the source document that do not form new blocks of content; the content is distributed in lines.

The following values of the `display` property make an element inline-level: `inline`, `inline-table`, and `inline-block`.

行内元素产生行内级盒子

Inline-level elements generate *inline-level boxes*, which are boxes that participate in an IFC.

In CSS, a **replaced element** is an element whose representation is outside the scope of CSS.

In other words, these are external objects whose representation is independent of the CSS formatting model.

In a BFC, boxes are laid  out one after the other, vertically, beginning at the top of a containing block.

## Positioning schemes

定位体系

In CSS 2.2, a box may be laid out according to three *positioning schemes*:

1. Normal flow
2. Floats
3. Absolute positioning

An element is called *out of flow* if it is floated, absolutely positioned, or is the root element.

## Normal flow

Boxes in the normal flow belong to a formatting context, which in CSS 2.2 may be table, block or inline.

In future levels of CSS, other types of formatting context will be introduced.

## Block formatting contexts

BFC是如何形成的？

Floats, absolutely positioned elements, block containers (such as inline-blocks, table-cells, and table-captions) that are not block boxes, and block boxes with 'overflow' other than 'visible' establish new BFC for their contents.

In a block formatting context, boxes are laid out one after the other, vertically, beginning at the top of a containing block.

## Inline formatting contexts

IFC是如何形成的？

An inline formatting context is established by a block container box that contains no block-level boxes.

IFC中盒子的布局方式

In an inline formatting context, boxes are laid out horizontally, one after the other, beginning at the top of a containing block.

Horizontal margins, borders, and padding are respected between these boxes.

盒子垂直方向上的对齐方式

The boxes may be aligned vertically in different ways: their bottoms or tops may be aligned, or the baselines of text within them may be aligned.

什么是Line Box?

The rectangular area that contains the boxes that form a line is called a **line box**.

也就是说line box必然存在于IFC中？我认为不是

User agents flow inline-level boxes into a vertical stack of line boxes.

line box的宽度

The width of a line box is determined by a containing block and the presence of floats.

The height of a line box is determined 

A line box is always tall enough for all of the boxes it contains.

When the 

When several inline-level boxes cannot fit horizontally within a single line box, they are distributed among two or more vertically-stacked line boxes.

In general, the left edge of a line box touches the left edge of its containing block and the right edge touches the right edge of its containing block.

When the total width of the inline-level boxes on a line is less 

Any text that is directly contained inside 

        <p>Some <em>emphasized</em> text</p>
        
普通文档流