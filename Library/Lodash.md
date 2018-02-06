我们为什么需要Lodash?

Even with the mainstream adoption

Lodash - A modern JavaScript utility library 

_.throttle(func, [wait=0], [options={}])

        // 1. Basic for loop.
        for(var i = 0; i < 5; i++) {
            // ....
        }

The `foo` loop is the classic workhorse for such a use-case but it pollutes the scope with an additional variable.

With array and the `apply` method, we can achieve the N loop without creating an additional variable.

        Array.apply(null, Array(5)).forEach(function(){
            // ...
        }); 

通过构造函数创建数组，避免了污染作用域。

The `Array` constructor function (which can be used without `new`), when passed more than 1 argument, creates an array containing the arguments passed in as its elements.

不是，这个技巧真的炫啊。

不过它还是太长了。

Lodash's `_.times` method

在ES6之前，函数是唯一实现独立作用域的方式。