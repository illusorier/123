## HTML Compile

AngularJS's HTML compiler allows the developer to teach the browser new HTML syntax.

The compiler allows you to attach behavior to any HTML element or attribute and even create new HTML elements or attributes with custom behavior.

AngularJS calls these behavior extensions `directives`.

Compiler is an AngularJS service which traverses the DOM looking for attributes.

The compilation process happens in two phases: 

1. **Compile**:

1. `$compile` traverses the DOM and matches directives.

    If the compiler finds

2.  Once all directives matching a DOM element have been identified, the compiler sorts the directive by their `priority`.

    
    
    

3. `$compile` links the template 

A directive is just a function which executes 

#### The difference between Compile and Link



在ng1中应当如何实现数据绑定？

In AngularJS applications, you move the job of filling page templates with data from the server to the client.

`$digest()`

Processes all of the watchers of the current scope and its children.
