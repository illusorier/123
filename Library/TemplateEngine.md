思考这样一个问题：假如不使用Angular这样的框架，我们要如何进行前端开发，如何开发一个较大型的网站。

可以把模板引擎理解为一个函数，下面的函数就是一个模板引擎：

        function greeting(data) {
            return `Hello, my name is ${data.name}`;
        }
        
        // ajax calls   
        var data = {
            name: 'bill'
        };
        
        someNode.innerHTML = greeing(data);
        
模板+数据 => 实际的HTML

当然模板引擎也可以输出任意格式的文本，如Text, XML, Markdown等等。

Nunjucks是Mozilla开发的一个纯JavaScript编写的模板引擎。

Available in node and all modern web browsers.

### Variable

A variable looks up a value from the template context.

        {{ username }}
        