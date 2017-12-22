The `$http` service is a function which takes a single argument - a configuration object - that is used to generate an HTTP request and returns a promise.

也就是说调用$http，并传入configuration object，会返回一个promise。

$httpProvider.interceptors

拦截器

For purposes of global error handling, authentication, or any kind of synchronous or asynchronous pre-processing of request or postprocessing of responses.

**request** interceptors are fired before a request is sent to the server (and of course before the data is transformed using the `transformRequest` function).

**requestError** interceptors are fired when there is a request error, i.e. if any of the previous request interceptors threw an error or returned a promise that get's rejected.