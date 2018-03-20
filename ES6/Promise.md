One of the most important and yet often misunderstood parts of programming in a language like JavaScript is how to express and manipulate program behavior spread out over a period of time.

JS异步问题来源于JS的单线程特性和Event Loop机制。
    
        // ajax(..) is some arbitrary Ajax function given by a library.
        
        var data = ajax(url);
        console.log(data);
        
在ES6之前，对于异步问题，ECMAScript原生提供的解决方案就是callback。
    
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

如何在代码中使用Promise?

Promise是一个抽象的概念，但在代码中它就是一个类，我们可以创建它的实例，也就是说：

    var p = new Promise();

在创建过程中，我们需要传入一个函数。

    new Promise( /* executor */ function(resolve, reject) { ... });
    
The `executor` function is executed immediately by the Promise implementation, passing `resolve` and `reject` functions

这个函数有两个参数：resolve和reject(这两个参数也是函数)。

具体的代码是写在这个函数中的，我们通过调用resolve和reject函数来resolve Promise。

A Promise can only have one of two possible resolution outcomes: fulfilled or rejected.

To construct a promise instance,use the `Promise(..)` constructor:

        var p = new Promise(function pr(resolve,reject){
          // ..
        });
    
The `Promise(..)` constructor takes a single function `(pr(..))`, which is called immediately and receives two control functions as arguments, usually named `resolve(..)` and `reject(..)`.

- If you call `reject(..)`, the promise is rejected, and if any value is passed to `reject(..)`, it is set as the reason for rejection.
    
- If you call 

Here's how you'd typically use a promise to refactor

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

那么，假如我们想在then方法中再发起一个AJAX请求，该怎么写代码？

如果没有写return，那么会发生什么？

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

#### Thenables

Any object(or function)  with a `then(..)` function on it is assumed to be a thenable.



    new Promise
    
A function that is passed with the arguments `resolve` and `reject`

手写一个Promise，MyPromise：

         var cb = function(resolve, reject){
              window.setTimeout(function(){
                resolve('hello');
              }, 3000);
         };
        
        var MyPromise = function(cb) {
        	function resolve(res){
          	return 
        }
          
          cb();
        };
