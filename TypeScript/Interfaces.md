# Interfaces

One of TypeScript's core principles is that type-checking focuses on the *shape* that values have.

TS中接口的概念与Java中也有所不同：Java中的接口是用来修饰类的；而TS中的接口还可以用来修饰对象。

假如我们有一个函数，而这个函数的某个参数是对象，我们希望能描述这个对象的形状，该如何做？

        function printLabel(labelledObj: {label:string}) {
            console.log(labelledObj.label);
        }
        
        let myObj = {size: 10, label: "Size 10 Object"};
        printLabel(myObj);
        
我们也可以用interface来实现相同的功能：

        interface LabelledValue {
            label: string;
        }
        
        function printLabel(labelledObj: LabelledValue {
            console.log(labelledObj.label);
        }
        
        let myObj = {size: 10, label: "Size 10 Object"};
        printLabel(myObj);
        
在Java中也有相似的场景：
        
The type-checker checks the call to printLabel.

The printLabel function has a single parameter which requires that the object passed in has a property called label of type string.

### Function Types

可以使用接口的方式来定义一个函数需要符合的形状

In addition to describing an object with properties, interfaces are also capable of describing function types.

To describe a function type with an interface, we give the interface a call signature.

This is like a function declaration with only the parameter list and return type given.

        interface SearchFunc {
            (source: string, subString: string): boolean;
        }
        
        let mySearch: SearchFunc;
        mySearch = function(source: string, subString: string) {
            let result = source.search(subString);
            return result > -1;
        }
        
当然也可以使用含有泛型的接口来定义函数的形状：



### Class Types

One of the most common uses of interfaces in languages like C# and Java, that of explicitly enforcing that a class meets a particular contract, is also possible TypeScript.

        interface ClockInterface {
            currentTime: Date;
        }
        
        class Clock implements ClockInterface {
            currentTime: Date;
            constructor(h: number, m: number) {}
        }

You can also describe methods in an interface that are implemented in the class.

