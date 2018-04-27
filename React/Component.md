> Components let you split the UI into independent, reusable pieces, and think about each piece in isolation.

Conceptually, components are like JavaScript function.

可以把组件理解为一个JS函数。

They accept arbitrary inputs (called "props") and return React elements describing what should appear on the screen.

## Functional and Class Component

在React中，有两种方式去声明组件：Functional or Class。

The simplest way to define a component is to write a JavaScript function:

    function Welcome(props) {
      return <h1>Hello, {props.name}</h1>
    }
        
This function is a valid React component because it accepts a single "props" (which stands for properties) object argument with data and returns a React element.

We call such components "functional" because they are literally JavaScript functions.

You can also use an `ES6 class` to define a component:

    class Welcome extends React.Component {
        render() {
            return <h1>Hello, {this.props.name}</h1>;
        }
    }

The above two components are equivalent from React’s point of view.

Classes have some additional features.

## Rendering a Component

Previously, we only encountered React elements that 

### Composing Components 

Components can refer to other components in their output.

This lets us use the same component abstraction for any level of detail.

A button, a form, a dialog, a screen: in React apps, all those are commonly expressed as components.

        function Welcome(props) {
          return <h1>Hello, {props.name}</h1>;
        }
        
        function App() {
          return (
            <div>
              <Welcome name="Sara" />
              <Welcome name="Cahal" />
              <Welcome name="Edite" />
            </div>
          );
        }
        
        ReactDOM.render(
          <App />,
          document.getElementById('root')
        );
        
Typically, new React apps have a single `App` component at the very top.


### Props are Read-Only

Whether you declare as a function or a class, it must never modify its own props.

> All React components must act like pure functions with respect to their props.
    