## 变量

在日常的JS编程过程中，我们经常会在某些地方写一些变量和函数，然后在另一些地方读取、修改或者调用它们。

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
    


One of the most fundamental paradigms of nearly all programming languages is the ability to store values in variables,and later retrieve or 

Where do those variables live?

## Compiler Theory

JavaScript is a compiled language.

In traditional compiled-language process,a chunk of source code,your program,will undergo typically three steps before it is executed,roughly called "compilation".

1. **Tokenizing/Lexing**:breaking up a string of characters into meaningful(to the language) chunks,called tokens.
2. **Parsing**:taking a stream(array) of tokens and turning it into a tree of nested elements,which collectively represent the 
3. **Code-Generation**

JavaScript engines don't get the luxury(like other language compiler) of having 

## Lexical Scope

"Scope" is a set of rules that govern how the Engine can look up

Lexical scope is scope that is defined at lexing time.

## Function vs. Block Scope

Scope consists of a series of "bubbles" that each act as a container or bucket,

## Scope From Functions

JavaScript没有块级作用域，在其他类C的语言中，由花括号封闭的代码块都有自己的作用域(执行环境)。

JavaScript has function-based scope.

No other structures create their own scope bubbles.



## Blocks As Scopes