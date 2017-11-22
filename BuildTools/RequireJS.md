RequireJS is a JavaScript file and module loader.

It is optimized for in-browser use, but it can be used in other JavaScript environments.
        
        
假如我们的项目目录如下：

        -project-directory/
            -index.html
            -scripts/
                -main.js
                -assets/
                    -require
                    -jquery
                    -lodash
                
我们不希望index.html中出现如下的代码：

    　　<script src="1.js"></script>
    　　<script src="2.js"></script>
    　　<script src="3.js"></script>
    　　<script src="4.js"></script>
    　　<script src="5.js"></script>
    　　<script src="6.js"></script>
    
运用RequireJS，我们可以这么做：

        <script src="scripts/assets/require.js" data-main="js/main"></script>
        
main.js中包括如下内容：

        require(['jquery', 'lodash'], function ($, _){
            // some code here
        });