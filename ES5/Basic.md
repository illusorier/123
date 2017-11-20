# Into Programming

## Code
A program,often referred to as *source code* or just *code*,is a set of special instructions to tell the computer what tasks to perform.

### Statements

In a computer language, a group of words, numbers, and operators that perform a specific task is a *statement*.

Programs are just collections of many statements.

## Expressions

什么是表达式？

Statements are made up of one or more *expressions*.

An expression is any reference to a variable or value,　or a set of variable(s) and value(s) combined with operators.

        a = b * 2;

This statement has four expressions in it:
- `2` is a *literal value expression*
- `b` is a *variable expression*,which means to retrieve its current value.
- `b * 2` is a *arithmetic expression*,　which means to do the multiplication.
- `a = b * 2` is an *assignment expression*.

> An *expression* is any valid unit of code that resolves to a value.

函数调用是不是表达式?

有两种类型的表达式

### Operators

JavaScript has both binary and unary operators,and one special ternary operator. A binary operator requires two operands,one before the operator and one after the operator:

    operand1 operator operand2
    
#### Assignment operators

An assignment operator assigns a value to its left operand based on the value of its right operand.

#### delete

The delete operator removes a property from an object.

    delete expression
    


Operators are how we perform actions on variables and values.

The `++` increment operator and the `--` decrement operator are both unary operators,which can be used in either a postfix position or prefix position.

#### Increment (++)

The increment operator increments (adds one to) its operand and returns a value.

- If used postfix,with operator after operand (x++) ,then it returns the value before incrementing.

#### Operator Precedence

What rules govern how the operators are processed when there's more than one present in an expression.



# Values & Types


#### Arrays

Because arrays are special objects(as `typeof` implies),they can also have properties,including the automatically updated `length` property.

#### Functions

The other `object` subtype you'll use all over your JS program is a function:

`typeof` returns `"function"`,which implies that a `function` is a main type -- and can thus have properties,but you typically will only use function object properties in limited cases.

#### Built-In Type Methods


## Natives

Natives are actually built-in functions.

- `String()`
- `Number()`
- `Boolean()`
- `Array()`
- `Object()`
- `Function()`
- `RegExp()`
- `Date()`
- `Error()`
- `Symbol()`


    var s = new String( "Hello World!" );
    
    typeof s; // "object"
    
    s instanceof String // true
    
    s.toString(); // "Hello World!"
    
    Object.prototype.toString.call(s);  // "[object String]"

##### String.prototype.toString()

The String object overrides the toString() method of the `Object` object;it does not inherit `Object.prototype.toString()`.For `String` objects,the toString() method returns a string representation of the object and is the same as the `String.prototype.valueOf()` method.

##### Using toString() to detect object class

#### Boxing Wrappers

These object wrappers serve a very important purpose.

Primitive values don't have properties or methods,so to access `.length` or `.toString()` you need an object wrapper around the value.Thankfully,JS will automatically box (aka wrap) the primitive value to fulfill such accesses.

## Functions

To break up the code's tasks into reusable pieces,instead of repeating yourself, defining a `function`.

A function is

要检测一个变量是不是基本数据类型，可以

## Strict Mode
ES5 added a "strict mode" to the language,



String.prototype.toUpperCase()

The **toUpperCase** method returns the calling string value converted to upper case.

## Error

The **Error** constructor creates an error object. Instances of Error objects are throw when runtime errors occur.

console.error(): Outputs an error message to the Web Console.

### Error types

#### ReferenceError

The **ReferenceError** object represents an error when a non-existent variable is referenced.

## Exception handling statements

You can throw exceptions using the **throw** statement and handle them using the **try...catch** statements.

### Exception types

- ECMAScript exceptions
- DOMException and DOMError

## Statements & declarations

### throw

The **throw statement** throws a user-defined exception.

Execution of the current function will stop (the statements after throw won't be executed),and control will be passed to the first **catch** block in the call stack.If no catch block exists among caller functions,the program will terminate.

    throw expression;
    
    throw 'Error';
    throw 42;
    throw true;
    
### try...catch

The **try..catch** statement marks a block of statements to try,and specifies a response,should an exception be thrown.

### break

The **break statement** terminates the current loop,`switch`, or `label` statement and transfers program control to the statement following the terminated statement.