什么是观察者模式？

The **observer pattern** is a software design pattern in which an object, called the subject, maintains a list of its dependents, called **observers**, and notifies them automatically of any state changes, usually by calling one of their methods.

Observable 可被观察的

Observer 观察者

当Observable发生变化，Observer就会做出相应的反应

比如看下面这个简单的例子，可被观察的是window上的click事件：

        Rx.Observable.fromEvent(window, 'click')
            .subscribe(e => {
                console.log('click');
            })
            
上面这段代码代码和直接addEventListener的最终效果是一样的。

什么是RxJS？

RxJS is a library for composing asynchronous and event-based programs by using observable sequences.

It extends the observable pattern to support 

ReactiveX combines the Observer pattern with the iterator pattern and functional programming with collections 

> Think of RxJS as Lodash for events

There are many libraries that make up the Reactive Extensions for JavaScript.

You are able to create data streams of anything, not just from click and hover events.

Reactive Extensions for JavaScript (RxJS) is a reactive streams library that allows you to work with *asynchronous data streams*. 

RxJS can be used both in browser or in the server-side using Node.js.

- **Asynchronous**, in JavaScript means we can call a function and register a *callback* to be notified when results are available,  

**Asynchronous data streams** are not new.

异步数据流

They have been around since Unix systems, and come in different flavours and names: streams (Node.js), pipes (Unix) or async pipes (Angular2).

### Observable sequence

可观察序列

In RxJS, you represent **asynchronous data streams** using observable sequences or also just called observables.

有哪些方法可以创造一个可观察序列？

Converting to observables

        // From one or multiple values
        Rx.Observable.of('foo', 'bar');
        
        // From array of values
        Rx.Observable.from([1,2,3]);
        
        // From an event
        Rx.Observable.fromEvent(document.querySelector('button'), 'click');
        
Creating observables        
        
- When using the **push pattern**, 

> Observables programming has two separate stages: setup and execution.

### Observables and Operators

RxJS combines **Observables** and **Operator** so we can subscribe to streams and react to changes using composable operations.

> Observables programming has two separate stages: setup and execution.

#### Observables / Observers

对比DOM，Observables => 事件  Observers => 回调 是不是可以这么理解？

Observables get their name from the Observer design pattern.

观察者模式

The **Observable** sends notifications while the **Observer** receives them.

##### Rx.Observable.interval(period, [scheduler])

Returns an observable sequence that produces a value after each period.

##### Rx.Observable.prototype.subscribe([observer] |)

You can pass in your observer when calling 

##### Rx.Observer.create([onNext], [onError], [onCompleted])

产生观察者

是不是可以把观察者理解为一系列函数？

Creates an observer from the specified 

### Using RxJS with Angular1

`rx.angular.js` serves as a bridge between RxJS and AngularJS.

**Subscription**: represents the execution of an Observable, 

**Operators**: are pure functions that enable a functional programming style 