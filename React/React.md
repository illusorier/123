目前来说，相比Angular2+当中用decorator声明组件的方式，我更喜欢React中通过继承声明组件的方式。

什么是XML?

In computing, **Extensible Markup Language(XML)** is a markup language that defines a set of rules for encoding documents in a format that is both human-readable and machine-readable through use of tags that can be created and defined by users.

JSX和JQuery中的`.before()`,`.after()`对比, cheap。

## Installation

使用React需要安装两个依赖包：react, react-dom.

    import React from 'react';
    import ReactDOM from 'react-dom';
    

While React can be used without a build pipeline, we recommend setting it up so you can be more productive.

#### JSX Represents Objects

Babel compiles JSX down to `React.createElement()` calls.

`React.createElement()` performs a few checks to help you write bug-free code but essentially it creates an object like this:

    const element = React.createElement(
      type: 'h1',
      props: {
        className: 'greeting',
        children: 'Hello, world!'
      }
    );
    
These objects are called "React elements".

You can think of them as descriptions of what you want to see on the screen.

React reads these objects and uses them to construct the DOM and keep it up to date.

## Rendering Elements

Elements are the smallest building blocks of React apps.

An element describes what you want to see on the screen:

    const element = <h1>Hello, world</h1>;
    
Unlike browser DOM elements, React elements are plain objects, and are cheap to create.

React DOM takes care of updating the DOM to match the React elements.

#### Rendering an Element into the DOM

    <div id="root"></div>
    
We call this a **"root" DOM node** because everything inside it will be managed by React DOM.

Applications built with just React usually have a single root DOM node.

To render a React element into a root Dom node, pass both to `ReactDOM.render()`:

    const element = <h1>Hello,world!</h1>;
    
    ReactDOM.render(
        element,
        document.getElementById('root')
    );
    
#### Updating the Rendered Element

React elements are immutable.

Once you create an element, you can't change its children or attributes.

An element is like a single frame in a movie: it represents the UI at a certain point in time.

With our knowledge so far, the only way to update the UI is to create a new element, and pass it to `ReactDOM.render()`

    function tick() {
      const element = (
        <div>
          <h1>Hello, world!</h1>
          <h2>It is {new Date().toLocaleTimeString()}.</h2>
        </div>
      );
      ReactDOM.render(
        element,
        document.getElementById('root')
      );
    }
    
    setInterval(tick, 1000);
    
> In practice, most React apps only call `ReactDOM.render()` once.

Elements can also represent user-defined components:
   
    const element = <Welcome name="Sara" />;
    
When React sees an element representing a user-defined component, it passes JSX attributes to this component as a single object. We call this object "props".

## State and Lifecycle

State is similar to props, but it is private and fully controlled by the component.

Components defined as classes have some additional features.

Local state is exactly that: a feature available only to classes.

具体的例子可以查看[此处][1]

[1]:https://reactjs.org/docs/state-and-lifecycle.html

#### Adding Lifecycle Methods to a Class

In application with many components, it's very important to free up resources taken by the component when they are destroyed.

We can declare special methods on the component class to run some code when a component mounts and unmounts.

These methods are called "lifecycle hooks".



#### Using State Correctly

There are three things you should know about `setState()`.

##### Do Not Modify State Directly

For example, this will not re-render a component:

        // Wrong
        this.state.comment = 'Hello';
        
Instead, use `setState()`:

        // Correct
        this.setState({comment: 'Hello'});
        
The only place where you can assign `this.state` is the constructor.

## Conditional Rendering

Condition rendering in React works the same way conditions work in JavaScript.

## Lists and Keys

#### Rendering Multiple Components



## React Top-Level API

`React` is the entry point to the React library.

#### Components

##### React.Component

`React.Component` is the abstract base class for React components when they are defined using ES6 classes, so it is rarely make sense to refer it directly.

Normally you would define a React component as a plain JavaScript class.

Instead, you will typically subclass it, and define at least a `render()` method.

**render()**

The `render()` method is required.

##### React.PureComponent

##### createClass()
If you don't use ES6 yet,you may use the React.createClass() helper instead to create a component class.

    var Greeting = React.createClass({
      render: function() {
        return <h1>Hello, {this.props.name}</h1>;
      }
    });

#### createElement()
    React.createElement(
      type,
      [props],
      [...children]
    )
Create and return a new **React element** of the given type.The type argument can be either a tag name 
    
Code written with JSX will be converted to use `React.createElement()`. You will not typically invoke `React.createElement()` directly if you are using JSX.

## ReactDOM

The `react-dom` package provides DOM-specific methods that can be used at the top level of your app.

#### render()

    ReactDOM.render(
      element,
      container,
      [callback]
      
Render a React element into the DOM in the supplied `container` and return a reference to the component ()


## Virtual DOM

While HTML is a text, the DOM is an in-memory representation of this text.

> Compare it to a process being an instance of a program. You can have multiple processes of the same one program.

