在ECMAScript中，有两种方式创建一个函数：函数声明语句或者函数表达式。

        function foo() {}
        
        var foo = function () {};
        
无论你选择哪种方式

What you end up with is an identifier for a function, that you can invoke by putting () after it, like `foo()`.


所谓的IIFE其实就是用函数表达式的方式创建一个匿名函数，并立即调用它。

下面这段代码的执行结果是什么？

        var a = 1;
        
        (function(a){
            console.log(a);
        })();

如何修改能使得输出结果为1？

        var a = 1;
                
        (function(a){
            console.log(a);
        })(a);
        
是不是可以这么理解：第一个a是形参，第二个a是实参？

An immediately-invoked function expression is a JavaScript programming language idiom which produces a lexical scope using JavaScript's function scoping.

The heart of the matter 

var foo = function(){...}

Because a function defined like so can be invoked by putting () after the function name,like foo(), and 

function(){...}() => SyntaxError:Unexpected token (

When the parser encounters the function keyword in the global scope or inside a function,it treats it as a function declaration(statement),and not as a function expression,by default.

If you don't explicitly tell the parser to expect an expression,it sees 



那么该如何解决这个问题呢？
Fortunately,the SyntaxError "fix" is simple.The most widely accepted way to tell the parser to expect a function expression is just to wrap it in parens,because in JavaScript,parens can't contain statements.
At this point,when 