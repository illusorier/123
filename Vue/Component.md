## Component

Components are one of the most powerful features of Vue. They help you extend basic HTML elements to encapsulate reusable code.

At a high level, components are custom elements that Vue's compiler attaches behavior to.

#### Registration

Vue中组件的注册方式类似于AngularJs，都是通过调用某个全局对象中相应的方法来完成。

To register a global component, you can use `Vue.component(tagName, options)`.

    Vue.component('my-component', {
      // options
    })
    
Once registered, a component can be used in an instance's template as a custom element, `<my-component></my-component>`.

Make sure the component is registered **before** you instantiate the root Vue instance.

##### Local Registration

You don't have to register every component globally. 

You can make a component available only in the scope of another instance/component by registering it with the `components` instance option.

    var Child = {
      template: '<div>A custom component!<div>'
    }
    
    new Vue({
      //...
      components: {
        // <my-component> will only be available in parent's template
        'my-component': Child
      }
    })
    
#### Composing Components

Components are meant to be used together, most commonly in parent-child relationships: component A may use component B in its own template.

In Vue.js, the parent-child component relationship can be summarized as **props down**, **events up**.

The parent passes data down to the child via **props**,

#### Props

##### Passing Data with Props

Every component instance has its own **isolated scope**.

This means you cannot (and should not) directly reference parent data in a child component's template.

数据可以用props传入子组件。

Data can be passed down to child components using **props**.

A prop is a custom attribute for passing information from parent components.

    Vue.component('child', {
      // declare the props
      props: ['message'],
      // just like data, the prop can be used inside tempaltes
      // and is also made available in the vm as this.message.
      
##### Dynamic Props

Similar to binding a normal attribute to an expression, we can also use `v-bind` for dynamically binding props to data on the parent.

Whenever the data is updated in the parent, it will also flow down to the child.

##### One-Way Data Flow

All props form a **one-way-down** binding between the child property and parent one: when the parent property updates, it will flow down to the child, but not the other way around.

##### Prop Validation

#### Custom Events

Every Vue instance implements an events interface, which means it can:

- Listen to an event using `$on(eventName)`
- Trigger an event using `$emit(eventName)`

In addition, a parent component can listen to the events emitted from a child component using `v-on` in the template where the child component is used.

> You cannot use `$on` to listen to events emitted by children. You must use `v-on` directly in the template.

There may be times when you want to listen for a native event on the root element of a component.

#### Content Distribution with Slots

在创建component的时候，我们有时需要在组件中加入自定义的template，和组件原有的template组合形成最终的组件template。

When using components, it is often desired to compose them like this:

    <app>
      <app-header></app-header>
      <app-footer><app-footer>
    </app>
    
There are two things to note here:

1. The `<app>` component does not know what content may be present inside its mount target. It is decided by the component using `<app>`.

2. The `<app>` component very likely has its own template.

To make the composition work, we need a way to interweave the 

> Everything in the parent template is compiled in parent scope; everything in the child template is compiled in child scope.

##### Single Slot

Parent content will be **discarded** unless the child component template contains at least one `<slot>` outlet.

##### Named Slots

`<slot>` elements have a special attribute, `name`

#### Misc

##### Child Component Refs

除了props和events之外，还有一种方式可以直接访问子组件。

Despite the existence of props and events, sometimes you might still need to directly access a child component in JavaScript.

To achieve this you have to assign a reference ID to the child component using `ref`.

> $refs are only populated after the component has been rendered, and it is not reactive.
