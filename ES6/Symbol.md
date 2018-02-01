## Symbols

ES6引入了一种新的原始数据类型`Symbol`,表示独一无二的值。

它是JavaScript语言的第七种数据类型。

With ES6, for the first time in quite a while, a new primitive type has been added to JavaScript: the `symbol`.

Unlike the other primitive types, symbols don't have a literal form.
    
        var sym = Symbol("some optional description");
        
        typeof sym;         // "symbol"

Some things to note:
- You cannot and should not use `new` with `Symbol(..)`. It's not a constructor,nor are you producing an object.

- The parameter passed to `Symbol(..)` is optional. If passed, it should be a string that gives a friendly description for the symbol's purpose.

- The `typeof` output is a new value ( "symbol" ) that is the primary way to identify a symbol.

The description, if provided, is solely used for the stringification representation of the symbol:

        sym.toString();            //  "Symbol(some optional description)"

The internal value of a symbol itself -- referred 

The main point of a symbol is to create

参数相同的Symbol函数的返回值是不相等的。

    var s1 = Symbol();
    var s2 = Symbol();
    
    s1 // Symbol()
    
    s1 === s2 // false
    
##### 作为属性名的Symbol

由于每一个Symbol值都是不相等的，

    //以下三种方法的结果是相同的
    let mySymbol = Symbol();
    
    let a = {};
    a[mySymbol] = 'Hello';
    
    let a = {
      [mySymbol]:'Hello'
    };
    
    let a = {};
    Object.defineProperty(a, mySymbol, { value: 'Hello' }};
    
Symbol值作为对象属性名时，不能用点运算符。

#### 属性名的遍历

Symbol作为属性名使用时，

Similar to how primitive 

The main point of a symbol is to create

The specification uses the `@@` prefix notation to refer to the built-in symbols,the most common ones being: `@@iterator`,