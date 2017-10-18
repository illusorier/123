The **for statement** creates a loop that consists of three 

问题1：输出100以内能同时被3和8整除的正整数。

        for (var i = 1; i <= 100; i++) {
            if ( i%3 === 0 && i%8 === 0 ) {
                console.log(i);
            }
        }
        
问题2：如何判断一个变量的值是不是整数？

问题3：如何翻转字符串？

String.prototype.split() method splits a String object into an array of strings by separating the string into substrings, using 

问题4：计算一个整数的阶乘。

问题5：实现一个数组的遍历有哪些方法？

for语句、for...in语句和Array.forEach()方法。

for循环的写法：for ([初始化]; [条件判断]; [计数器])

The **for...in statement** iterates over the enumerable properties of an object,

问题6：如何判断某个value是否存在于某个数组中？

`Array.prototype.includes` is a replacement for `indexOf` which developers used to check for presence of a value in an array.

Interestingly, many JavaScript libraries already had `includes` or similarly working `contains`.

- jQuery: `$.inArray`

- Lodash: `_.includes`

问题7：如何将数组中某个元素移到某个新的位置？

##### Array.prototype.splice()

The `splice()` method changes the contents of an array by removing 

`splice`方法的作用是在数组的某个位置删除若干个元素，同时可以插入若干个指定元素。



       originArr, oldIndex, newIndex
       
       
       
        
        

##### Array.prototype.slice()

The `slice()` method returns 

        var arr = ["Apple", "Banana", "Orange"];
        
        

#### JavaScript Arrays are passed by reference

Arrays are passed to functions by reference, or as a pointer to the original.

This means anything you do to the Array inside the function affects the original.

        var arr1 = ['hello']
        
        var arr2 = arr1;
        
        arr1 = ['world'];
        
        console.log(arr2);
        // ['hello']

##### Create an Array 

        var fruits = ['Apple', 'Banana'];

##### Add to the end of an Array

        var newFruits = fruits.push('Orange');
        // ["Apple", "Banana", "Orange"]

