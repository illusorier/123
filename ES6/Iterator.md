## Iterators

> It's one thing to write JS code, but it's another to properly organize it.

WTF! This is some real thinking about programming! 

遍历的问题

The `for...in` statement iterates over the enumerable properties of an object.

The `for...of`statement creates a loop iterating over iterable objects

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
    

ES6引入了`for...of`循环，作为遍历所有数据结构的统一方法。

一个数据结构只要部署了`Symbol.iterator`属性，就被视为实现了iterator接口，就可以用`for...of`循环遍历它的成员。

`for...of`循环可以使用的范围包括数组、Set和Map结构、