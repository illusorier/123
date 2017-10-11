##### Rendering engines

Firefox, Chrome and Safari are built upon two rendering engines.

Firefox uses Gecko - a "home made" Mozilla rendering engine.

Both Safari and Chrome use Webkit.

Webkit is an open source rendering engine

##### The main flow

The rendering engine 

![](./assets/browser-flow.png)
 
![](./assets/browser-webkitflow.png)
 
### Reflows and Repaints
 
 用脚本进行DOM操作的代价很昂贵。
  
有个贴切的比喻，把DOM和ECMAScript各自想象为一个岛屿，它们之间用收费桥粱连接，ECMAScript每次访问DOM，都要途径这座桥，并交纳“过桥费”。

console.time()

console.timeEnd()