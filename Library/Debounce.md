**Debounce** and **throttle** are two similar (but different!) techniques to control how many times we allow a function to be executed over time.

Having a debounced or throttled version of our function is especially useful when we are attaching the function to a DOM event.

背景:

在某些情景下，DOM事件会多次触发，但我们希望callback多次执行。

### Debounce

The Debounce technique allow us to "group" multiple sequential calls in a single one.

这里有两种解决方案：trailing和leading。

- leading: Trigger the function execution immediately, so it behaves exactly as the original non-debounce handler, but not fire again until there is a pause in the rapid calls.

Implementation: Lodash

### Throttle

By using `_.throttle`, we don't allow to our function to execute more than once every X milliseconds.

The main difference between this and debouncing is that throttle guarantees the execution of the function regularly, at least every X milliseconds.