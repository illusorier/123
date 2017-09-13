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