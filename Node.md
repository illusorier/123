## Buffer

Prior to the introduction of `TypedArray` in ES6, the JavaScript language had no mechanism for reading or manipulating streams of binary data.

## Events

异步的、事件驱动的架构。 

Much of the Node.js core API is built around an idiomatic asynchronous event-driven architecture in which certain kinds of objects (called "`emitters`") periodically 

All objects that emits events 

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

All streams are instances of `EventEmitter`.