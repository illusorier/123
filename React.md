在例如Angular和Vue这样的框架当中，我们依然需要书写HTML，在React当中，我们用JSX在JS中书写HTML。

什么是XML?

In computing, **Extensible Markup Language(XML)** is a markup language that defines a set of rules for encoding documents in a format that is both human-readable and machine-readable through use of tags that can be created and defined by users.

什么是JSX？

JSX is a XML-like syntax extension to ECMAScript without any defined semantics.

It's NOT intended to be implemented by engines or browsers.



JSX和JQuery中的`.before()`,`.after()`对比, cheap。

## Installation

While React can be used without a build pipeline, we recommend setting it up so you can be more productive.

## Introducing JSX
    
    const element = <h1>Hello, world!</h1>;
    
This funny tag syntax is neither a string nor HTML.

It is called JSX, and it is a syntax extension to JavaScript.

We recommend using it with React to describe what the UI should look like.

JSX may remind you of a template language, but it comes with the full power of JavaScript.

JSX produces React "elements", which will be rendered to the DOM.

#### Embedding Expressions in JSX

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
    
    ReactDOM.render(
      element,
      document.getElementById('root')
    };

We split JSX over multiple lines for readability.

We also recommend wrapping JSX in parentheses to avoid the pitfalls of automatic semicolon insertion.

It is a JavaScript XML syntax transform which lets you write HTML-ish tags in your javascript.

#### JSX is an Expression Too

After compilation, JSX expressions become regular JavaScript objects.

This means that you can use JSX inside of `if` statement and `for` loops, assign it to variables, accept it as arguments, and return it from functions:

    function getGreeting(user) {
      if (user) {
        return <h1>Hello, {formatName(user)}!</h1>;
      }
      return <h1>Hello, Stranger.</h1>;
    }
    
#### Specifying Attributes with JSX

You may use quotes to specify string literals as attributes:

    const element = <div tabIndex="0"></div>;
    
You may also use curly braces to embed a JavaScript expression in an attribute:

    const element = <img src={user.avatarUrl}></img>;
    
You should either use quotes (for string values) or curly braces (for expressions), but not both in the same attribute.

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

## Components and Props

Components let you split the UI into independent, reusable pieces, and think about each piece in isolation.

Conceptually, components are like JavaScript function.

They accept arbitrary inputs (called "props") and return React elements describing what should appear on the screen,

#### Functional and Class Component

The simplest way to define a component is to write a JavaScript function:

    function Welcome(props) {
      return <h1>Hello, {props.name}</h1>
    }

This function is a valid React component because it accepts a single "props" object argument with data and returns a React element.

You can also use an `ES6 class` to define a component:

    class Welcome extends React.Component {
       render() {
         return <h1>Hello, {this.props.name}</h1>;
       }
    }

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





## Handling Events

Handling events with 

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

