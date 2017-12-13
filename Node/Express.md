Express是什么？

Express - Node.js web application framework

Use Express for the server framework.

最早接触到express是在学习node.js时，当时尝试在本地架设HTTP服务器。

使用express的第一步是创建一个express应用程序。

Creates an Express application.

The **express()** function is a top-level function exported by the **express** module.

    const express = require('express`);
    const app = express();
    
路由，中间件，错误处理是express应用程序的三个核心内容。

## middleware

Express is a routing and middleware web framework.

An Express application is essentially a series of middleware function calls.

**Middleware** functions are functions that have access to the request object (req), the response object (res), and the **next** function in the application's request-response cycle.

Middleware functions can perform the following tasks:

If the current middleware function does not end the request-response cycle, it must call next() to pass control to the next middleware function.

An Express application can use the following types of middleware:

- Application-level middleware
- Router-level middleware
- Error-handling middleware
- Built-in middleware
- Third-party middleware

### Application-level middleware

Bind application-level middleware to an instance of the **app object** 

This example shows a middleware function with no mount path. The function is executed every time the app receives a request.

        const app = express();
        
        app.use(function (req, res, next) {
            console.log('Time:', Data.now());
            next();
        });

### Router-level middleware

Router-level middleware works in the same way as application-level middleware, except it is bound to an instance of **express.Router()**.

        const express = require('express');
        const router = express.Router();
        
不要忘记这也是个中间件。

        app.use('/', router);

### Built-in middleware

Starting with version 4.x, Express no longer depends on Connect.

The middleware functions that were previously included with Express are now in separate modules.

Express has the following built-in middleware function:

#### express.static()


### Use a reverse proxy

A reverse proxy sits in front of a web app and performs supporting operations on the requests, 