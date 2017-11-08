> It's one thing to write JS code, but it's another to properly organize it. Utilizing common patterns for organization and reuse goes a long way to improving 

WTF! This is some real thinking about programming! 

## Background

JavaScript原有的表示"集合"的数据结构，主要是数组和对象，ES6又添加了`Map`和`Set`。

这样就需要一种统一的机制，来处理所有不同的数据结构。    

遍历器就是这样一种机制，它为各种不同的数据结构提供统一的访问机制。

原有的遍历Array和Object的方法。

The `for...in` statement iterates over the enumerable properties of an object.

The `for...of`statement creates a loop iterating over iterable objects

## Iterators

        interface Iterable {
          [Symbol.iterator]() : Iterator,
        }
        
        interface Iterator {
          next(value?: any) : IterationResult,
        }
        
        interface IterationResult {
          value: any,
          done: boolean,
        }

An iterator is a structured pattern for pulling information from a source in one-at-a-time fashion.

        Iterator [required]
          next() {method}: retrieves next IteratorResult
      
There are two optional members that some iterators are extended with:

        Iterator [optional]
          return() {method}: stops iterator and returns IteratorResult
          throw() {method}: signals error and returns IteratorResult
      
The `IteratorResult` interface is specified as:

        IteratorResult
          value {property} current
    
There's also an `Iterable` interface,which describes objects that must be able to produce iterators.

        Iterable
          @@iterator() {method}: produces an Iterator

      
##### IteratorResult

The `IteratorResult` interface specifies that the return value from any iterator operation will be an object of the form:

        { value: .. , done: true / false }
    
Built-in iterators will always return values of this form,but more properties are,of course,allowed to be present one the return value,as necessary.

#### `next` Iteration

#### Optional: `return(..)` and `throw(..)`


      

#### Iterator Loop
   
If an iterator is also an iterable,it can be used directly with the `for..of` loop.You make an iterator an iterable by giving it a `Symbol.iterator` method that simply returns the iterator itself:

        var it = {
          [Symbol.iterator]() { return this; },
          
          next() {..},
          ..
        };
        
        it[Symbol.iterator]() === it;
    

当使用 `for...of`` 循环遍历某种数据结构时，该循环会自动去寻找Iterator接口。

也就是说 Iterator 接口会供 `for...of`` 消费。一种数据结构只要部署了Iterator接口，我们就称这种数据结构是“可遍历的”(iterable)。

ES6规定，默认的 Iterator 接口部署在数据结构的 `Symbol.iterator` 属性。

一种数据结构只要部署了Iterator接口，我们就称这种数据结构是“可遍历的”(iterable)。

`Symbol.iterator` 属性本身是一个函数，就是当前数据结构默认的遍历器生成函数。

执行这个函数，会返回一个遍历器对象。

至于属性名 `Symbol.iterator`