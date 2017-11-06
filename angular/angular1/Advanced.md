## Advanced AngularJS

看完以下部分，应当能回答这个问题：How data-binding works in AngularJS?

There is a lot of vocabulary around this: `$watch`, `$apply`, `$digest`, `$dirty-checking`.

浏览器和Angular中DOM和视图更新的先后顺序: callback代码执行完后再更新DOM。

Our browser is waiting for events, for example the user interactions.

If you click on a button or write into an input, the event's callback will run inside JavaScript and there you can do any DOM manipulation, so when the callback is done, the browser will make the appropriate change in the DOM.

Angular extends this events-loop creating something called `angular context`.  

Angular扩展了浏览器本身的event loop。

> Watches are not called periodically based on a timer.

##### The $watch list

Every time you bind something in the UI you insert a `$watch` in a `$watch list`.

##### $digest loop

When the browser receives an event that can be managed by the `angular context`, the `$digest` loop will be fired. This loop is made from two smaller loops. One processes the `$evalAsync` queue and the other one processes the `$watch` list.

When the `$digest loop` finishes, the DOM makes the changes.

> If you want to be notified whenever $digest is called, you can register a watchExpression function with no listener.

        $rootScope.$watch(function() {
          console.log('digest!');
        }); 

##### When angular does not use $apply for us

 #### Compile vs Link
 
 ##### The compile phase
 
 When the DOM is loaded Angular starts the compile phase, 
 
 ![](../../assets/angular-compile.png)
 
  ![](../../assets/angular-link.png)

#### $parse

Advanced Angular

If you want to step up in your AngularJS knowledge, $parse is one of the most important services that you should know about.

Converts Angular expression into a function.

`$parse` takes an expression, and returns you a function.

##### $scope.$evalAsync() vs $timeout()

Sometimes, in an AngularJS application, you have to explicitly tell AngularJS when to initiate it's $digest lifecycle (for dirty-data checking).

Most of time, this can be easily accomplished with the $scope.$apply method.

However, some of the time, you have to defer the $apply() invocation because it may or may not conflict with an already-running $digest phase.

But, the $scope.$evalAsync() is likely to execute in the same tick of the JavaScript event loop.

        angular
            .module('demo', [])
            .directive('demoDirective', function() {
            
            

#### 'this' vs $scope in AngularJS controller

- `this`: When the controller constructor function is called, `this` is the controller.

- `$scope`: Every controller has an associated `$scope` object. A controller (constructor) function is responsible for setting model properties and functions/behaviour on its associated `$scope`.

#### Kill $scope - Replace it with controllerAs