**Debounce** and **throttle** are two similar (but different!) techniques to control how many times we allow a function to be executed over time.

Having a debounced or throttled version of our function is especially useful when we are attaching the function to a DOM event.

### Debounce

The Debounce technique allow us to "group" multiple sequential calls in a single one.

这里有两种解决方案：trailing和leading。