## $location

The $location service parses the URL in the browser address bar

`$location` service has two configuration modes which control the format of the URL in the browser address bar: **Hashbang mode**(the default) and the **HTML5 mode**.

##### $locationChangeSuccess

Broadcasted after a URL was changed.

## $urlRouter

`$urlRouterProvider` has the responsibility of watching `$location`.

## $http

The `$http` service is a core AngularJS service that facilitates communication with the remote HTTP servers via the browser's XMLHttpRequest object or via JSONP. 

The `$http` service is a function which takes a single argument - a configuration object - that is used to generate an HTTP request and returns a promise.

Shortcut methods are also available.

## $resource

AngularJS `$resource` service is specially designed for dealing with RESTful APIs

