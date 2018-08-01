输入URL => 发起请求 => 解析HTML，生成DOM tree => 生成render tree =>

##### Rendering engines

Firefox, Chrome and Safari are built upon two rendering engines.

Firefox uses Gecko - a "home made" Mozilla rendering engine.

Both Safari and Chrome use Webkit.

Webkit is an open source rendering engine

The browser's main components are:

1. The user interface

2. The browser engine

3. The rendering engine - responsible for displaying the requested content. For example if the requested content is HTML, it is responsible for parsing the HTML and CSS and displaying the parsed content on the screen.

> It is important to note that Chrome, unlike most browsers, hold multiple instances of the rendering engine - one for each tab.

##### The main flow

The rendering engine will start getting the contents of the requested document from the networking layer.

After that this is the basic flow of the rendering engine:

![](../assets/browser-flow.png)
 
![](../assets/browser-webkitflow.png)
 
### Reflows and Repaints
 
用脚本进行DOM操作的代价很昂贵。
  
有个贴切的比喻，把DOM和ECMAScript各自想象为一个岛屿，它们之间用收费桥粱连接，ECMAScript每次访问DOM，都要途径这座桥，并交纳“过桥费”。

浏览器下载完页面中的所有组件—HTML，JavaScript、CSS和图片等资源后会解析生成两个内部数据结构-DOM树和渲染树。

## Browser Script Loading

Today newer browsers support the ability to download scripts in parallel.

The scripts are still executed in the order they are declared.

scripts won't execute until the previous script or stylesheet has executed. 

The browser blocks further rendering of the page while all this is happening.

This is why the great and the good of the performance world recommend putting script elements at the end of your document, as it blocks as little content as possible.

console.time()

console.timeEnd()

Render-tree Construction

The CSSOM and DOM trees are combined into a render tree, which is then used to compute the layout of each visible element

Reflow is the name of the web browser process for re-calculating the positions and geometries of elements in the document,

Because reflow is a user-blocking operation in the browser, it is useful for developers to understand how to improve reflow time 

Sometimes reflowing a single element in the document 

当DOM的变化影响了元素的

完成重排后，浏览器会重新绘制受影响的

每次重排必然会导致重绘，那么，重排会在哪些情况下发送？

- 添加或者删除可见的DOM元素
- 元素位置改变
- 元素尺寸改变
- 元素内容改变
- 页面渲染初始化

`DocumentFragments` are DOM Nodes.

They are never part of the main DOM tree.

The usual use case is to create the document fragment, append elements to the document fragment and then append the document fragment to the DOM tree.

