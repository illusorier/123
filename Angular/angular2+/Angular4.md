Angular is a framework for building client applications in HTML and either JavaScript or a language like TypeScript that compiles to JavaScript.

在Ng4的开发中, Angular CLI占据了什么样的位置？

The Angular CLI is a *command line interface* tool that can create a project, add files, and perform a variety of ongoing development tasks such as testing, bundling, and development.

Then you launch the app by *bootstrapping* the *root module*.

> Decorators are functions that modify JavaScript classes.

## NgModules

Angular apps are modular and Angular has its own modularity system called *NgModules*.

Angular本身有自己的模块化系统。

Every Angular app has at least one NgModule class, the root module, conventionally named `AppModule`.

每个angular app都至少有一个NgModule class，作为根module。

While the root module may be the only module in a small application, most apps have many more *feature modules*, each a cohesive block of code dedicated to an application domain.

从文件目录结构的角度去理解ng4：

有一个`app.module.ts`文件，包含了该项目的根模块。

Every Angular app has a *root module* class.

You bootstrap that module to launch the application.

By convention, the *root module* class is called `AppModule` and it exists in a file named `app.module.ts`.

An NgModule, whether a root or feature, is a class with `@NgModule` decorator.

`NgModule` is a decorator function that takes a single metadata object whose properties describe the module.

The most important properties are:

- `declarations` - the *view classes* that belong to this module. Angular has three kinds of view classes


        import { Ngmodule } from '@angular/core';
        import { BrowserModule } from '@angular/platform-browser'
        import { AppComponent } from './app.component'
        
        @NgModule({
            declarations: [ AppComponent ],
            bootstrap: [ AppComponent ]
        })
        
The `@NgModule.bootstrap` property identifies this `AppComponent` as the *bootstrap component*

You launch the application by bootstrapping the `AppModule` in the `main.ts` file.

Angular offers a variety of bootstrapping options targeting multiple platform.

Every component must be declared in one - and only one - NgModule.       

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

> The naming convention for service files is the service name in lowercase followed by `.service`.

You could get the data from anywhere - a web service, local storage, or a mock data source.

The `@Injectable()` decorator tells TypeScript to emit metadata about the service.

The metadata specifies that Angular may need to inject other dependencies into this service.