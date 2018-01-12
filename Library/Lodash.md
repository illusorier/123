我们为什么需要Lodash?

Even with the mainstream adoption

Lodash - A modern JavaScript utility library 

_.throttle(func, [wait=0], [options={}])

        // 1. Basic for loop.
        for(var i = 0; i < 5; i++) {
            // ....
        }

The `foo` loop is the classic workhorse for such a use-case but it pollutes the scope with an additional variable.

在ES6之前，函数是唯一实现独立作用域的方式。