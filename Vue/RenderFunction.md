Those coming from a React world are probably very familiar with render functions.

React components are built with them, usually through `JSX`.

> It's worth nothing that Vue.js's template actually compile down to render function at build time.

> Templates just provide a convenient and familiar syntax on top of render function. While more powerful, render functions often suffer in the readability department.

大多数情况下，我们使用template元素来构建HTML文档。

Vue recommends using templates to build your HTML in the vast majority of cases. 

但这不意味着我们不能用JS来生成HTML。

There are situations however, where you really need the full programmatic power of JavaScript.

That's where you can use the **render function**, a closer-to-the-compiler alternative to templates.

Components with `render function` do not have a template tag or property.

Instead they define a function called `render` 

render属性是一个函数

##### createElement Arguments

How to use template features in the createElement function.

    render: function (createElement) {
      // @returns {VNode}
      return createElement(
        // {String | Object | Function}
        'div'
        // An HTML tag name, 
        // {Object}
        // A data object corresponding to the attributes you would use in a template.Optional.
        {}
        // {String | Array}
        // Children VNodes, built using createElement()
        // Optional
      )
    }
    
This object also allows you to bind normal HTML attributes as well as 

The `render` function has priority over the render function compiled from `template` option or in-DOM HTML template of the mounting element which is specified by the `el` option.

> Aliasing `createElement` to `h` is a common convention you'll see in the Vue ecosystem and

虚拟DOM

Vue builds a **virtual DOM** to keep track of the changes it needs to make to the real DOM.

"Virtual DOM" is what we call the entire tree of VNodes, built by a tree of Vue components.