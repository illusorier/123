# Basic Types

Type annotations in TypeScript are lightweight ways to record the intended contract of the function or variable.

    let isDone: boolean = false;
    let color: string = 'blue';
    let decimal: number = 6;
    
As in JavaScript,all numbers in TypeScript are floating point values.

    let list: number[] = [1, 2, 3];
    let list: Array<number> = [1, 2, 3];
    
We may need to describe the type of variables that we do not know when we are writing an application.
    
# Interfaces

One of TypeScript's core principles is that type-checking focuses on the *shape* that values have.

In TypeScript,interfaces fill the role of naming these types.

    interface LabelledValue {
      label: string
    }
    
    function printLabel(labelledObj: LabelledValue) {
      console.log(labelledObj);
    }
    
    let myObj = {size: 10, label: "Size 10 Object");
    
#### Optional Properties
Not all properties of an interface may be required.Some exists under

# Functions
To begin,just as in JavaScript,TypeScript functions can be created both as a named function or as an anonymous function.

#### Function Types

    function add(x: number, y: number): number {
        return x + y;
    }
    
    let myAdd = function(x: number, y: number): number { return x+y; };
    
A function's type has the same two parts: the type of arguments 

# Generics

In languages like C# and Java,one of the main tools in the toolbox for creating reusable components is *generics*,

    function identity(arg: any): any {
      return arg;
    }

While using `any` is certainly generic in that will accept any and all types of `arg`,we actually are losing


# Classes
Traditional JavaScript uses functions and prototype-based inheritance to build up reusable components.

    class Greeter {
      greeting: string;

# Decorators

A *Decorator* is a special kind of declaration that can be attached to

Decorators use the form `@expression`, where `expression` must evaluate to a function that will be called at runtime with information about the decorated declaration.

#### Class Decorators

A *Class Decorator* is declared just before a class declaration.

The class decorator is applied to the constructor of the class and




