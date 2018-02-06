## Scope

ECMAScript的变量是松散类型的，所谓松散类型就是可以用来保存任何类型的数据。

换句话说，每个变量仅仅是一个用于保存值的占位符而已。

定义变量时要使用var操作符

    function test () {
        var message = "hi"; // 局部变量
    }
    
用var操作符定义的变量将成为定义该变量的作用域中的局部变量。

当函数被调用时，就会创建该变量并为其赋值。而在此之后，这个变量又会被销毁。

    function test () {
        message = "hi"; // 全局变量
    }

One of the most fundamental paradigms of nearly all programming languages is the ability to store values in variables, and later retrieve or modify those values.

Without such a concept, a program could perform some tasks, but they would be extremely limited.

为什么会有作用域这个概念？

But the inclusion of variables into our program begets the most interesting questions we will now address:

Where do those variables live?

In other words, where are they stored?

How does our program find them when it needs them?

These questions speak to the need for a well-defined set of rules for storing variables in some location, and for finding those variables at a later time. 

**Scope** is a set of rules that govern how the *Engine* can look up a variable by its identifier name and find it, either in the current *Scope*, or in any of the *Nested Scopes* it's contained within.

函数的作用域是由该函数定义的位置决定还是调用的位置？

## Functions As Scopes

We have seen that 

## Scope From Functions

JavaScript没有块级作用域，在其他类C的语言中，由花括号封闭的代码块都有自己的作用域(执行环境)。

JavaScript has function-based scope.

No other structures create their own scope.

## Blocks As Scopes

While functions are the most common unit of scope, and certainly the most wide-spread of the design approaches in the majority of JS in circulation.

Other units of scope are possible, and the usage of these other scope units can lead to even better, cleaner to maintain code.

Many languages other than JavaScript support Block Scope.

在下面这段代码中，由于JS不支持块级作用域，变量i以及循环当中的变量所存在的作用域为enclosing scope (function or global).

        for (var i=0; i<10; i++) {
        	console.log( i );
        }
        
Why pollute the entire scope of a function with the `i` variable that is only going to be used for the for-loop?

那么这个问题目前有哪些解决方案？

The `let` keyword attaches the variable declaration