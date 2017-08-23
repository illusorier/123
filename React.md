    const element = <h1>Hello, world!</h1>;
    
This funny tag syntax is neither a string nor HTML.

It is called JSX, and it is a syntax extension to JavaScript.

We recommend using it with React to describe what the UI should look like.

JSX produces React "elements", which will be rendered to the DOM.

You can embed any JavaScript expression in JSX by wrapping it in **curly braces**.

    function formatName(user) {
      return user.firstName + ' ' + user.lastName;
    }
    
    const user = {
      firstName: Bill,
      lastName: Wei
    }

    const element = {
      <h1>
        Hello, {formatName(user)}!
      </h1>
    };

We split JSX over multiple lines for readability.

We also recommend wrapping JSX in parentheses.

It is a JavaScript XML syntax transform which lets you write HTML-ish tags in your javascript.

After compilation,JSX expressions become regular JavaScript objects.

This means

Elements are the smallest building blocks of React apps.



    <div id="root"></div>
    
We call this a **"root" DOM node** because everything inside it will be managed by React DOM.

Applications built with just React usually have a single root DOM node.

To render a React element into a root Dom node, pass both to `ReactDOM.render()`:

    const element = <h1>Hello,world!</h1>;
    ReactDOM.render(
      element,
      document.getElementById('root')
    );
    
React elements are immutable.Once you create an element,you can't change its children or attributes.

An element is like a single frame in a movie: it represents the UI at a certain point in time.

With our knowledge so far, the only way to update the UI is to create a new element, and pass it to `ReactDOM.render()`

    function tick() {
      const element = {
        <div>
          <h1>Hello, world!</h1>
          <h2>It is {new Data().toLocaleTimeString()}.</h2>
        </div>
      }
      
      Reac

## Components and Props

Components let you split the UI into independent,reusable pieces,and think about each piece in isolation.

Conceptually, components are like JavaScript function.

They accept arbitrary inputs(called "props") and 

#### Functional and Class Component

The simplest way to define a component is to write a JavaScript function:

    function Welcome(props) {
      return <h1>Hello, {props.name}</h1>
    }

This function is a valid React component because it accepts a single "props" object argument with data and returns a React element.

Elements can also represent user-defined components:
   
    const element = <Welcome name="Sara" />;
    
When React sees an element representing a user-defined component, it passes JSX attributes to this component as a single object. We call this object "props".

## State and Lifecycle
State is similar to props, but it is private and fully controlled by the component.

Components defined as classes have some additional features.Local state is exactly that.

#### Adding Lifecycle Methods to a Class
In application with many components, it's very important to free up resources taken by the component when they are destroyed.

We can declare special methods on the component class to run some code when a component mounts and unmounts.

#### Using State Correctly

## Handling Events

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

