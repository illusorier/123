> JavaScript与HTML之间的交互是通过事件实现的。事件可以使用侦听器(或处理程序)来预订事件，以便事件发生时执行相应的代码。这种在传统软件工程中被称为观察员模式的模型，

事件流描述的是从页面中接收事件的顺序。

IE的事件流叫事件冒泡(event bubbling)，即事件开始时由最具体的元素

"DOM2级事件"规定的事件流包括三个阶段:

事件就是用户或浏览器自身执行的某种动作。

响应某个事件的函数就叫事件处理程序(或事件侦听器)。事件处理程序的名字以"on"开头。

为事件指定处理程序的方式有好几种。

某个元素支持的每种事件，都可以使用一个与相应事件处理程序同名的

## EventTarget

`EventTarget` is an interface implemented by objects that can receive events and may have listeners for them.

`Element`, `document`, and `window` are the most common event targets, but 

#### MouseEvent

The **MouseEvent** interface represents events that occur due to the user interacting with a pointing device (such as a mouse).

Common events using this interface include *click*, *dbclick*, *mouseup*, *mousedown*.

MouseEvent derives from UIEvent, which in turn derives from Event. 

#### CSS Transition Events

##### transitionstart

A CSS transition has actually started.

## Event Order

If an element and one of its ancestors have an event handler for the same event, which one should fire first?

        <div id="element1">
            <div id="element2"></div>
        </div>

#### Event capturing

事件捕获，由外层元素到内层元素。

the event handler of element1 fires first, the event handler of element2 fires last.

#### Event bubbling

事件冒泡，由内层元素到外层元素。

the event handler of element2 fires first, the event handler of element1 fires last.

#### W3C model

W3C has very sensibly decided to take a middle position in this struggle.

Any event taking place in the W3C event model is first captured until it reaches the target element and then bubbles up again.

If not specified, `useCapture` defaults to `false`.

Events can be created with the `Event` constructor as follow:

        

##### Event.currentTarget

Identifies the current target for the event, as the event traverses the DOM.



