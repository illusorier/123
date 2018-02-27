## Arrow Functions

箭头函数

Two factors influenced the introduction of arrow functions: shorter functions and non-binding of `this`.

在某些特殊情况下，参数左右的圆括号和函数体左右的花括号都可以省略。

An *arrow function expression* has a shorter syntax than a *function expression* and does not have its own *this*, *arguments*, *super*, or *new.target*.

        function foo(x,y) {
            return x + y;
        }
    
        var foo = (x,y) => x + y;
    
The arrow function definition consists of a parameter list (of zero or more parameters,and surrounding `(...)`), followed by the `=>` market, followed by a function body.

The body only needs to be enclosed by `{...}` if there's more than one expression,or if the body consists of a non-expression statement.

Arrow functions are *always* function expressions; there is no arrow function declaration.

It also should be clear that they are anonymous function expressions.

Arrow functions have a nice, shorter syntax.

#### Not Just Shorter Syntax, But `this`

Until arrow functions, every new function defined its own `this` value

        function Person() {
            // The Person()
            this.age = 0;
        }
        
        var p = new Person();
        
In ECMAScript 3/5, the `this` issue was fixable by assigning the value in `this` to a variable that could be closed over.

下面这个例子是在Vue中使用clipboard.js

        new Vue({
            data: {
                count: 0
            },
            methods: {
                add: function() {
                    clipboard.on('success', function(e) {
                        // 指向的并不是Vue中的count
                        this.count ++;
                    });
                }
            }
        })