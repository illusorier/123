In total, there are nine new functions for searching and manipulating arrays in ES5.

        Array.prototype.indexOf
        

Looping over arrays is one of the most common forms of program control flow, and JavaScript programs in the browser are no exception.

Common tasks such as finding a node in the DOM, iterating over 

数组的遍历非常常见。

用ES5中新增的forEach方法来代替for循环。

Using forEach makes this code a little shorter, but there are other more important reasons why it is often a better choice.

There are some other common patterns of looping over arrays.

        myString
            .split(",")
            .fiter(function() {})
            .map(function() {})
            .reduce(function() {})
            
This style of programming

每个Array实例都继承的方法。

The `splice()` method changes the contents of an array by removing existing elements and/or adding new elements.

删除数组中某位置的元素，替换数组中某位置的元素

返回值

An array containing the deleted elements.

If only one element is removed, 

The `slice()` method returns a shallow copy of a portion of an array into a new array object 