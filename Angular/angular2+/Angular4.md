Angular is a framework for building client applications in HTML and either JavaScript or a language like TypeScript that compiles to JavaScript.

在Ng4的开发中, Angular CLI占据了什么样的位置？

The Angular CLI is a *command line interface* tool that can create a project, add files, and perform a variety of ongoing development tasks such as testing, bundling, and development.

Then you launch the app by *bootstrapping* the *root module*.

> Decorators are functions that modify JavaScript classes.

## Angular libraries

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

## Attribute Directives

An Attribute directive changes the appearance or behavior of a DOM element.

Directives的注册。

If you ran the app now, Angular would not recognize the `highlight` attribute and would ignore it.

You must declare the directive in `AppModule`

`@Directive` requires a CSS selector to identify the HTML in the template that is associated with the directive.

## Service

Components should not fetch or save data directly.

They should focus on presenting data and delegate data access to a service.

> The naming convention for service files is the service name in lowercase followed by `.service`.

You could get the data from anywhere - a web service, local storage, or a mock data source.

The `@Injectable()` decorator tells TypeScript to emit metadata about the service.

The metadata specifies that Angular may need to inject other dependencies into this service.

## Directives

Angular template are *dynamic*.

When Angular renders them, it transform 