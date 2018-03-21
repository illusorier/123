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