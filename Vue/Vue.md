## The Vue Instance

Every Vue application starts by creating a new **Vue instance** with the `Vue` function:

        var vm = new Vue({
            // options
        })

When you create a Vue instance, you pass in an **options object**.

How you can use these options to create your desired behavior.

### Data and Methods

When a Vue instance is created, it adds all the properties found 

        var vm = new Vue({
            data: {
                name: 'bill'
            }
        });
        
When you pass a plain JavaScript object to a Vue instance as its `data` option, Vue will walk through all of its properties and convert them to getter/setters using `Object.defineProperty`.


组件写法：

组件这个概念是在Angular1的后期版本 (1.5) 中引入的，而Vue完整支持组件化的代码结构，每个路由对应的都是某个组件，而不是像Angular当中controller + template。

每个组件都由相应的数据(modal)，决定了该组件目前所处于的状态。

两者组件注册(register)的写法是类似的，vue并没有采用react和ng2的基于class的组件声明方式。

- Compiler: code that is responsible for compiling template strings into JavaScript render functions.

- Runtime: code

#### Constructor

我们通过构造函数Vue创建一个Vue的实例来启动Vue。

类似于面向对象中类的实例化。

Using the variable vm (short for ViewModel) to refer to our Vue instances.

传入构造函数的参数(options object)包括了关于该Vue实例的哪些内容？

我认为这是理解Vue的很好的一个角度。

首先，每个Vue实例都需与一个HTML元素相关联，可以是an existing DOM element,也可以是用html的template属性，还可以是用js写的render属性。

When you instantiate a Vue instance, you need to pass in an **options object** which can contain options for data, template, element to mount on, lifecycle callbacks and more.
    
The Vue constructor can be extended to create reusable component constructors with pre-defined options.

除此之外，我们还可以用构造函数Vue的extend方法来创建可复用的组件构造函数。

    var MyComponent = Vue.extend({
      // extension options
    })
    
    // all instance of 'MyComponent` are created with
    // the pre-defined extension options
    var myComponentInstance = new MyComponent()
    
Although it is possible to create 
    
#### Properties and Methods

Each Vue instance **proxies** all the properties found in its `data` object:

API
#### Options / Data

##### data

- Type: Object | Function

- Details: 

  The data object for the Vue instance.
  
  Once observed, you can no longer add reactive properties to the root data object.It is therefore recommended to declare all root-level 

  After the instance is created, the original data object can be accessed as `vm.$data`.
  
##### computed

- Type: `{ [key: string]: Function | { get`

- Details:

  Computed properties to be 

##### methods

- Details:

  Methods to be mixed into the Vue instance
  
  Note that you should not use an arrow function to define a method (Arrow functions bind the parent context).

#### Options / DOM

##### el

- Type: string | HTMLElement

- Details: Provide the Vue instance an existing DOM to mount on. It can be a CSS selector string or an actual HTMLElement.

  After the instance is mounted, the resolved element will be accessible as `vm.$el`.
  
  If this option is available at instantiation, the instance will immediately enter compilation;
  
  If neither `render` function nor `template` option is present, the in-DOM HTML of the mounting 
  
##### template

- Type: string

  A string template to be used as the markup for the Vue instance. The template will **replace** the mounted element.
  
  If render function is present in the Vue option,the template will be ignored.
  
#### Options / Lifecycle Hooks

##### mounted

- Type: Function
- Details: Called after the instance has just been mounted where `el` is replaced by the newly created `vm.$el`.

#### Instance Methods / Lifecycle

##### vm.$mount( [elementOrSelector] )

If a Vue instance didn't receive the el option at instantiation, it will be in "unmounted" state, without an associated DOM element. vm.$mount() can be used

The method returns the instance itself so you can chain other instance methods after it.

## Template Syntax

我们都知道Vue可以实现双向数据绑定，把rendered DOM(被渲染的DOM)和Vue实例的数据绑定。

Vue.js uses an HTML-based template syntax that allows you to declaratively bind the rendered DOM to the underlying Vue instance's data.

下面这点很重要！

Under the hood, Vue compiles the templates into Virtual DOM render functions.

Combined with the reactivity system, Vue is able to intelligently figure out the minimal amount of components to re-render and apply the minimal amount of DOM manipulation when the app state changes.

#### Text

数据绑定最基本的形式就是在某个元素中插入text，与data中的属性实现绑定。

但这种

The most basic form of data binding is text interpolation using "Mustache" syntax (double curly braces):

    <span>Message: {{ msg }}</span>
    
The mustache tag will be replaced with the value of the `msg` property on the corresponding data object.

It will also be updated whenever the data object's `msg` property changes.

You can also perform one-time interpolations that do not update on data change by using the *v-once directive*

#### Attributes



Mustache cannot be used inside HTML attributes, instead use a `v-bind directive`:

    <a v-bind:href = "url"></a>
    
The `v-` prefix serves as a visual cue for identifying Vue-specific attributes in your templates.
    
Vue.js provides special shorthands for two of the most often used directives, `v-bind` and `v-on`:
    
    <a :href="url"></a>
    
    <a v-on:click = "doSomething"></a>
    
    <a @click = "doSomething"></a>
    
They may look a bit different from normal HTML, but `:` and `@` are valid chars for attribute names.
    
#### Using JavaScript Expressions

So far we've only been binding to simple property keys in our templates.

But Vue.js actually supports the full power of JavaScript expressions inside all data bindings.

#### Directive

Directive are special attributes with the `v-` prefix

## Computed Properties and Watchers

#### Computed Properties

In-template expressions are very convenient,but they are really only meant for simple operations.

Putting too much logic into your templates can make them bloated and hard to maintain.

    <div id="example">
      {{ message.split('').reverse().join('') }}
    </div>
    
You can data-bind to computed properties in

## Event Handling

我们通过`v-on`这个directive来实现对DOM

We can use the `v-on` directive to listen to DOM events and run some JavaScript when they're triggered.

#### Method Event Handlers

The logic for many event handlers will be more complex though, so keeping your JavaScript in the value of the `v-on` can also accept the name of a method you'd like to call.

#### Methods in Inline Handlers

Instead of binding directly to a method name, we can also use methods in an inline JavaScript statement.

#### Event Handlers 

The logic for many event handlers will be more complex though, so keeping

#### Form Input Bindings

那么，在Vue中我们该如何实现双向绑定

You can use the `v-model` directive to create two-way data bindings on form input and textarea elements.

You can use the  `v-model` directive to create two-way data binding way 

## Render Functions

大多数情况下，我们使用template元素来构建HTML文档。

Vue recommends using templates to build your HTML in the vast majority of cases. 

但这不意味着我们不能用JS来生成HTML。

这时我们便使用Vue实例Options的render属性。

There are situations however, where you really need the full programmatic power of JavaScript.

That's where you can use the **render function**, a closer-to-the-compiler alternative to templates.

render属性是一个函数


##### createElement Arguments

How to use template features in the createElement function.

    render: function (createElement) {
      // @returns {VNode}
      return createElement(
        // {String | Object | Function}
        // {Object}
        // A data object corresponding to the attributes you would use in a template.Optional.
        // {String | Array}
        // Children VNodes.Optional
      )
    }
The `render` function has priority over the render function compiled from `template` option or in-DOM HTML template of the mounting element which is specified by the `el` option.

> Aliasing `createElement` to `h` is a common convention you'll see in the Vue ecosystem and 

## Custom Directives

In addition to the default set of directives shipped in core(`v-model` and `v-show`), Vue also allows you to register your own custom directive.

#### Hook Function



## Different Builds

#### Terms

- Compiler: code that is responsible for compiling template strings into JavaScript render functions.
- Runtime: code that 

#### Runtime + Compiler vs Runtime-only

If you need to compile 

## Reactivity in Depth

When you pass a plain JavaScript object to a Vue instance as its data option,Vue will walk through all of its properties and convert them to getter/setters using `Object.defineProperty`.

Every component instance has a corresponding **watcher** instance,which records any properties "touched" during

## Custom Directives

In addition to the default set of directives shipped in core (`v-model` and `v-show`)