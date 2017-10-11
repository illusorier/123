    // ajax(..) is some arbitrary Ajax function given by a library.
    var data = ajax( url );
    
    console.log( data );
    
The simplest (but definitely not only, or )
    
You may have heard that it's possible to make synchronous Ajax requests.

While that's technically true, you should never, ever do it, under any circumstances, because it locks the browser UI and prevents any user interaction.

## Event Loop

    // `eventLoop` is an array that acts as a queue (first-in, first out)
    var eventLoop = [ ];

It's important to note that `setTimeout(..)` doesn't put your callback on the event loop.

What it does is set up a timer; when the timer expires, the environment places your callback into the event loop,

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

Terminology

A promise can be: fulfilled rejected pending settled.

A Promise is an object that is used as a 
Any Promise object is in one of three mutually exclusive states.


Promises are not about replacing callbacks.Promises provide a trustable intermediary -- that is,between your calling code and the async code that will perform the task -- to manage callbacks.

A 

#### Making and Using Promises

To construct a promise instance,use the `Promise(..)` constructor:

    var p = new Promise( function pr(resolve,reject){
      // ..
    });
    
The `Promise(..)` constructor takes a single function `(pr(..))`,which is called immediately and receives two control functions as arguments,usually named `resolve(..)` and `reject(..)`.

- If you call `reject(..)`,the promise is rejected,and if any value is passed to `reject(..)`,it is set as the reason for rejection.
    
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
  

Promises have a `then(..)` method that accepts one or two callback functions.The first function (if present) is treated as the handler to call if the promise is fulfilled successfully.

The shorthand for calling `then(null,handleRejection)` is `catch(handleRejection)`.

Both `then(..)` and `catch(..)` automatically construct and return another promise instance,

#### Thenables

Any object(or function)  with a `then(..)` function on it is assumed to be a thenable.
