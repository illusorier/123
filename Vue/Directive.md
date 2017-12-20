在AngularJS和Vue中，有directive这样的一个概念，在声明directive时，会写至少一个回调，在bootstrap的过程中执行。

那么在DOM API的层面上，他们是如何实现的？



AngularJS和Vue都自定义directive支持，与此同时，它们本身也提供了一些重要的内置directive。

In addition to the default set of directives shipped in core (`v-modal` and `v-show`), Vue also allows you to register your own custom directives.

Register a directive globally or locally.

        // Register a global custom directive called `v-focus`
        Vue.directive('focus', {
          // When the bound element is inserted into the DOM...
          inserted: function (el) {
            // Focus the element
            el.focus()
          }
        })

### Hook Function

A directive definition object can provide several hook functions (all optional):



### Directive Hook Arguments

Directive hooks are passed these arguments:

