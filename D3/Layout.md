D3总共提供了12个布局

12个布局中，层级图(Hierarchy)不能直接使用，打包图是由层级图扩展而来的。

这些布局的作用都是将某种数据转换成另一种数据，而转换后的数据是利于可视化的。

If your data is already in a hierarchical format, such as JSON, you can pass it directly to `d3.hierarchy`.

`d3.hierarchy(data[,children])`

Constructs a root node from the specified hierarchical data.

The returned node and each descendant has the following properties:

- node.data - the associated data

- 

`pack(root)`

Lays out the specified root hierarchy, assigning the following properties on *root* and its descendants:

- node.x - 

You must call `root.sum` before passing the hierarchy to the pack layout.