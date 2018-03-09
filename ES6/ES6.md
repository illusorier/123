### Block-Scoped Declarations

The fundamental unit of variable scoping in JavaScript has always been the `function`.

If you needed to create a block of scope, the most prevalent way to do so other than a regular function declaration was the IIFE.

        var a = 1;
        
        (function(){
            var a = 2;
            console.log(a);
        })();
        
        console.log(a);
            
在ES6之前，JavaScript没有块级作用域的概念

    var count = 3;
    
    for (var i=0; i < count; i++){}
    
    console.log(i);
    
Now we can create declarations that are bound to any block, called *block scoping*.

This means all we need is a pair of `{...}` to create a scope.

Instead of using `var`,which always declares variable attached to the enclosing function (or global, if top level) scope,use `let`.
    
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

## Spread/Rest

ES6 introduces a new `...` operator that is typically referred to as the *spread* or *rest* operator.

        function foo(x,y,z){
            console.log( x, y, z );
        }
        
        foo( ...[1,2,3] );        // 1 2 3
    
When `...` is used in front of an array (actually, any *iterable*), it acts to "spread" it out into its individual values.

Spreading out an array as a set of arguments to a function call.

`...` acts to give us a simply syntactic replacement for the `apply(..)` method, which we would typically have used pre-ES6 as:

        foo.apply( null, [1,2,3] );	

But `...` can be used to spread out/expand a value in other contexts as well,

The other common usage of `...` can be seen as essentially the opposite;

## Destructuring

解构赋值

ES6 introduces a new syntactic feature called destructuring, which may be a little less confusing if you instead think of it as *structured assignment*.

ES6允许按照一定模式，从数组和对象中提取值，对变量赋值。

以前，为变量赋值，只能直接指定值。

        let a = 1;
        let b = 2;
        let c = 3;
        
ES6允许写成下面这样：

        let [a, b, c] = [1, 2, 3];

本质上，这种写法属于“模式匹配”，只要等号两边的模式相同,左边的变量就会被赋予对应的值。

        let [ , , third] = ["foo", "bar", "baz"];
        third // "baz"
        
        let [x, , y] = [1, 2, 3];
        x // 1
        y // 3

如果解构不成功，变量的值等于`undefined`。

另一种情况是不完全解构，即等号左边的模式，只匹配一部分的等号右边的数组。

如果等号的右边不是数组（或者严格地说，不是可遍历结构），那么将会报错。

解构不仅可以用于数组，还可以用于对象。

        let { foo, bar } = { foo: "aaa", bar: "bbb" };
        
        foo // "aaa"
        bar // "bbb"

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