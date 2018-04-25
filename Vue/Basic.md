Vue是什么，它能被应用在什么样的场景中，可以解决哪些问题？

Vue可以被应用于Web App的开发的场景中。

网站开发

The core library focuses on the view layer only.

获取数据 => 渲染到页面上

那么，Vue和传统的前端开发(HTML, CSS, JS)的连接点在哪？

根据HTML和CSS生成页面，执行JS。

## The Vue Instance

Vue的启动方式

Every Vue application starts by creating a new **Vue instance** with the `Vue` function:

        var vm = new Vue({
            // options 
        })

When you create a Vue instance, you pass in an **options object**.

Vue启动后发生了什么？

## Class and Style Bindings

A comm

## Computed Properties and Watchers

#### Computed Properties

In-template expressions are very convenient, but they are really only meant for simple operations.

Putting too much logic into your templates can make them bloated and hard to maintain.

    <div id="example">
      {{ message.split('').reverse().join('') }}
    </div>
    
For any complex logic, you should use a **computed property**.

## List Rendering

We can use the `v-for` directive to render a list of items based on an array.

## Event Handling

We can use the `v-on` directive to listen to DOM events and run some JavaScript when they are triggered.