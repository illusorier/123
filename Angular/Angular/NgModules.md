#### 模块在Angular中的位置 => 如何声明模块？

Angular apps are modular and Angular has its own modularity system called *NgModules*.

Every Angular app has at least one NgModule class, the root module, conventionally named `AppModule`.

每个angular application都至少有一个NgModule class，作为根module。

While the root module may be the only module in a small application, most apps have many more *feature modules*, each a cohesive block of code dedicated to an application domain.

**How？**

An NgModule, whether a root or feature, is a class with `@NgModule` decorator.

`NgModule` is a decorator function that takes a single metadata object whose properties describe the module.

The most important properties are:

- `declarations` - the *view classes* that belong to this module. Angular has three kinds of view classes: components, directives, and pipes.

    You tell Angular which components belong to the `AppModule` by listing 
- `exports`
- `imports`
- `providers`
- `bootstrap`


下面是一个简单的module声明：

        import { Ngmodule } from '@angular/core';
        import { BrowserModule } from '@angular/platform-browser'
        import { AppComponent } from './app.component'
        
        @NgModule({
            imports:      [ BrowserModule ],
            providers:    [ Logger ],
            declarations: [ AppComponent ],
            exports:      [ AppComponent ],
            bootstrap:    [ AppComponent ]
        })
        export class AppModule {}
        
> The `export` of `AppComponent` is just to show how to use the `exports` array to export a component. A root module has no reason to export anything because other components do not need to *import* the root module.

Every component must be declared in one - and only one - NgModule.       

> Module声明上的差异: 没有provider, exports和bootstrap。

> 文件目录结构的差异：

有一个`app.module.ts (src/app/app.module.ts) `文件，包含了该项目的根模块。

还有一个`main.ts (src/main.ts) `文件

By convention, the *root module* class is called `AppModule` and it exists in a file named `app.module.ts`.

仅仅声明root module是不够的。

You launch the application by bootstrapping the `AppModule` in the `main.ts` file.

> 在Angular1中，我们是如何bootstrap整个项目的？

Angular offers a variety of bootstrapping options targeting multiple platforms.

#### Compile ahead-of-time (AOT)

In the *static* option, the Angular compiler runs ahead of time as part of the build process, 
