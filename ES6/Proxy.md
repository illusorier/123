One of the most obviously meta programming features added to ES6 is the `Proxy` feature.

ES6原生提供Proxy构造函数，用来生成Proxy实例。

        var proxy = new Proxy(target, handler);
        
`get`方法用于拦截