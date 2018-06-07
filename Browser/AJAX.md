AJAX

Asynchronous JavaScript + XML

这一技术能够向服务器请求额外的数据而无须刷新页面，能够带来更好的用户体验。

Although X in Ajax stands for XML, JSON is used more than XML nowadays because of its many advantages such as being lighter and a part of JavaScript.

Both JSON and XML are used for packaging information in Ajax model.

The `XMLHttpRequest` API is the core of Ajax.

To send an HTTP request, create an `XMLHttpRequest` object, open an URL, and send the request.

    let xhr = new XMLHttpRequest();
    
    xhr.open(httpMethod, url);
    xhr.send();

在使用XHR对象时，要调用的第一个方法是`open()`，它接受3个参数：

    XMLHttpRequest.open(method, url, async, user, password);

After the transaction completes, the object will contain useful information such as the response body and the HTTP status of the result.     
    
A request made via `XMLHttpRequest` can fetch the data in one of two ways, asynchronously or synchronously.

The type of request is dictated by the optional **async** argument (the third argument) that is set on the `XMLHttpRequest.open()` method.
 
XMLHttpRequest有两种使用方式：同步或异步。

