## Array

因为TS应用了类型系统，因此有关数组的使用也有所不同。

Array types can be written in one of two ways.

In the first, you use the type of the elements followed by `[]` to denote an array of that element type:

最基本的使用方式：

        let fibonacci: number[] = [1, 1, 2, 3, 5];
        
假如要实现和JavaScript中一样的数组声明方式，即不对数组成员的类型做任何限制：

        let myArray: any[] = [1, "1", {}];
        
The second way uses a generic array type  
        
另一种方式，数组泛型：

        ley fibonacci: Array<number> = [1, 1, 2, 3, 5];

## Any

We may need to describe the type of variables that we do not know when 

## Tuple

Tuple types allow you to express an array where the type

        let myArray: [number, string] = ["hello", 1];
      
## Enum

An enum is a way to organize a collection of related values.