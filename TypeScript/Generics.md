In languages like C# and Java, one of the main tools in the toolbox for creating reusable components is *generic*.

Being able to create a component that can work over a variety of types rather than a single one.

在JavaScript当中，声明变量或函数时并不需要指明类型，因此也就没有必要引入泛型这个概念，但TypeScript却有所不同。

Without generics, we would either have to give the identity function a specific type:

        function identity(arg: number): number {
            return arg;
        }
        
Or, we could describe the identity function using the `any` type:

        function identity(arg: any): any {
            return arg;
        }

While using `any` is certainly generic

We actually are losing the information about what that type was

        function identity<T> (arg: T): T {
            return arg;
        }
        
泛型函数

Once we have written the generic identity function, we can call it in one of two ways.