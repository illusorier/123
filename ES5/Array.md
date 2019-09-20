In total, there are nine new functions for searching and manipulating arrays in ES5.

        Array.prototype.indexOf
        

Looping over arrays is one of the most common forms of program control flow, and JavaScript programs in the browser are no exception.

Common tasks such as finding a node in the DOM, iterating over 

数组的遍历非常常见。

用ES5中新增的forEach方法来代替for循环。

Using forEach makes this code a little shorter, but there are other more important reasons why it is often a better choice.

Declarative 

声明式

There are some other common patterns of looping over arrays.

        myString
            .split(",")
            .fiter(function() {})
            .map(function() {})
            .reduce(function() {})
            
This style of programming is commonly referred to as functional programming.

每个Array实例都继承的方法。

The `splice()` method changes the contents of an array by removing existing elements and/or adding new elements.

删除数组中某位置的元素，替换数组中某位置的元素

返回值

An array containing the deleted elements.

If only one element is removed, 

The `slice()` method returns a shallow copy of a portion of an array into a new array object 

Array.prototype.forEach()

The `forEach()` method executes a provided function once for each array element.

> There is no way to stop a forEach() loop other than by throwing an exception. If you need such behavior, the `forEach()` method is the wrong tool. Use a plain loop or `for...of` instead.

Array.prototype.map()

Array类的实例对象所继承的方法，是对该实例的操作。

array-like

要访问数组里特定位置的元素

通过循环遍历数组

迭代(iterate)

递归(recursion):反复调用自身

迭代和递归中都包含了重复和循环。

The concept of Recursion and Iteration is to execute a set of instructions repeatedly.

Iteration is a loop being excuted until a certain condition is met.

Recursion makes code smaller while iteration makes it longer.

循环

遍历数组

traverse an array: do something with each element of an array.

通过for循环可以遍历数组

可以使用数组的length属性

添加元素到数组的开头和末尾

        Array.prototype.every = function(arr) {
                
        }


表达式 => for语句

数组中最后一个元素的下标的值是length-1

几乎所有的编程语言都原生支持数组类型，因此数组是最简单的内存数据结构。

JavaScript也不例外，此外，我们也可以用Object自主创建一些常用的数据类型。

我们在数组中保存的数据是动态的，是变化的，因此我们需要对数组进行各种操作，以对应数据的变化。

那么，我们用什么形式在代码中去实现这些操作呢，