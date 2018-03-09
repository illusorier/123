**CSS transitions** provide a way to control animation speed when changing CSS properties.

Instead of having property changes take effect immediately, you can cause the changes in a property  to take place over a period of time.

Which CSS properties can be transitioned?

> The `auto` value if often a very complex case.

CSS can't animate between `display: none` and `display: block`, `height: 0` and `height: auto`.

Use `max-height` instead of `height`.

        .from {
            max-height: 0;
        }
        
        .to {
            max-height: 500px; // This value must be large enough.
        }
