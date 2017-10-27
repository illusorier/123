## Buffer

Prior to the introduction of `TypedArray` in ES6, the JavaScript language had no mechanism for reading or manipulating streams of binary data.

## Events

异步的、事件驱动的架构。 

Much of the Node.js core API is built around an idiomatic asynchronous event-driven architecture in which certain kinds of objects (called "`emitters`") periodically emit named events that    

All objects that emits events 

When the `EventEmitter` object emits (触发)

与DOM

## File System

One of the most common things you'll want to do with just about any programming language is open and read a file.

All the methods have asynchronous and synchronous forms.

####  fs.readFile

This is the most common way to read a file with Node.js.

#### fs.createReadStream

A readable stream object can be useful for a lot of reasons, a few of which include:

## Path

The `path` module provides utilities for working with file and directory paths.

##### path.resolve([...paths])

The `path.resolve()` method resolves a sequence of 

这里要注意的是路径片段的组合是从右往左的。

The given sequence of paths is processes from right to left, with each subsequent `path` prepended until an absolute

## Process

The `process` object is an instance of EventEmitter.

## Net

The `net` module provides an asynchronous network API

##### net.createServer

## Stream

A stream is an abstract interface for working with streaming data in Node.js

流在Node.js中是处理流数据的抽象接口。

All streams are instances of `EventEmitter`.

While it is important for all Node.js users to understand how stream work, the `stream` module itself is most useful for developers that are creating new types of stream instances.

There are four fundamental stream types within Node.js:

- Readable - 可读的流
- Writable - 可写的流
- Duplex - 可读写的流
- Transform - 

#### API for Stream Consumers

流消费者

Almost all Node.js applications, no matter how simple, use streams in some manner.

#### Writable Streams

Writable streams are an abstraction for a destination to which data is written.

All Writable streams implement the interface defined by the `stream.Writable` class.

所有Writable流都实现了`stream.Writable`类定义的接口。

#### Readable Streams

Readable streams are an abstraction for a source from which data is consumed.

可读流（Readable streams）是对提供数据的 源头 （source）的抽象。

#### Two Modes

Readable streams effectively operate in one of two modes: flowing and paused.

可读流事实上工作在下面两种模式之一：flowing 和 paused 。

When in flowing mode, data is read from the underlying system automatically and provided to an application as quickly as possible using events via the `EventEmitter` interface.

When in flowing mode, 

All Readable streams begin in paused mode but can be switched to flowing mode in one of the following ways:

#### Three States

The "two modes" of operation for a Readable stream are a simplified abstraction for 
    
Specifically, at any given point in time, every Readable is in one of three possible states:

- readable._readableState.flowing