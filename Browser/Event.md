> JavaScript与HTML之间的交互是通过事件实现的。事件可以使用侦听器(或处理程序)来预订事件，以便事件发生时执行相应的代码。这种在传统软件工程中被称为观察员模式的模型，

事件流描述的是从页面中接收事件的顺序。

IE的事件流叫事件冒泡(event bubbling)，即事件开始时由最具体的元素

"DOM2级事件"规定的事件流包括三个阶段:

事件就是用户或浏览器自身执行的某种动作。

响应某个事件的函数就叫事件处理程序(或事件侦听器)。事件处理程序的名字以"on"开头。

为事件指定处理程序的方式有好几种。

某个元素支持的每种事件，都可以使用一个与相应事件处理程序同名的

## EventTarget

在浏览器中，事件的分发和监听都要依赖于某个实现了`EventTarget`接口的object。

这个object往往是某个Element，也可以是其他特殊的object，如`XMLHttpRequest`。

`EventTarget` is an interface implemented by objects that can receive events and may have listeners for them.

`Element`, `document`, and `window` are the most common event targets, but other objects can be event targets too, for example `XMLHttpRequest`.

#### MouseEvent

The **MouseEvent** interface represents events that occur due to the user interacting with a pointing device (such as a mouse).

Common events using this interface include *click*, *dbclick*, *mouseup*, *mousedown*.

MouseEvent derives from UIEvent, which in turn derives from Event. 

The `mousedown` event is fired when a pointing device button is pressed on an element.

The `mouseover` event is fired when a pointing device (usually a mouse) is moved while over an element.

#### CSS Transition Events

##### transitionstart

A CSS transition has actually started.

## Event Order

在页面上的某一个区域，可能存在重叠的多个元素，那么当我们点击这一区域时，这多个元素click事件的callback是如何执行的？

        <button></button>
        
        var btn = document.querySelector('button');
        
        btn.addEventListener('click', function(){
        	    console.log('btn');
        });
        
        document.addEventListener('click', function(){
        	    console.log('document');
        })

If an element and one of its ancestors have an event handler for the same event, which one should fire first?

        <div id="element1">
            <div id="element2"></div>
        </div>

#### Event capturing

事件捕获，由父元素到子元素。

the event handler of element1 fires first, the event handler of element2 fires last.

#### Event bubbling

事件冒泡，由子元素到父元素。

the event handler of element2 fires first, the event handler of element1 fires last.

#### W3C model

W3C has very sensibly decided to take a middle position in this struggle.

Any event taking place in the W3C event model is first captured until it reaches the target element and then bubbles up again.

The web developer can choose whether to register an event handler in the capturing or in the bubbling phase.

This is done through the `addEventListener()` method.

If its last argument is `true` the 

If not specified, `useCapture` defaults to `false`.

Events can be created with the `Event` constructor as follow:

##### Event.target

A reference to the object that dispatched the event.

It is different from `event.currentTarget`  

##### Event.currentTarget

Identifies the current target for the event, as the event traverses the DOM.

Unlike the `input` event, the `change` event is not necessarily fired for each change to an element's `value`.

#### GlobalEventHandlers.onscroll

An event handler for scroll events on `element`.

### MutationRecord

A `MutationRecord` represents an individual DOM mutation.

It is the object that is passed to `MutationObserver`'s callback.

### MutationObserver

`MutationObserver` provides developers with a way to react to change in a DOM.

The `Event()` constructor creates a new `Event`.

        var evt = new Event("myEvt");
        
        document.dispatchEvent(evt);


The `EventTarget.addEventListener()` method adds the specified `EventListener` 


Dispatches an `Event` at the specified ` 

