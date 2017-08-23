## WebSocket

The WebSocket object provides the API for creating and managing a WebSocket connection to a server,

## XMLHttpRequest

Ajax技术的核心是XMLHttpRequest对象，这是微软首先引入的一个特性，其他浏览器提供商都提供了相同的技术实现。

XMLHttpRequest is an API that provides client functionality for transferring data between a client and a server.

It provides an easy way to retrieve data from a URL without having to do a full page refresh.

### Constructor

    var xhr = new XMLHttpRequest();
    
### Methods

在使用XHR对象时，要调用的第一个方法open()，它接受3个参数: 要发送的请求的类型("get"、"post"等)、请求的URL

要发送特定的请求，必须像下面这样调用send()方法

在收到响应后，响应的数据会自动填充XHR对象的属性，相关的

只要readyState属性的值由一个值变成另一个值，都会触发一次readystatechange事件

##### XMLHttpRequest.open()

The **XMLHttpRequest.open()** method initializes a request.

    xhrReq.open(method, url);
    
    
- method: The HTTP method to use, such as "GET", ""

##### XMLHttpRequest.send()

The **XMLHttpRequest.send()** method sends the request.


## XMLHttpRequestEventTarget

XMLHttpRequestEventTarget is the interface that 

### Properties

- XMLHttpRequestEventTarget.onload: Contains the function to 

## FormData

### Constructor

The **FormData()** constructor creates a new **FormData** object.

    var formData = new FormData(form)
    
- form (optional): An HTML `<form>` element

## Blob

### Constructor

Blob(blobParts[,options]): Returns a new **Blob** object. The content of the blob consists of the

## JSON

JSON(JavaScript Object Notation) is a lightweight data-interchange format.

JSON is built in two structures:

- A collection of name/value pairs.In various languages,this is realized as an object,record,struct,dictionary,hash table,keyed list,or associative array.

- An ordered listed of values.

The **JSON** object contains methods for parsing JSON and converting values to JSON.

JavaScript and JSON differences

### JSON.stringify()

The **JSON.stringify()** method converts a JavaScript value to a JSON string.

### JSON.parse()

The **JSON.parse()** method parses a JSON string,constructing the JavaScript value or object described by the string.

An optional **reviver** function can be

## Date

- If no arguments are provided, the constructor creates

## Media Query

媒体查询主要由两部分组成:媒体类型和媒体特性。

A **media query** consists of an optional media type and can, as 

    
    <link rel="stylesheet" media="(max-width: 800px)" href="example.css" />

When a media query is true, the corresponding style sheet or style rules are applied.

The **@media** CSS at rule lets you specify declaration that depend on the condition of a media query.

#### MediaQueryList

A MediaQueryList object stores information on a media query

You can compose complex media queries using logical operators