AJAX

Asynchronous JavaScript + XML

这一技术能够向服务器请求额外的数据而无须刷新页面，能够带来更好的用户体验。

也就是说假如不利用AJAX这一技术，我们只能在浏览器第一次通过特定URL加载该网站页面时与服务器进行通讯。

Although X in Ajax stands for XML, JSON is used more than XML nowadays because of its many advantages such as being lighter and a part of JavaScript.

Both JSON and XML are used for packaging information in Ajax model.

The `XMLHttpRequest` API is the core of Ajax.

Use `XMLHTTPRequest` objects to interact with servers.

You can retrieve data from a URL 

To send an HTTP request, create an `XMLHttpRequest` object, open an URL, and send the request.

    let xhr = new XMLHttpRequest();
    
    xhr.open(httpMethod, url);
    xhr.send();

在使用XHR对象时，要调用的第一个方法是`open()`，它接受3个参数：要发送的请求的类型、请求的URL和表示是否异步发送请求的布尔值。

    XMLHttpRequest.open(method, url, async, user, password);

URL是相对于执行代码的当前页面(当然也可以使用绝对路径)，调用`open()`方法并不会真正发送请求。

After the transaction completes, the object will contain useful information such as the response body and the HTTP status of the result.     
    
A request made via `XMLHttpRequest` can fetch the data in one of two ways, asynchronously or synchronously.

The type of request is dictated by the optional **async** argument (the third argument) that is set on the `XMLHttpRequest.open()` method.
 
XMLHttpRequest有两种使用方式：同步或异步。

XMLHttpRequest provides the ability to listen to various events that can occur while the request is being processed.

The `load` event is fired when a resource and its dependant resources have finished loading.

Although `XMLHttpRequest` is most commonly used to send and receive textual data, it can be used to send and receive binary content.

Instances of `XMLHttpRequest` can be used to submit forms in two ways:

- using only AJAX
- using the `FormData` API

