## Directives

最基本的问题就是：如何去写一个Directive?

        angular
            .module('moduleName')
            .directive('directiveName', function() {
              return {
                // DDO
              }
            })

ng-show/ng-hide和ng-if的差异？

不管是directives还是components，它们的作用都是将项目代码中重复部分提取出来，抽象成一个新的概念。

At a high level, directives are markers on a DOM element (such as an attribute, element name or CSS class)

Similar to the terminology used when an element matches a selector, we say an element **matches** a directive。

`$compile` can match 

Let's talk about the **API for registering directives**.

Much like controllers, directives are registered on modules.

While creating directives, AngularJS allows you to create an `isolated scope` with some custom bindings to the parent scope.

These bindings are specified by the attribute defined in `HTML` and the definition of the `scope` property in the directive definition object.

There are 3 types of binding options

There are a few special events that AngularJS emits.

When a DOM node that has been compiled with Angular's compiler is destroyed, it emits a $destroy event.

#### Template-expanding directive

可以实现HTML的复用，提高代码的可维护性和扩展性。

> Unless your template is very small, it's typically better to break it apart into its own HTML file and load it with the `templateUrl` option.

你可以register一个最简单的directive, 它的DDO中只有templateUrl，但这样的directive功能十分局限。

You need to create a different controller each time in order to re-use such a directive.

#### Isolating the Scope of a Directive





#### Creating a Directive that Wraps Other Elements

#### Creating Directives that Communicate

Sometimes it's desirable to be able to pass in an entire template rather than a string or an object.

To do this, we need to use the `transclude` option.



##### What is the difference between a source template and an instance template?

The fact that Angular allows DOM manipulation 

### Directive Definition Object

`scope`

The scope property can be `false`, `true`, or an object.

- `false` (default): 

`compile`

        function compile($element, $attrs) { ... }

The compile function deals with transforming the template DOM.

Since most directives do not do template transformation, it is not used often.

The compile function takes the following arguments:

- `tElement` - 

A compile function can have a return value which can be either a function or an object.

`controller`

Controller constructor function.

`require`



`link`

This property is used only if the `compile` property is not defined.

        function link($scope, $element, $attrs, controller) { ... }
        
The link function is responsible for registering DOM listeners as well as updating the DOM.

It is executed after the template has been cloned.

This is where most of the directive logic will be put.

#### Transclusion

Transclusion is the process of extracting a collection of DOM elements from one part of the DOM elements and copying them to another part of the DOM, while maintaining their connection to the original AngularJS scope from where they were taken.

会有一个常见的需求：我们希望directive中的template是可以被扩充的，是动态的。

    <modal>
      <modal-body></modal-body>
      <modal-foot></modal-foot>
    </modal>
    
Transclusion is used (often with `ngTransclude`) to insert  