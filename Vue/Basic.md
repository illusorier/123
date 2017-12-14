## Class and Style Bindings

A comm

## Computed Properties and Watchers

#### Computed Properties

In-template expressions are very convenient, but they are really only meant for simple operations.

Putting too much logic into your templates can make them bloated and hard to maintain.

    <div id="example">
      {{ message.split('').reverse().join('') }}
    </div>
    
You can data-bind to computed properties in

It is often a better idea to use a computed property rather than an imperative `watch` callback.