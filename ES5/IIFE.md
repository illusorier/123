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