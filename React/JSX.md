在例如Angular和Vue这样的框架当中，我们依然需要书写HTML，在React当中，我们用JSX在JS中书写HTML。

JSX并不是类似于ES6或TypeScript的存在，它无法通过一个通用的编译器转换成"原生"的JS。

比如下面这段JSX：

    const element = <h1>Hello, world!</h1>;
    
经过Babel编译后的结果是这样的：

    "use strict"
    
    var element = React.createElement(
      "h1"
      null,
      "hello, world!"
    );
    
是不是可以这么理解：JSX是FaceBook为了配合React而推出的？
    
在Vue中，

### What is JSX？

JSX is a XML-like syntax extension to ECMAScript without any defined semantics.

It's NOT intended to be implemented by engines or browsers.

It is called JSX, which is a syntax extension to JavaScript.

JSX may remind you of a template language, but it comes with the full power of JavaScript.

We recommend using it with React to describe what the UI should look like.

JSX  => produce => React "element" => rendered into => DOM

### Expressions And JSX

> JSX不仅仅可以用于表现静态的HTML元素，你还可以将JS中的表达式包裹花括号后放在JSX中。

You can embed any JavaScript expression in JSX by wrapping it in **curly braces**.

Angular和Vue是否也有类似的特性？

> You may also use curly braces to embed a JavaScript expression in an attribute:

    const element = <img src={user.avatarUrl}></img>;
      
We 

推荐用括号包裹JSX

After compilation, JSX expressions become regular JavaScript function calls and evaluate to JavaScript objects.
        
### JSX In Depth
        
> Fundamentally, JSX just provides syntactic sugar for the `React.createElement(component, props, ...children)` function.

Each JSX element is just syntactic sugar for calling `React.createElement()`.

You will not typically invoke the following methods directly if you are using JSX.

- createElement()

- createFactory()
