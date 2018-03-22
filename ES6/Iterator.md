在ES6之前，JS对于对象和数组的遍历通常有哪些方案？

> It's one thing to write JS code, but it's another to properly organize it. Utilizing common patterns for organization and reuse goes a long way to improving the readability and understandability of your code.

WTF! This is some real thinking about programming! 

# Background

JavaScript原有的表示"集合"的数据结构，主要是数组和对象，ES6又添加了`Map`和`Set`。

这样就需要一种统一的机制，来处理所有不同的数据结构。    

遍历器就是这样一种机制，它为各种不同的数据结构提供统一的访问机制。

原有的遍历Array和Object的方法。

The `for...in` statement iterates over the enumerable properties of an object.

The `for...of`statement creates a loop iterating over iterable objects

# Iterators

如果使用TypeScript的写法

`Iterable` interface, which describes objects that must be able to produce iterators(可遍历的):  

        interface Iterable {
            [Symbol.iterator]() : Iterator,
        }
        
可遍历的“对象”有一个名为`Symbol.iterator`的方法，执行它可以产生一个遍历器对象。
        
遍历器：

        interface Iterator {
            next(value?: any) : IterationResult,
            // retrieve next IteratorResult
        }
        
        interface IteratorResult {
            value: any,
            // current iteration value or final return value (optional if `undefined`)
            done: boolean,
            // boolean, indicates completion status
        }

The `IteratorResult` interface specifies that the return value from any iterator operation will be an object of the form:

        { value: .. , done: true / false }
    
Built-in iterators will always return values of this form,but more properties are,of course,allowed to be present one the return value,as necessary.

### `next` Iteration

ES6 also includes several new data structure, called collections.

These collections are not only iterables themselves, but they also provide API method(s) to generate an iterator

#### Optional: `return(..)` and `throw(..)`


      

#### Iterator Loop

The ES6 `for...of` loop directly consumes a conforming 
   
If an iterator is also an iterable, it can be used directly with the `for..of` loop.

You make an iterator an iterable by giving it a `Symbol.iterator` method that simply returns the iterator itself:

        var it = {
            // make the `it` iterator an iterable
            [Symbol.iterator]() { return this; },
          
            next() {..},
            ..
        };
        
        it[Symbol.iterator]() === it;
    

当使用 `for...of`` 循环遍历某种数据结构时，该循环会自动去寻找Iterator接口。

也就是说 Iterator 接口会供 `for...of`` 消费。一种数据结构只要部署了Iterator接口，我们就称这种数据结构是“可遍历的”(iterable)。

ES6规定，默认的Iterator接口部署在数据结构的 `Symbol.iterator` 属性。

或者说，一种数据结构只要具有`Symbol.iterator`属性，就可以认为是“可遍历的”(iterable)。

`Symbol.iterator` 属性本身是一个函数，就是当前数据结构默认的遍历器生成函数。

执行这个函数，会返回一个遍历器对象。

至于属性名 `Symbol.iterator`

原生具备Iterator