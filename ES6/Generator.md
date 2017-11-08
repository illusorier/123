## Generators

通过Generators，我们可以在JS这样的单线程语言中实现协程这样的概念。

An expectation that JS developers almost universally rely on in their code: once a function starts executing, it runs until it completes, and no other code can interrupt and run in between.

All functions run to completion.In other words, once a function starts running, it finishes before anything else can interrupt.

As of ES6, a new form of function is being introduced, called a generator.

A generator can pause itself in mid-execution, and can be resumed either right away or at a later time.

Moreover,each pause/resume cycle in mid-execution is an opportunity for two-way message passing,where the generator can return a value,and the controlling code that resumes it can send a value back in.

#### Syntax

The generator function is declared with this new syntax:

        function *foo() {}
    
The position of the `*` is not functionally relevant.
    
There's a concise generator form in object literals:

        var a = {
          *foo() { .. }
        }
   
##### Executing a Generator

Though a generator is declared with `*`, you still execute it like a normal function:

        foo();
    
You can still pass it arguments:

        function *foo(x,y) {
          // ..
        }
        
        foo( 5, 10 );
    
The major difference is that executing a generator, like `foo(5,10)` does not actually run the code in the generator.

Instead, it produces an iterator that will control the generator to execute its code.

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