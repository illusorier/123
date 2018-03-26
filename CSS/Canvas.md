`<canvas>` is an HTML element which can be used to draw 

`<canvas>` element has only two attributes, `width` and `height`.

These are both optional and can also be set using DOM properties.

When no `width` and `height` attributes are specified, the canvas will initially be **300 pixels** wide and **150 pixels** high.

The `id` attribute is not specific to the `<canvas>` element but is one of the global HTML attributes which can be applied to any HTML element.

2D rendering context

The `<canvas>` element creates a fixed-size drawing surface.

The canvas is initially blank.

To display something, a script first needs to access the rendering context and draw on it.

The `<canvas>` element has a method called `getContext()`, 

For 2D graphic, you specify "2d" to get a `CanvasRenderingContext2D`.

![](../assets/canvas-1.png)

Unlike SVG, `<canvas>` only supports one primitive shape: rectangles.

The only other primitive shapes are *paths*.

### HTMLCanvasElement

### CanvasRenderingContext2D

