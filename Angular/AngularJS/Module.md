Most applications have a main method that instantiates and wires together the different parts of the application.

比如在Vue的官方文档中就有这样的描述：Every Vue application starts by creating a new **Vue instance** with the `Vue` function.

AngularJS apps do not have a main method.

Instead modules declaratively specify how an application should be bootstrapped.

我们可以把一个module想象成一个Module类的实例，通过该实例的一些方法来构建整个application。

A module is a collection of configuration and run blocks which get applied to the application during the bootstrap process.

1. **Configuration blocks** - 


       angular
           .module('moduleName')
           .config(function(){
                
           })
           
           
2. **Run blocks** - 