# Interfaces

TS中接口的概念与Java中也有所不同：Java中的接口是用来修饰类的；而TS中的接口还可以用来修饰对象。

假如我们有一个函数，而这个函数的某个参数是对象，我们希望能描述这个对象的形状，该如何做？

        function printLabel(labelledObj: {label:string}) {
            console.log(labelledObj.label);
        }
        
        let myObj = {size: 10, label: "Size 10 Object"};
        printLabel(myObj);
        
The type-checker checks the call to printLabel.

The printLabel function has a single parameter which requires that the object passed in has a property called label of type string.

### Class Types

One of the most common uses of interfaces in languages like C# and Java, that of explicitly enforcing that a class meets a particular contract, is also possible TypeScript.

        interface ClockInterface {
            currentTime: Date;
        }

You can also describe methods in an interface that are implemented in the class 

