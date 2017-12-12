In client-server protocols, like HTTP, sessions consist of three phases:

1.

无状态

HTTP is a stateless protocol.

In order to associate a request to any other request, you need a way to store user data between HTTP requests.

Cookies and URL parameters are both suitable ways to

But

### What is a "Cookie"?

A cookie is a small piece of text stored on a user's computer by their browser.

Common uses for cookies are authentication, storing of site preferences, shopping cart items, and server session identification.

Each time the user's web browser interacts with a web server it will pass the cookie information to the web server.

Only the cookies stored by the browser that relate to the domain in the requested URL will be sent to the server.

### What is a "Session"?

A session can be defined as a server-side storage of information that is desired to persist throughout the user's interaction with the web site or web application. 

Instead of storing large and constantly changing information via cookies in the user's browser, only a unique identifier is stored on the client side (called a "session id"). 

This session id is passed to the web server every time the browser makes an HTTP request (ie a page link or AJAX request). 

The web application pairs this session id with it's internal database and retrieves the stored variables for use by the requested page.

### cookie-parser

Parse `Cookie` 