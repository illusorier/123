Vue中模块的书写方法、理念与AngularJS是非常相似的。

与React不同的是，它们仍然需要书写HTML，类似于模板引擎，可以理解为对HTML的一种扩展。

这种扩展主要提现在两个方面：

- 自定义的attribute
- 节点的innerText的特殊写法

Mustaches cannot be used inside HTML attributes.

Instead, use a **v-bind directive**.

这是与AngularJS的一点不同。