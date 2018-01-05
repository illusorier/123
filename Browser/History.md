The sequence of Documents in a browsing context is its **session history**.

历史记录

History objects provide a representation 

Each **session history entry** consists of either a URL or a state object, or both, and may in addition have a title

The `History` interface allows manipulation of the browser *session history*

HTML5 introduced the **history.pushState()** and **history.replaceState()** methods, which allow you to add and modify history entries.

SPA的路由功能是如何实现的？

The HTML5 History API gives developers the ability to modify a website's URL without a full page refresh.

### pushState()

pushState() takes three parameters: a state object, a title (which is currently ignored), and (optionally) a URL.

### replaceState()




A `popstate` event is dispatched to the window every time the active history entry 