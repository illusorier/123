Vue是什么，它能被应用在什么样的场景中，可以解决哪些问题？

Vue可以被应用于Web App的开发的场景中。

The core library focuses on the view layer only,

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