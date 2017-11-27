React使用单向数据流，这意味着父组件把自身的状态作为属性传递给子组件。

也就是说当父组件的状态更新时，

Local state is a feature available only to classes.

### Using State Correctly

The only place where you can assign `this.state` is the constructor.

React may batch multiple `setState()` calls into a single update for performance.

### Adding Lifecycle Methods to a Class

In applications with many components, it's very important to free up resources taken by the components when they are destroyed.

> Often, several components need to reflect the same changing data. We recommend lifting the shared state up 

In React, sharing state is accomplished by moving it up to the closest common ancestor of the component that need it.

##### setState()

This is the primary method you use to update the user interface in response to event handler and server responses.

The first argument is an ``

You may optionally pass an object as the first argument to `setState()` instead of a function:

        setState(stateChange[, callback])