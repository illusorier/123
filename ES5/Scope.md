## Scope

What is scope?

什么是作用域？

One of the most fundamental paradigms of nearly all programming languages is the ability to store values in variables, and later retrieve or modify those values.

变量是编程语言中最基础的概念之一。

我们为什么需要变量这个概念？

Without such a concept, a program could perform some tasks, but they would be extremely limited.

But the inclusion of variables into our program begets the most interesting questions we will now address:

Where do those variables live?

In other words, where are they stored?

当程序执行时，变量的值是如何resolved？

How does our program find them when it needs them?

These questions speak to the need for a well-defined set of rules for storing variables in some location, and for finding those variables at a later time. 

**Scope** is a set of rules that govern how the *Engine* can look up a variable by its identifier name and find it, either in the current *Scope*, or in any of the *Nested Scopes* it's contained within.

作用域、作用域链、执行上下文、词法环境等概念都与代码执行时，标识符的解析有关。

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

`let`

The `let` keyword attaches the variable declaration to the scope of whatever 

### Dynamic Scope 

There are two predominant models for how scope works.

The first of these is by far the most common, used by the vast majority of programming languages which is **Lexical Scope**.

静态作用域

The other model, which is still used by some languages is called **Dynamic Scope**.

动态作用域

Lexical scope is the set of rules about how 

The key characteristic of lexical scope is that it is defined at author-time,

Dynamic scope actually is a near cousin to another mechanism (`this`) in JavaScript.

在动态作用域的机制下，一个函数执行时变量值的解析是由调用该函数的上下文环境决定的。

Dynamic scope do not concern itself with how and where functions and scopes are declared, but rather **where they are called from**.

### Scope Chain

作用域链这个概念产生的本质在于：能形成作用域的独立模块(如函数)的相互嵌套。

If to describe briefly and showing the main point, a scope chain is mostly related with inner functions.

As we know, ECMAScript allows creation of inner functions and we can even return these functions from parent functions.

The scope chain is exactly this list of all (parent) variable objects for the inner contexts.

This chain is used for variables lookup.

The scope chain of a function context is created at function call and consists of the AO and the internal [[Scope]] property of this function.

    activeExecutionContext = {
      VO: {...},
      this: thisValue,
      Scope: []
    };
    
where Scope by definition is:

    Scope = AO + [[Scope]]
    
Lexical environments 

倘若没有作用域这一概念，我们在编程过程中需要避免使用相同的标识符，否则会产生混乱。

Concept of a scope helps us to use in one program the same name variables but with 

Block and function concepts lead us to one of the major scope properties - to nest 

In static scoping, an identifier refers to its 

Today static scope is used in many languages:C, Java, ECMAScript, Python, Ruby, Lua, etc.

