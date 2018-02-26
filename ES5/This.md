## This value

`this` 是JavaScript中十分令人困惑的概念，因为在不同的环境下，它指向的值是不一样的。

One of the most confused mechanisms in JavaScript is the `this` keyword.

It's a special identifier keyword that's automatically defined in the scope of every function.

If the `this` mechanism is so confusing,even to seasoned JavaScript developers, one may wonder why it's even useful?

既然this这个概念这么令人困惑，那么我们为什么依旧需要它：

The motivation and utility of `this`:

        function identify() {
          return this.name.toUpperCase();
        }
          
        function speak() {
          var greeting = "Hello, I'm " + identify.call( this );
          console.log( greeting );
        }
        
        var me = {
          name: "Kyle"
        };
        
        var you = {
          name: "Reader"
        };
        
        identify.call( me );
        identify.call( you );
        
        speak.call( me );
        speak.call( you );
        
我们知道，代码（函数）有其相应的执行上下文。

如果某个函数的执行，依赖于某个对象中包含的数据；那么，除了显式得将该对象作为参数传入函数，是否还有其他解决方法？

利用作用域链：可以将这些数据作为局部变量声明在函数调用的上下文中，但这显然会造成很多问题。
    
This code snippet allows the `identify()` and `speak()` functions to be re-used against multiple context (`me` and `you`) objects.

Instead of relying on `this`, you could have explicitly passed in a context object to both `identify()` and `speak()`.

        function identify(context) {
        	return context.name.toUpperCase();
        }
        
        function speak(context) {
        	var greeting = "Hello, I'm " + identify( context );
        	console.log( greeting );
        }
        
        identify( you ); 
        speak( me ); 

`this` mechanism provides a more elegant way of implicitly "passing along" an object reference, leading to cleaner API design and easier re-use.

The more complex your usage pattern is, the more clearly you'll see that passing context around as an explicit parameter is often messier than passing around a `this` context.

#### call vs apply

它们的作用是什么，有什么区别？

Calls a function with a given this value and arguments provided individually.

区别在于参数的格式

        fun.call(thisArg, arg1, arg2, ...)
        
        fun.apply(thisArg, [argsArray])

#### Call-site

We must inspect the call-site (the location in code where a function is called, not where it is declared) to answer the question: what's this `this` a reference to?

`this` is a binding made for each function invocation, based entirely on its call-site (how the function is called).

#### Default Binding

每个函数被调用时，其内部都有一个特殊的值，this，它指向一个对象。

The first rule we will examine comes from the most common case of function calls: standalone function invocation.

这种情况下，`this`指向全局对象

`this` points to the global object.

Applied when function called with a plain,un-decorated function reference.

If `strict mode` is in effect,`this` set to `undefined`.

#### Implicit Binding

Another rule to consider is: does the call-site have a context object, also referred to as an owning or containing object.

        function foo() {
        	console.log( this.a );
        }
        
        var obj = {
        	a: 2,
        	foo: foo
        };
        
        obj.foo(); // 2

Regardless of whether `foo()` is 

If so, the implicit binding rule says that it's that object which should be used for the function call's this binding.

##### Implicitly Lost

One of the most common frustrations that `this` binding creates is when an implicitly bound function loses that binding,which usually means it falls back to the default binding.


    function foo() {
      console.log( this.a );
    }
    
    var obj = {
      a: 2;
      foo:foo
    };
    
    var bar = obj.foo;
    
    var a = "oops, global";
    
    bar();
    
Even though
    
The more subtle,more common,and more unexpected way this occurs is when we consider passing a callback function:

    function foo() {
      console.log( this.a );
    }
    
    function doFoo(fn) {
      fn();
    }
    
    var obj = {
      a: 2,
      foo: foo
    }
    
    var a = "oops, global";
    
    doFoo( obj.foo );
    
    

#### Explicit Binding

If we want to force a function call to use a particular object for the `this` binding,without putting a property function reference on the object?

#### `new` binding

When a function is invoked with `new` in front of it,otherwise known as a constructor call,the following things are done automatically:

1. a brand new object is created(aka,constructed) out of thin air

this is a property of the execution context.It's a special object in which context a code is executed.

    activeExecutionContext = {
      VO:{...},
      this:thisValue
    };

A `this` value is a special object which is related with the execution context.Therefore,it may be named as a `context object`.

Any object can be used as `this` value of the context.

The `this` value is a property of the execution context, but not a property of the variable object.

The value is determined on entering the context and is immutable while the code is running in the context.

#### Binding Exceptions

##### Ignored `this`