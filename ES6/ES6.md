ES2015 (aka ES6)

ES2016 (aka ES7)
# Syntax

### Block-Scoped Declarations

The fundamental unit of variable scoping in JavaScript has always been the `function`.

If you needed to create a block of scope, the most prevalent

在ES6之前，JavaScript没有块级作用域的概念

    var count = 3;
    
    for (var i=0; i < count; i++){}
    
    console.log(i);
    
Now we can create declarations that are bound to any block,called *block scoping*.

This means all we need is a pair of `{...}` to create a scope.

Instead of using `var`,which always declares variable attached to the enclosing function(or global,if top level) scope,use `let`.
    
    var a = 2
    
    {
      let a = 3;
      console.log(a);
    }
    
    console.log(a);
    
You should always put the `let` declaration(s) at the very top of that block.

If you have more than one to declare, using just one `let`.

    {
      let a = 2, b, c;
    }
    
There's another experimental (not standardized) form of the `let` declaration called the `let` - block, which looks like:

    let (a = 2, b, c) {
      // ..
    }
    
That form is what i call explicit block scoping.


`let` + `for`



###Spread/Rest

ES6 introduces a new `...` operator that's typically 

    function foo(x,y,z){
        console.log( x, y, z );
    }
    
    foo( ...[1,2,3] );        // 1 2 3
    
When `...` is used in front of an array, it acts to "spread" it out into its individual values.

Spreading out an array as a set of arguments to a function call.

`...` acts to give us a simply syntactic

But `...` can be used to spread out/expand a value in other contexts as well,

### Destructuring

ES6 introduces a new syntactic feature called destructuring,which may be a little less confusing if you instead think of it as *structured assignment*.

### Object Literal Extensions

ES6 adds a number of important convenience extension to the humble `{ .. }` object literal.

#### Concise Properties

    var x = 2,
        y = 3,
        o = {
          x,
          y
        };

##### Concise Methods

While `f() {..}` seems to just be shorthand for `f: function(){..}`, concise methods have special behaviors that their older counterparts don't;specifically, the allowance for `super`.

Generators also have a concise method form:

    var o = {
      *foo() { .. }
    };

##### ES5 Getter/Setter

### Arrow Functions

    function foo(x,y) {
      return x + y;
    }
    
    var foo = (x,y) => x + y;
    
The arrow function definition consists of a parameter list(of zero or more parameters,and surrounding `(...)`), followed by the `=>` market,followed by a function body.

The body only needs to be enclosed by `{...}` if there's more than one expression,or if the body consists of a non-expression statement.

Arrow functions are *always* function expressions;there is no arrow function declaration.

It also should be clear that they are anonymous function expressions.

Arrow functions have a nice, shorter syntax.

#### Not Just Shorter Syntax, But `this`

    var 
    
Herein we finally can see the primary design char

### Symbols
With ES6,for the first time in quite a while,a new primitive type has been added to JavaScript:the `symbol`.Unlike the other primitive types,symbols don't have a literal form.
    
    var sym = Symbol("some optional description");
    
    typeof sym;         // "symbol"

Symbol值通过`Symbol`函数生成。

Some things to note:
- You cannot and should not use `new` with `Symbol(..)`.It's not a constructor,nor are you producing an object.
- The parameter passed to `Symbol(..)` is optional.If passed,it should be a string that gives a friendly description for the symbol's purpose.

The internal value of a symbol itself --

The main point of a symbol is to create

参数相同的Symbol函数的返回值是不相等的。

    var s1 = Symbol();
    var s2 = Symbol();
    
    s1 // Symbol()
    
    s1 === s2 // false
    
##### 作为属性名的Symbol

    //以下三种方法的结果是相同的
    var mySymbol = Symbol();
    
    var a = {};
    a[mySymbol] = 'Hello';
    
    a = {
      [mySymbol]:'Hello'
    };
    
    var a = {};
    Object.defineProperty(a, mySymbol, { value: 'Hello' }};
    
Symbol值作为属性名时，不能用点运算符访问该对象相应属性。

#### 属性名的遍历

Symbol作为属性名使用时，

Similar to how primitive 

The main point of a symbol is to create

The specification uses the `@@` prefix notation to refer to the built-in symbols,the most common ones being: `@@iterator`,

### `for..of` Loops

Joining the `for` and `for..in` loops from the JavaScript we're familiar with,ES6 adds a `for..of` loop,which loops over the set of values produced by an iterator.

The value you loop over

An iterable is simply an object that is able to produce an iterator,which the loop then uses.

##### `for...in`

`for...in`遍历的是对象的属性，而不是值。

The **for...in statement** iterates over the enumerable properties of an object,in original insertion order.For each distinct property,statements can be executed.

    for (variable in object) {
      // ...
    }
    
**variable**: A different property name is assigned to *variable* on each iteration.

**object**: Object whose enumerable properties are iterated.

The loop will iterate over all enumerable properties of the object itself and those the objects inherits from its constructor's prototype.

##### Iterating over own properties only

If you only want to consider properties attached to the object itself,and not its prototypes,

##### Object.getOwnPropertyNames()




##### Object.keys()

The `Object.keys()` method returns an array of a given object's own enumerable properties,in the same order as that provided by a `for...in` loop(the difference being that a for-in loop enumerates properties in the prototype chain as well).

### Generators

An expectation that JS developers almost universally rely on  in their code: once a function starts executing,it runs until it completes,and no other code can interrupt and run in between.

All functions run to completion.In other words,once a function starts running,it finishes before anything else can interrupt.

As of ES6,a new form of function is being introduced,called a generator.

A generator can pause itself in mid-execution,and can be resumed either right away or at a later time.

Moreover,each pause/resume cycle in mid-execution is an opportunity for two-way message passing,where the generator can return a value,and the controlling code that resumes it can send a value back in.

##### Syntax
The generator function is declared with this new syntax:

    function *foo() {}
    
The position of the `*` is not functionally relevant.
    
There's a concise generator form in object literals:

    var a = {
      *foo() { .. }
    }
   
##### Executing a Generator

Though a generator is declared with `*`,you still execute it like a normal function:

    foo()
    
You can still pass it arguments:

    function *foo(x,y) {
      // ..
    }
    
    foo( 5, 10 );
    
The major difference is that executing a generator,like `foo(5,10)` doesn't actually run the code in the generator.

Instead,it produces an iterator that will control the generator to execute its code.

##### `yield`

Generators also have a new keyword you can use inside them,to signal the pause point: `yield`.

    function *foo() {
      var x = 10;
      var y = 20;
      
      yield;
      
      var z = x + y;
    }
    
`yield` can appear any number of times(or not at all,technically!) in a generator.

`yield` is not just a pause point.It's an expression that sends out a value when pausing the generator.

    function *foo() {
      while (true) {
        yield Math.random();
      }
    }
    
The `yield` expression not only sends a value -- `yield` without a value is the same as `yield undefined` -- but also receives (e.g., is replaced by) the eventual resumption value.
    
A `yield..` expression can appear anywhere a normal expression can.

    function *foo() {
      var arr = [ yield 1, yield 2, yield 3 ];
      console.log( arr, yield 4 );
    }

`yield` is not technically an operator,because it can be used all by itself as in `var x = yield`,thinking of it as an operator can sometimes be confusing.

`yield *`
In the same way that the `*` makes a `function` declaration into `function*` generator declaration,a `*` makes `yield` into `yield*`,which is a very different mechanism,called *yield delegation*.

Grammatically,`yield *..` will behave the same as a `yield ..`, as discussed before.

`yield * ..` requires an iterable;it then invokes that iterable's iterator,and delegates its own host generator's to that iterator until it's exhausted.

#### Input and Output

A generator is still a function, which accepts arguments(input) and return a value(output).

    function *foo(x) {
      var y = x * (yield "Hello");
      return y;
    }
    
    var it = foo( 6 );
    
    // start `foo(..)`
    it.next();
    
    var res = it.next( 7 );
    
    res.value;

First,we pass in `6` as the parameter `x`.Then we call `it.next()`,and it starts up `*foo(..)`(advance from its current location).

The `yield` expression pauses `*foo(..)`(in the middle of the assignment statement), and essentially requests the calling code to provide a result value for the `yield` expression.

Next, we call `it.next( 7 )`, which is passing the `7` value back in to *be* the result of the paused `yield` expression

In general, you're going to have one more `next(..)` call than you have `yield` statements.

`yield ..` and `next(..)` pair together as a two-way message passing system **during the execution of the generator**.

We don't pass a value to the first `next()` call.

Only a paused `yield` could accept such a value.

The specification and all compliant browsers just silently discard anything passed to the first `next()`.

Always start a generator with an argument-free `next()`.

There's an extra `next()` compared to the number of `yield` statements. The final `it.next()` call is again asking

#### Multiple Iterators

Each time you construct an *iterator*, you are implicitly constructing an instance of the

#### Generator'ing Values

In the previous section, we mentioned an interesting use for generators, as a way to produce values.

An *iterator* is a well-defined interface for stepping through a series of values from a producer.

The JS interface for iterators, as it is in most languages, is to call `next()` each time you want the next value from the producer.

#### Iterating Generators Asynchronously


#### Iterator Control

#### Early Completion

#### Iterating Generators Asynchronously

    function ajax( url, function(err,data){
      if (err) {
        it.throw( err );
      }
      else {
        it.next( data )
      }
    }
    
    function *main() {
      try {
        var text = yield ajax( 11, 31 );
        console.log( text );
      }
      catch (err) {
        console.error( err );
      }
      
    var it = main();
    
    it.next();
    
In `yield ajax(11,31)`, first the `ajax(11,31)` call is made, which returns nothing (aka `undefined`)

That's a nearly perfect solution to our previously stated problem with callbacks not being able to express asynchrony in a sequential, synchronous fashion that our brains can relate to.
        

Generator函数是ES6提供的一种异步编程解决方案，语法行为与传统函数完全不同。

执行Generator函数会返回一个遍历器对象
 
### Modules

#### The Old Way

The traditional module pattern 

    function Hello(name) {
      function greeting() {
        console.log( "Hello " + name + "!");
      }
      
      // public API
      return {
        greeting: greeting
      };
    }
    
    var me = Hello( "Kyle" );
    me.greeting();
    
#### Moving Forward

As of ES6, we no longer need to rely on

##### CommonJS


    
#### The New Way

The two main new keywords that enable ES6 modules are `import` and `export`.

Both `import` and `export` must always appear in the top-level scope.

They must appear outside of all blocks and functions.

##### `export`ing API Members

The `export` keyword is either put in front of a declaration, or used as an operator with a special list of bindings to export.

    export function foo() {
      // ...
    }
    
    export var awesome = 42;
    
    var bar = [1,2,3];
    export { bar };
    
    export { foo, awesome, bar };
    
These are called *named export*,as you are in effect exporting the name bindings of the variables/functions/etc.

Anything you don't label with 

You can also "rename" (aka alias) a module member during named export:

    function foo() { .. }
    
    export { foo as bar };
    
When this module is imported, only the `bar` member name is available to import.

Module exports are not just normal assignments of values
    
Though you can clearly use `export` multiple times inside a module's definition,ES6 definitely prefers the approach that a module has a single export,which is known as *default export*.

##### `import`ing API Members

If you want to import certain specific named members of a module's API into your top-level scope,you use this syntax:

    import { foo, bar, baz } from "foo";
    
The "foo" string is called a *module specifier*.

The `foo`,`bar`,and `baz` identifiers listed must match named exports on the module'API.
    

### Maps
Objects are the primary mechanism for creating unordered key/value-pair data structures.

The major drawback with object is the inability to use a non-string value as the key.

The only drawback is that you can't use the `[ ]` bracket syntax for setting and retrieving values.But `get(..)` and `set(..)` work perfectly suitably instead.

### Classes

`class`

At the heart of the new ES6 class mechanism is the `class` keyword,which identifies a block where the contents define the members of a function's prototype.

    class Foo {
      constructor(a,b) {
        this.x = a;
        this.y = b;
      }
      
      gimmeXY() {
        return this.x * this.y;
      }
    }

- `class Foo` implies creating a (special) function of the name

`extends` and `super`

ES6 classes also have syntactic sugar

    class Bar extends Foo {
      constructor(a,b,c) {
        super(a,b);
        this.z = c;
        
        
        
In the constructor, `super` automatically refer to the "parent constructor".In a method

### Decorator
