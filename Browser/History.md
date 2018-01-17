The `Window.history` read-only property returns a reference to the `History` object, which provides an interface for manipulating the browser *session history*.

Moving backward and forward 

`onpopstate` is an event handler for the `popstate` event on the window.

A `popstate` event is dispatched to the window 

The sequence of Documents in a browsing context is its **session history**.

历史记录

History objects provide a representation 

Each **session history entry** consists of either a URL or a state object, or both, and may in addition have a title

The `History` interface allows manipulation of the browser *session history*

HTML5 introduced the **history.pushState()** and **history.replaceState()** methods, which allow you to add and modify history entries.

SPA的路由功能是如何实现的？

In older versions of HTML, we had limited control over browser history.

The HTML5 History API gives developers the ability to modify a website's URL without a full page refresh.

Before

### pushState()

pushState() takes three parameters: a state object, a title (which is currently ignored), and (optionally) a URL.

### replaceState()

A `popstate` event is dispatched to the window every time the active history entry 

The `Window.location` read-only property returns a Location object with information about the current location of the document.

Though `Winodw.location` is a read-only `Location` object, you can also assign a `DOMString` to it.

        location.href = 'https://www.baidu.com';
        
The `Location.replace()` 

The `Location.reload()` method reloads the resource from the current URL.

If it is `false` or not specified, the browser may reload the page from its cache.

### popstate

A **popstate** event is dispatched to the window each time the active history entry changes between two history entries for the same document.


