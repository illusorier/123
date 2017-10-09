> JavaScript与HTML之间的交互是通过事件实现的。事件可以使用侦听器(或处理程序)来预订事件，以便事件发生时执行相应的代码。这种在传统软件工程中被称为观察员模式的模型，

事件流描述的是从页面中接收事件的顺序。

IE的事件流叫事件冒泡(event bubbling)，即事件开始时由最具体的元素

"DOM2级事件"规定的事件流包括三个阶段:

事件就是用户或浏览器自身执行的某种动作。

响应某个事件的函数就叫事件处理程序(或事件侦听器)。事件处理程序的名字以"on"开头。

为事件指定处理程序的方式有好几种。

某个元素支持的每种事件，都可以使用一个与相应事件处理程序同名的

#### MouseEvent

The **MouseEvent** interface represents events that occur due to the user interacting with a pointing device (such as a mouse).

Common events using this interface include *click*, *dbclick*, *mouseup*, *mousedown*.

MouseEvent derives from UIEvent, which in turn derives from Event. 

#### CSS Transition Events

##### transitionstart

A CSS transition has actually started.