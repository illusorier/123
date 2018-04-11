The globally valid rule for SVG files is, that *later* elements are rendered *atop previous* elements.

SVG files on the web can be displayed directly in the browser or embedded in HTML files

For all elements, SVG uses a coordinate system or **grid** system similar to the one used by canvas (and by a whole lot of other computer drawing routines).
 
That is, the top left corner of the document is considered to be the point (0,0), or point of origin.
 
Positions are then measured in pixels from the top left corner, with the positive x direction being to the right, and the positive y direction being to the bottom.

## Basic shapes

There are several basic shapes used for most SVG drawing.

SVG有六种基本图形：

- rect 矩形
- circle 圆形
- ellipse 椭圆
- line 线段
- polyline 折线
- polygon 多边形

To insert a shape, you create an element in the document.

Different elements correspond to different shapes and take different attributes to describe the size and position of those shapes.

`Circle`

The circle element draws a circle on the screen.

There are really only 3 attributes that are applicable here.

## Paths

路径

The `<path>` element is the most powerful element in the SVG library of basic shapes.

Using a path element you can draw rectangles 

The shape of a path element is defined by one attribute: `d`.

d: A list of points and other information about how to draw the path.

### Line commands

All of the commands comes in two variants.

There are five line commands for `<path>` node.

Each one just draws a straight line between two points.

The first command is the "Move To" or M.

There are three commands that draw lines.

The most generic is the "Line To" command, called with L.

L takes two parameters - x and y coordinates - and draws a line from the current position to a new position.

Z draws a straight line from the current position back to the first point of the path.

## Fills and Strokes

Basic coloring can be done by setting two attributes on the node: `fill` and `stroke`.

## Transformations

The `<g>` SVG elements is a container used to group other SVG elements.

Transformations applied to the `<g>` element are performed on all of its child elements, and any of its attributes are inherited by its child elements.



