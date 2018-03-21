        @Component({
            selector: 'app-root',
            templateUrl: './app.component.html',
            styleUrls: ['./app.component.css']
        })
        export class AppComponent {
            title: string;
            myHero: string;
            
            constructor(title: string, myHero:string) {
                this.string = string;
                this.myHero = myHero;
            }
        }

Component initialization: Constructor or variable initialization?

在Angular中组件是如何声明的？

        import { Component } from '@angular/core';
        
The `@Component` decorator identifies the class immediately below it as a component class.

        @Component({
            selector:
            
Some of the most useful `@Component` configuration options:



You define a component's view with its companion template.

Without a framework, you would be responsible for 

比如我们可能在 `$.ajax()` 请求成功后的回调中去手动修改DOM tree (`$.html()`)。　

Angular supports *two-way data binding*, a mechanism for coordinating parts of a template with parts of a component.

### Creating a class for the data

我认为这是一个非常好的实践。

A component has a lifecycle managed by Angular.



