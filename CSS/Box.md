盒模型应当是理解CSS的第一个入口。

HTML中的每个元素在页面中都是一个矩形盒子。

Each box has a *content area* and optional surrounding *padding*, *border*, and *margin* areas.

Determining the size, properties - like its color, background, borders aspect - and the position of these boxes is the goal of the rendering engine.

每个盒子有4个edge: the **margin edge**, **border edge**, **padding edge**, and **content edge**.

The **content area** is the area containing the real content.

It

If the CSS **box-sizing** property is set to default, the CSS properties **width**, **min-width**, **max-width**, **height**, **min-height** and **max-height** control the content size.

The **padding area** extends to the border surrounding the padding.

**content area**的背景会扩展到**padding area**。

When the content area has a background, color or image set on it, this will extend into the padding, which 

## Margins,Padding,and Borders.

Every HTML tag is surrounded by a world of properties that affect how the tag appears in a web browser.

Some properties - like borders and background colors - are immediately obvious to the naked eye.

Others, though, are invisible - like padding and margin. They provide a bit of empty space on one or more sides of a tag.

To a browser,any tag is a box with something inside it - text, an image, or even other tags containing other things.

Surrounding the content are different properties that make up the box:

- **padding** is the space between the content and the content's border.

- **border** is the line that's drawn around each edge of the box

- **margin** is what separates one tag from another.

For a given tag, you can use any or all of these properties in combination.

If you don't adjust any of these properties, then you'll end up with the browser's settings.

#### Margin and Padding Shorthand

The margin property may be specified using one, two, three, or four values. Each value is a `<length>`, a `<percentage>`, or the keyword `auto`.

- One value applies to all four sides.
- Two values apply first to top and bottom, the second one to left and right.
- Three values apply first to top, second to left and right and third to bottom.

#### Inline, Block, and Other Display Settings

In most cases, CSS works the same for inline boxes and  block boxes.

You can't increase the height of the inline element with top or bottom padding or margins.


### Determining Height and Width

The *height* and *width* properties assign a height and width to the content area of a style.

Type these property followed by any of the CSS measurement systems you've already encountered.

For the *width* property, percentage values are based on the percentage of the width of the style's containing element.

Percentage values for the *height* property work similarly.

##### Calculating a Box's Actual Width and Height

虽然*width*和*height*这两个属性看起来非常直观，但还是有一些需要注意的地方。



There's a difference between the value you set for a style's width and height and the amount of space that a web browser actually uses to display the style's box.

The *width* and *height* properties set the width and height of the *content area* of the style.

The general rule of thumb for setting heights on page elements is *don't*.

#### Redefining Box Width with Box-Sizing

##### content-box

This is the initial and default value as specified by the CSS standard. 

The width and height properties are measured including only the content


### Wrapping Content with Floating Elements

HTML normally flows from the top of the browser window down to the bottom, one headline, paragraph, or block-level element on top of another.

You can spice up your pages plenty with one little CSS property - float.

The *float* property moves an element to either the left or right edge of their *containing element*.

In the process, content below the floated element moves up and wrap around the float.

Floating elements are ideal for moving supplemental information out of the way of the page's main text.


- **left**:

You can even use the *float* property with an inline element, such as the `<img>` tag.

A web browser treats a floated inline element just like a block-level element.

#### Backgounds

To the frustration of many web designers, backgrounds and borders don't react to floated elements the same way content does.

First

#### Stopping the Float

The *clear* property accepts the following options:

- **left**: The style will drop be

### Building Float-Based Layouts

Float-based layouts take advantage of the *float* property to 

The *none* value turns off any floating and positions the element like a normal, unfloated element.

Unless you're floating an image with a predefined width
