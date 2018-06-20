继"面向对象编程"之后，"函数式编程"是否会成为下一个编程语言的主流范式？

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

