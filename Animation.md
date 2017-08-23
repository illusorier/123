三种为HTML文档应用简单特殊效果的方式的方式:过渡、动画和变换。

这三种特性都是在CSS3中新添加的。

过渡效果一般由浏览器直接改变元素的CSS属性实现。

例如，如果使用:hover选择器，一旦用户将鼠标悬停在元素之上，浏览器就会应用跟选择器关联的属性。

创建简单的过渡:

> 刚开始布局页面时浏览器不会应用过渡。

CSS includes several properties that transform a web page element, by either rotating it,scaling it,moving it,or skewing it.

The basic CSS property to 

## Transform

- `scale()`: affects the size of the element

## Transitions

While transforms can be fun (especially the rotate function), they really bring your page to life when coupled with a CSS transition.

A transition is simply an animation from one set of CSS properties to another set over a specific amount of time.

To make a transition work, you need a few things in place:

- **Two styles**. One style represents the beginning look of the element, while the second style is the ending look. The web browser will take care of the process of animating the change between the two styles.

- **The transition property**. CSS adds the transition property. In general, you apply the transition property to the original style, the style that defines the look of an element before the animation begins.

- **A trigger**. The trigger is the action that causes the change between the two styles.

A web browser can't animate every single CSS property, but you still have a long list of properties to choose from.

#### Adding a Transition

At the heart of CSS transitions are four properties that control which properties to animate, how long the animation takes, the type of animation used, and an optional delay before the animation begins.

## Animation


The `animation` property in CSS can be used to animate many other CSS properties such as color, background-color,height,or width.

#### Sub-properties
- `animation-name`
- `animation-duration`: the length of time it takes for an animation to complete one cycle.
- `animation-timing-function`: 
- 

#### Performance

# Transition
The `transition` property is a shorthand property used to represent up to four transition-related longhand properties:

    .example {
      transition: [transition-property] [transition-duration] [transition-timing-function] [transition-delay];
      
The `transition-timing-function` property,normally used as part of `transition` shorthand,is used to define 