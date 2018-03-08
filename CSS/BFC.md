    
    
    <div class="outer">
      <div class="float">I am a floated elemen.</div>
      I am text inside the outer box.
    </div>
    
我们给outer设置一个可见的border，接下来可能会出现两种可能性，假如文字较少，图片较高，边框会浮于图片之上，反之文字、边框都会环绕图片。

There are two ways in which we ordinarily fix this layout problem.

Using any value other than the initial value of `visible` creates a Block Formatting Context, and 

In addition to using `overflow` to create a BFC, some other CSS properties create a BFC.

Flex and Grid items also create something like a BFC, except they are described as a **Flex Formatting Context** and **Grid Formatting Context** respectively.