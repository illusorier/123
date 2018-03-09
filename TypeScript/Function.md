## Function

TypeScript also adds some new capabilities to the standard JavaScript functions to make them easier to work with.

因为类型系统的引入，我们需要给函数的参数和返回值标注类型。

        function add (x: number, y: number): number {
            return x + y;
        }
        
        let myAdd = 
        
We can add types to each of the parameters

