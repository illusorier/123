There are many libraries that make up the Reactive Extensions for JavaScript.

Reactive Extensions for JavaScript (RxJS) is a reactive streams library that allows you to work with *asynchronous data streams*. 

RxJS can be used both in browser or in the server-side using Node.js.

**Asynchronous data streams** are not new.

They have been around since Unix systems, 

### Observable sequence

可观察序列

In RxJS, you represent **asynchronous data streams** using observable sequences or also just called observables.

有哪些方法可以创造一个可观察序列？

- When using the **push pattern**, 

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

