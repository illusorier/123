Express是什么？

Express - Node.js web application framework

最早接触到express是在学习node.js时，当时尝试在本地架设HTTP服务器。

使用express的第一步是创建一个express应用程序。

The **express()** function is a top-level function exported by the **express** module.

    var express = require('express`);
    var app = express();
    
路由，中间件，错误处理是express应用程序的三个核心内容。
    

## Routing

Routing refers to determining how an application responds to a client request to a particular endpoint, which is a URI and a specific HTTP request method(GET,POST,and so on).

Each route can have one or more handler function, which are executed when the route is matched.

Route definition takes the following structure:

    app.METHOD(PATH, HANDLER)
    
Where:

- app is an instance of express.
- METHOD is an HTTP request method, in lowercase.
- PATH is a path on the server.
- HANDLER is the function executed when the route is matched.



There is a special routing method, **app.all()**, which is not derived from any HTTP method. This method is used

A route method is derived from one of the HTTP methods, and is attached to an instance of the **express** class.



#### Route parameters

Route parameters 

##### app.get(path, callback [,callback...])

Routes HTTP GET requests to the specified path with the specified callback function.


## middleware

Express is a routing and middleware web framework.

An Express application is essentially a series of middleware function calls.

**Middleware** functions are functions that have access to the request object (req), the response object (res), and the **next** function in the application's 

If the current middleware function does not end the request-response cycle, it must call next() to pass control to the next middleware function.

An Express application can use the following types of middleware:

- Application-level middleware
- Router-level middleware
- Error-handling middleware
- Built-in middleware
- Third-party middleware

#### Application-level middleware

This example shows a middleware function with no mount path. The function is executed every time the app receives a request.

    var app = express()
    
    app.use( function (req, res, next) {
      console.log('Time:', Data.now())
      next()
    })

#### Router-level middleware

Router-level middleware works in the same way as application-level middleware, except it is bound to an instance of **express.Router()**.

#### Built-in middleware

The only built-in middleware function in Express is **express.static()**

#### express()

Creates an Express application. The **express()** function is a top-level function exported by the **express** module.

The app object conventionally denotes the Express application.

    var express = require('express')
    var app = express()

#### app.listen

#### res.send([body])

Sends the HTTP response.

The body parameter can be a Buffer object, a String, an object, or an Array.

    res.send

#### res.sendFile

    res.sendFile(path [,options] [,fn])
    
Transfers the file at the given path.

### Request

The **req** object represents 