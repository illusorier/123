在进入ES5、ES6之后，这些概念发生了哪些变化？

## Execution Contexts

我认为执行上下文和作用域是两个相似的概念，都是为了描述变量或者说标识符的解析而存在的。

> Execution context (EC) is the abstract concept used by ECMA-262 specification for an executable code.

可执行的代码可以被分为两类：全局代码和函数代码，分别对应两种不同的执行上下文。

从数据结构的角度理解，执行上下文们本身是一个栈（只能在表的一端进行插入和删除运算）。

Set of active execution contexts forms a stack.

The bottom of this stack is always a global context, the top - a current(active) execution context.

所有被激活的执行上下文形成一个栈。

For examples, we define the stack of execution contexts as an array:

    ECStack = [];

The stack is modified ( pushed/popped ) during the entering and exiting various kinds of EC.

The stack is pushed every time on entering a function ( even if the function is called recursively or as the constructor), and also at built-in eval function work.

It is necessary to notice that the code of concrete function does not include codes of the inner functions.

## Variable Object

在全局作用域中执行下面这段代码的结果是什么？

        function f(a) {
            console.log(a);
            
            var a;
            
            function a() {}
        }
        
        f(1);

*A variable object(VO)* is a special object related with an execution context and which stores:

- variables (`var`,VariableDeclaration)
- function declarations
- function formal parameters

> In ES5, the concept of *variable object* is replaced with *lexical environments* model. 

It is possible to present variable object as a normal ECMAScript object:

    VO = {};

VO is a property of an execution context:

    activeExecutionContext = {
        VO: {
            // context data (var, FD, function arguments)
        }
    };

Indirect referencing VO is possible in global context.

For other contexts, it is purely mechanism of implementation.

### Variable object in different execution contexts

#### Variable object in global context

*Global object* is the object which is created before entering any execution context; this object exists in the single copy,its properties are accessible from any place of the program,the life cycle of the global object ends with program end.

At creation the global object is initialized with such properties as `Math`,`String`,`Date`,`parseInt` etc.,and also by additional

#### Variable object in function context

    VO(functionContext) === AO;
    
An activation object is created on entering the context of a function and initialized by property `argument` which value is the Argument object:

    AO = {
      arguments: <Arg0>
    };  
    
*Arguments* object is a property of the activation object.It contains the following properties:

- callee - the reference to the current function;
- length - quantity of *real passed* arguments;


#### Phases of processing the context code

Processing of the execution context code is divided on two basic stages:

1. Entering the execution context;
2. Code execution

Modifications of the variable are closely related with these two phases.

Notice, that processing of these two stage are the general behavior and independent from the type of the context.

#### Entering the execution context

On entering the execution context(but before the code execution), VO is filled with the following properties:

- for each *formal parameter* of a function (if we are in function execution context), a property of the variable object with a name and a value of formal parameter is created; for not passed parameters - property of VO with a name of formal parameter and value undefined is created;

- for each *function declaration* (FunctionDeclaration,FD), a property of the variable object with a name and a value of a function-object is created; if the variable object already contains a property with the same name, replace its value and attributes.

- for each *variable declaration*, a property of the variable object with a name and a value undefined is created; if the variable name is the same as name of already declared formal parameter or a function, the variable declaration does not disturb the existing property.

在代码执行之前，函数声明的优先级是最高的，其次是参数（若在函数上下文中），最后是变量。
      