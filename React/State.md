问题：如何update UI？

React使用单向数据流，这意味着父组件把自身的状态作为属性传递给子组件。

也就是说当父组件的状态更新时，子组件相应得重新渲染。

React的[官方文档](https://reactjs.org/docs/state-and-lifecycle.html)中有这样一个例子：在引入state这个概念前，

Local state is a feature available only to classes.

### Using State Correctly

The only place where you can assign `this.state` is the constructor.

React may batch multiple `setState()` calls into a single update for performance.

### Adding Lifecycle Methods to a Class

In applications with many components, it's very important to free up resources taken by the components when they are destroyed.

    compoenntDidMount() {
      // ...
    }
    
    componentWillUnmount() {
      // ...
    }

### Lifting State Up

> Often, several components need to reflect the same changing data. We recommend lifting the shared state up to their closest common ancestor.

In React, sharing state is accomplished by moving it up to the closest common ancestor of the component that need it.

假如我们有个组件，这个组件有个input提供输入，然后实时显示input输入的值。

这个组件的功能很简单，但假如我们创建了多个该组件的实例，我们希望在一个实例中input的修改能得到同步，该怎么做？

我们可以将“这个值”作为属性传入这些实例中，那么这些实例显示的都是同一个值。
但这就产生了一个问题，子组件不能修改这些"props"。

React是如何解决这个问题的？

In React, this is usually solved by making a component "controlled".

Just like the DOM `<input>` accepts both a `value` and an `onChange` prop.

### Containment

Some components do not know their children ahead of time.

We recommend that such components use the special `children` prop to pass children elements directly into their output.

还有一种很常见的需求，组件所包含的模板是动态的。

Sometimes you might need multiple "holes" in a component.

##### setState()

`setState()` enqueues changes to the component state and tells React that this component and its children need to be re-rendered with the updated state.

This is the primary method you use to update the user interface in response to event handler and server responses.

The first argument is an `updater` function with the signature:

        (prevState, props) => stateChange

You may optionally pass an object as the first argument to `setState()` instead of a function:

        setState(stateChange[, callback])