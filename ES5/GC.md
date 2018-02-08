In order to not bother the programmer with allocations, JavaScript does it alongside with declaring values.

ECMAScript的变量是松散类型的，所谓松散类型就是可以用来保存任何类型的数据。

换句话说，每个变量仅仅是一个用于保存值的占位符而已。

定义变量时要使用var操作符

    function test () {
        var message = "hi"; // 局部变量
    }
    
用var操作符定义的变量将成为定义该变量的作用域中的局部变量。

当函数被调用时，就会创建该变量并为其赋值。而在此之后，这个变量又会被销毁。

    function test () {
        message = "hi"; // 全局变量
    }
