What is an algorithm and why should we care?

什么是算法？

Algorithms are steps of how to do some tasks.

There are "good" and "bad" algorithms.

The good ones are fast; the bad ones are slow.

时间复杂度

Time complexity (or running time) is the estimated time an algorithm tasks to run.

时间复杂度通过一个自变量为

However, you do not measure time complexity in seconds, but as a **function** of the input.

The **time complexity** is expressed as a function of the input.

The **time complexity** is not about timing how long the algorithm takes.

Instead, how many operations are executed.

Why is that the time complexity is expressed as a function of the input? 

By, the 

查找算法 排序算法 

算法的五大特征

输入(Input)：一个算法有零个或多个输入，以刻画运算对象的初始情况，所谓零个输入是指算法本身给定了初始条件。

输出(Output)：一个算法有一个或多个输出，没有输出的算法毫无意义。

如何确定某个值是否存在于某个数组中？

线性查找和二分查找都可以完成该任务。

有哪些角度可以用来分析某个算法，如何对这两个不同的算法进行比较？

The running time of an algorithm depends on how long it takes a computer to run the lines of code of the algorithm - and that depends on the speed of the computer, the programming language, and the compiler that translates the program from the programming language into code that runs directly on the computer, among other factors.

也就是说，实际决定一个算法运行时间的因素有很多，因此我们不能仅仅根据某算法在某台计算机上的运行时间就决定其性能。

We think about the running time of an algorithm as a function of its input.

也就是说我们可以用一个函数来描述该算法运行时间随输入值变化而变化。

How fast a function grows with the input size.

The rate of growth of the running time.

然后我们通过该函数来分析算法的性能，比如其运行时间随输入数量的增长率如何。

数学定义：如果存在正常数c和n0,使得当N大于等于n0时，T(n)小于等于cf(N),则记为T(N) = O(f(N))。

By dropping the less significant

在进行算法分析时，我们常常会丢掉低阶项，因为低阶项的增长率较低，不会影响到该函数与其他函数的相对级别。

Big O notation is used in Computer Science to describe the performance or complexity of an algorithm.

我们可以

大O算法中的n到底代表什么？
 
O(1) describes an algorithm that will always execute in the same time (or space)  

空间复杂度

Space complexity of an algorithm represents the amount of memory space required by the algorithm in its life cycle.

时间复杂度

In both cases, the time complexity is generally expressed as a function of the size of the input.

An algorithm is said to **constant time** (also written as **O(1)** time) if the value of *T(n)* is bounded by a value that does not depend on the size of the input.

Sometimes, we want to say that an algorithm takes at least a centain amount of time, big-Ω 

    function sum(n) {
      int partialSum;
      
      partialSum = 0;


给定两个函数，通常存在一些点，在这些点上一个函数的值小于另一个函数的值，在另一些点上，一个函数的值大于另一个函数的值。


冒泡排序

排序标准

Bubble Sort is the simplest sorting algorithm that works by repeatedly swapping the adjacent elements if they are in wrong order.   

5 4 3 2 1

4 5 3 2 1

4 3 5 2 1

4 3 2 5 1

4 3 2 1 5