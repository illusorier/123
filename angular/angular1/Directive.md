## Directives

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

#### Creating a Directive that Wraps Other Elements

##### What is the difference between a source template and an instance template?

The fact that Angular allows DOM manipulation 

`compile`

        function compile($element, $attrs) { ... }

The compile function deals with transforming the template DOM.

Since most directives do not do template transformation, it is not used often.

A compile function can have a return value which can be either a function or an object.

`link`

This property is used only if the `compile` property is not defined.

        function link($scope, $element, $attrs, 
        
The link function is responsible for registering DOM listeners as well as updating the DOM.

It is executed after the template has been cloned.

This is where most of the directive logic will be put.

#### Transclusion

Transclusion is the process of extracting a collection of DOM elements from one part of the DOM elements and copying them to another part of the DOM, while maintaining their connection to the original AngularJS scope from where they were taken.

Transclusion is used (often with `ngTransclude`) to 