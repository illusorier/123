In the visual formatting model, each element in the document tree generates zero or more boxes according to the box model.

The layout of these boxes is governed by:

-
-
-
-

The `display` property, specifies a box's type.

display属性决定了元素的盒子类型

In CSS 2.2, 

**Block-level elements** are elements which generate a block-level box.

块级元素会产生块级盒子

Values of the `display` property that make an element block-level element: `block`, `list-item`, and `table`.

**Block-level boxes** are boxes that participate in a BFC.

If a block container box has a block-level box inside it, then we force it to have only block-level boxes inside it.

        <div>
            Some text
            <p>More text</p>
        </div>

**Inline-level elements**

Inline-level el

行内元素会产生行内级盒子

In CSS, a **replaced element** is an element whose 

In a BFC, boxes are laid  out one after the other, vertically, beginning at the top of a containing block.

An inline formatting context is established by a block container box that contains no block-level boxes.

Any text that is directly contained inside 

        <p>Some <em>emphasized</em> text</p>