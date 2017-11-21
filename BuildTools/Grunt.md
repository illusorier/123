### The "wrapper" function

`Gruntfile`的文件结构

Every `Gruntfile` (and gruntplugin) uses this basic format, and all of your Grunt code must be specified inside this function:

        module.exports = function(grunt) {
            // Do grunt-related things in here
        };
        
### Configuration tasks

具体的使用方法

How to configure tasks for your project using a `Gruntfile`.
        
Task configuration is specified in your `Gruntfile` via the `grunt.initConfig` method.

#### grunt-nunjucks-2-html

Once plugin has been installed include it in your `Gruntfile.js`.

       grunt.loadNpmTasks('grunt-nunjucks-2-html');