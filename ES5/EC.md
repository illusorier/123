What is actually happening when code is executed/functions are invoked?

## Execution Contexts

执行上下文

> Execution context (EC) is the abstract concept of the environment in which the current code is being evaluated in.

Typically, this "environment" is either: (1) the default **global** environment or (2) the **function** environment

代码执行时所处的环境

可执行的代码可以被分为两类：全局代码和函数代码，分别对应两种不同的执行上下文。

When the JavaScript interpreter "compiles" 

从数据结构的角度理解，执行上下文们本身是一个栈（只能在一端进行插入和删除运算）。

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
          
          function a() {}
          
          var a = 'inner';
          
          console.log(a);
      }
      
      f('outer');

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
- properties-indexes which values are the values of function's arguments.

    

> In ES5 the concept of activation object is also replaced with common and single model of lexical environment.

#### Phases of processing the context code

Processing of the execution context code is divided on two basic stages:

1. Entering the execution context;
2. Code execution

Modifications of the variable are closely related with these two phases.

Notice, that processing of these two stage are the general behavior and independent from the type of the context.

#### Entering the execution context

On entering the execution context (but before the code execution), VO is filled with the following properties:

- for each *formal parameter* of a function (if we are in function execution context), a property of the variable object with a name and a value of formal parameter is created; for not passed parameters - property of VO with a name of formal parameter and value undefined is created;

- for each *function declaration* (FunctionDeclaration,FD), a property of the variable object with a name and a value of a function-object is created; if the variable object already contains a property with the same name, replace its value and attributes.

- for each *variable declaration*, a property of the variable object with a name and a value undefined is created; if the variable name is the same as name of already declared formal parameter or a function, the variable declaration does not disturb the existing property.

在代码执行之前，函数声明的优先级是最高的，其次是函数的参数（若在函数上下文中），最后是声明的变量。

也就是说假如变量与函数同名，在该变量声明语句执行之前，该标识符指向同名函数。

我们再来看看下面几个例子：

    function f(a) {
      console.log(a);
      
      var a = 'inner';
      
      console.log(a);
    }
    
    f('outer');


    function f(a) {
        console.log(b);
        
        var b = 'inner';
        
        console.log(a);
      }
      
      f('outer');



The official ES5 docs defines Lexical Environment 

该定义说明了标识符的解析是由该标识符定义的位置，而非调用的位置决定。

During the microseconds before JavaScript code is ever executed, three things happen during the creation phase:

1.The **ThisBinding** State Component is determined.

2.The **LexicalEnvironment** State Component is defined.

The `LexicalEnvironment` is where "identifier resolution" happens.

Within Lexical Environment are two components: (1) the environment record and (2) a reference to the outer environment.

Strictly speaking, **lexical environments** in this case are just more theoretically 
 
 
      