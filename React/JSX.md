在例如Angular和Vue这样的框架当中，我们依然需要书写HTML，在React当中，我们用JSX在JS中书写HTML，是否可以理解为一种特殊的数据结构？ 

### What is JSX？

JSX is a XML-like syntax extension to ECMAScript without any defined semantics.

It's NOT intended to be implemented by engines or browsers.
   
        const element = <h1>Hello, world!</h1>;

It is called JSX, which is a syntax extension to JavaScript.

JSX may remind you of a template language, but it comes with the full power of JavaScript.

We recommend using it with React to describe what the UI should look like.

JSX  => produce => React "element" => rendered into => DOM

### Expressions And JSX

> JSX不仅仅可以用于表现静态的HTML，你还可以将JS中的表达式放在JSX中。

You can embed any JavaScript expression in JSX by wrapping it in **curly braces**.

仅就这点而已，React和Angular、Vue是类似的，后面两种框架也支持在HTML中书写JS表达式。

> You may also use curly braces to embed a JavaScript expression in an attribute:

        const element = <img src={user.avatarUrl}></img>;
        
### JSX In Depth
        
> Fundamentally, JSX just provides syntactic sugar for the `React.createElement(component, props, ...children)` function.

Each JSX element is just syntactic sugar for calling `React.createElement()`.

You will not typically invoke the following methods directly if you are using JSX.

- createElement()

- createFactory()
