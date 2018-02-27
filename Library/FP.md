继"面向对象编程"之后，"函数式编程"是否会成为下一个编程语言的主流范式？

World's most popular functional programming language: JavaScript.

> A pure function is a function that, given the same input, will always return the same output and does not have any observable side effect.\

You can call a function with fewer arguments than it expects.

It returns a function that takes the remaining arguments.

有了柯里化以后，我们就能做到，所有函数都只接受一个参数。

        function add (x,y) {
            return x + y;
        }
        
        function add (x) {
            return function (y) {
                return x + y;
            };
        }
