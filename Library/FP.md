继"面向对象编程"之后，"函数式编程"是否会成为下一个编程语言的主流范式？

我们为什么需要函数式编程？

Functional programming makes programs more testable and predictable and therefore leads to fewer bugs.

World's most popular functional programming language: JavaScript.

> A pure function is a function that, given the same input, will always return the same output and does not have any observable side effect.

### What is a function?

什么是函数？

A **function** is a process which takes some input, called **arguments**, and produces some output called a **return value**.

这是函数在编程当中的概念

Functions may serve the following purposes:

- Mapping: Produce some output based on given inputs. A function maps input values to output values. (这点和数学上很类似)

- Procedures: A function may be called 

- IO:

Pure function are all about mapping.

Good programmers give functions descriptive names so that when we see the code, we can see the function names and understand what function does.

You can call a function with fewer arguments than it expects.

It returns a function that takes the remaining arguments.

什么是柯里化？

有了柯里化以后，我们就能做到，所有函数都只接受一个参数。

      function add (x,y) {
          return x + y;
      }
      
      var sum = add(1, 2);
      
      function add (x) {
          return function (y) {
              return x + y;
          };
      }

      var curry = add(1);
      var sum = curry(2);
      
为什么需要柯里化？ 
      
Currying seems incredibly unnecessary at first mainly because we are illustrating it with an operation as simple as adding two numbers.

This technique is powerful because it gives us better control over our functions.

闭包是与函数式编程息息相关的一个概念

> A closure is the combination of a function and the lexical environment within which that function was declared.

*higher-order function* is a function that accepts another function as an argument.

This passed function is sometimes referred to as the *callback*.

The curried effect is achieved by binding some of the arguments to the first function invoke, so that those values are fixed for the next invocation.

下面是一个我们在讲解柯里化时常常用到的例子：