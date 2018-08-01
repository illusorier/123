One of the most important and yet often misunderstood parts of programming in a language like JavaScript is how to express and manipulate program behavior spread out over a period of time.

JS异步问题来源于JS的单线程特性和Event Loop机制。
    
      // ajax(..) is some arbitrary Ajax function given by a library.
      
      var data = ajax(url);
      console.log(data);
        
在ES6之前，对于异步问题，ECMAScript原生提供的解决方案就是callback。

那么，在传统程序设计语言中，异步问题一般是如何处理的？
    
The simplest (but definitely not only, or necessarily event best!) way of "waiting" from now until later is to use a function, commonly called a callback function:
    
        // ajax(..) is some arbitrary Ajax function given by a library.
        
        ajax(url, function myCallbackFunction(data){
            console.log(data);
        });
        
#### Async Console
        
`console.*`并不是标准的一部分。
        
There is no specification or set of requirements around how the `console.*` methods work - they are not officially part of JavaScript, but are instead added to JS by the *hosting environment*.

In particular, there are some 

## Event Loop

The JS engine does not run in isolation.

What is the *event loop*?

Let's conceptualize it first through some fake-ish code:

        // `eventLoop` is an array that acts as a queue (first-in, first out)
        var eventLoop = [ ];
        var event;
        
        // keep going "forever"
        while(true) {
            // perform a "tick"
            if (eventLoop.length > 0) {
                // get the next event in the queue
                event = eventLoop.shift();
        
                // now, execute the next event
                try {
                    event();
                }
                catch (err) {
                    reportError(err);
                }
            }
        }
        
As you can see, there's continuously running loop represented by the `while` loop, and each iteration of this loop is called a "**tick**"

> It's important to note that `setTimeout(..)` doesn't put your callback on the event loop. What it does is set up a timer; when the timer expires, the environment places your callback into the event loop,

## Parallel Threading

The terms "async" and "parallel" are quite different.

**async** is about the gap between *now* and *later*.

**parallel** is about things being able to occur simultaneously.

An event loop, by contrast, breaks its work into tasks and executes

## Promise

### Higher-order Functions, aka Callback Functions

**Callback functions** are derived from a programming  paradigm known as **functional programming**.

JavaScript is single threaded,meaning that two bits of script cannot run at the same time;they have to run one after another.

You've probably used events and callbacks to get around this.

Promise和Event的对比
Events are great for things that can happen multiple times on the same object-keyup,touchstart etc.
At their most basic,promises are a bit like event listeners expect:
1.A promise can only succeed or fail once.
2.If a promise has succeeded or failed and you later add a success/failure callback,the correct callback will be called,even though the event took place earlier.

在AngularJS和Vue的开发过程中，我们会用一些对Ajax进行了封装的库，如$http, vue-resource, axios等等。

Axios的github上对它的描述：Promise based HTTP client for the browser and node.js.

Terminology

A promise can be: fulfilled rejected pending settled.

A Promise is an object that is used as a 
Any Promise object is in one of three mutually exclusive states.

Asynchronous programming

异步编程

The primary mechanism for managing asynchrony has been the function callback.

Promise并不是用来取代callback。

Promises are not about replacing callbacks.

语法糖 回调代码 异步代码

#### Making and Using Promises

Promise是一个抽象的概念，但在代码中它就是一个类，我们可以创建它的实例，也就是说：

    var p = new Promise();

在创建过程中，我们需要传入一个函数，这个函数会被立刻执行。

    new Promise( /* executor */ function(resolve, reject) { ... });
    
The `executor` function is executed immediately by the Promise implementation, passing `resolve` and `reject` functions.

要注意的是，传入executor的两个参数的标识符可任意指定，不过习惯于将它们命名为`resolve`和`reject`。

Promise有三种状态

A Promise can only have one of two possible resolution outcomes: fulfilled or rejected.

- If you call `reject(..)`, the promise is rejected, and if any value is passed to `reject(..)`, it is set as the reason for rejection.
    
- If you call `resolve(..)` with no value, or any non-promise value, the promise is fulfilled.

- If you call `resolve(..)` and pass another promise,

Here's how you'd typically use a promise to refactor a callback-reliant

      funcrion ajax(url,cb) {
        // make request,eventually call `cb(..)`
      }
      
      ajax( "http://some.url.1",function handeler(err,contents){
        if (err) {
          // handle ajax error
        }
        else {
          //  handle `contents` success
        }
      } );
    
上面这段代码是不用Promise的典型API写法，该API有两个参数，一个url和一个callback。
  
Promises have a `then(..)` method that accepts one or two callback functions.

The first function (if present) is treated as the handler to call if the promise is fulfilled successfully.

The second function (if present) is treated as the handler to call if the promise is rejected explicitly, or if any error/exception is caught during resolution.

The shorthand for calling `then(null, handleRejection)` is `catch(handleRejection)`.

Both `then(..)` and `catch(..)` automatically construct and return another promise instance, which is wired to receive the resolution from whatever the **return value** is from the original promise's fulfillment or rejection handler.

then和catch方法都会自动构造并返回一个新的Promise实例。

`then`方法可以被同一个`promise`调用多次，当`promise`成功执行时，所有`onFulfilled`需按照其注册顺序依次回调；当`promise`被拒绝执行时，所有的`onRejected`需按照其注册顺序依次回调。

下面这个例子对理解Promise十分有益：

        ajax( "http://some.url.1" )
        .then(
            function fulfilled(contents){
                return contents.toUpperCase();
            },
            function rejected(reason){
                return "DEFAULT VALUE";
            }
        )
        .then( function fulfilled(data){
            // handle data from original promise's
            // handlers
        } );

In this snippet, we are returning an immediate 

A `Promise` is an object representing the eventual completion or failure of an asynchronous operation.

Most people are *consumers* of already-created promises.

比如下面的代码，我们在平常的前端开发中会经常遇到：

    axios.get(url).then(function(res){
      // ...
    });
    
那么，假如我们有这么一个需求，希望在第一个get请求返回成功后，再发起第二个get请求，并在请求成功后执行一些操作：

    
A common need is to execute two or more asynchronous operations back to back, where each subsequent operation starts when the previous operation succeeds, with the result from the previous step.

We accomplish this by creating a *promise chain*.

**Promise.prototype.then()**

The `then()` method returns a `Promise`.

- return a value, the promise returned by `then` gets resolved with the returned value as its value.

Promise/A+规范原文[1]

[1]:https://promisesaplus.com

A promise must be in one of three states: pending, fulfilled, or rejected.

A promise must provide a `then` method 

2.2.4 `onFufilled` or `onRejected` must not be called until the execution context stack contains only platform code.

2.2.6 `then` may be called multiple times on the same promise.

- If/when `promise` is fulfilled, all respective `onFulfilled` callbacks must execute in the order of

2.2.7 `then` must return a promise.