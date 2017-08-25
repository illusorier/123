Angular is a framework for building client applications in HTML and either JavaScript or a language like TypeScript that compiles to JavaScript.

Then you launch the app by *bootstrapping* the *root module*.

Angular apps are modular and Angular has its own modularity system called *NgModules*.

Angular本身有自己的模块化系统。

Every Angular app has at least one NgModule class, the root module, conventionally named `AppModule`.

每个angular app都至少有一个NgModule class，作为根module。

While the root module may be the only module in a small application, most apps have many more *feature modules*.

> Decorators are functions that modify JavaScript classes.

An NgModule, whether a root or feature, is a class with `@NgModule` decorator.

`NgModule` is a decorator function that takes a single metadata object

## NgModules

Angular ships as a collection of JavaScript modules.

You can think of them as library modules.

Each Angular library name begins with the `@angular` prefix.

You install them with the npm package manager and import parts of them with JavaScript `import` statements.

Angular本身自带了诸多核心模块，可以按需引入。

For example, import Angular's `Component` decorator from the `@angular/core` library like this:

        import { Component } from '@angular/core';
        


## Components

A *component* controls a patch of screen called a *view*.

## Metadata

> ng4中使用装饰器模式来声明子组件，而ng1和vue2中则使用一个API来return出子组件的构造函数。

The `@Component` decorator takes a required configuration object with the information Angular needs to create 

        @Component({
            selector: 'hero-list',
            templateUrl: './hero-list.component.html',
            providers: [HeroService}
        })
            
            
- `selector`: CSS selector that tells Angular to create and insert an instance of this component where it finds a `<hero-list>` tag in parent HTML.
- `templateUrl`: module-relative address of this component's HTML template.
- `providers`: array of dependency injection providers for services that the component requires.