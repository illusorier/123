The globally valid rule for SVG files is, that *later* elements are rendered *atop previous* elements.

SVG files on the web can be displayed directly in the browser or embedded in HTML files

For all elements, SVG uses a coordinate system or **grid** system similar to the one used by canvas (and by a whole lot of other computer drawing routines).
 
That is, the top left corner of the document is considered to be the point (0,0), or point of origin.
 
Positions are then measured in pixels from the top left corner, with the positive x direction being to the right, and the positive y direction being to the bottom.

There are several basic shapes used for most SVG drawing.

To insert a shape, you create an element in the document.

Different elements correspond to different shapes 

The `<path>` element is the most powerful element in the SVG library of basic shapes.

The shape of a path element is defined by one attribute: `d`.

