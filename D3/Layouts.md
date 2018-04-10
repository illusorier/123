D3 layout help you create more advanced visualisations.

D3总共提供了12个布局

12个布局中，层级图(Hierarchy)不能直接使用，集群图(Cluster)、树状图、矩阵树图、分区图和打包图(Pack)是由层级图扩展而来的。

布局不是要直接绘图，而是为了得到绘图所需的数据。

这些布局的作用都是将某种数据转换成另一种数据，而转换后的数据是利于可视化的。

In essence a layout is just a **JavaScript function** that takes your data as input and adds visual variables such as position and size to it.

初始数据先写在一个JSON文件中，再用D3来读取。

A `d3.hierarchy` object is a data structure that represents a hierarchy.

It has a number of functions defined on it for retrieving things like ancestor, descendant and leaf nodes and for computing the path between nodes.

It can be created from a nested JavaScript object such as:

        {
          "name": "Eve",
          "children": [
            {
              "name": "Seth",
              "children": [
                {
                  "name": "Noam"
                }
              ]
            }
          ]
        }
        
API: `d3.hierarchy(data[,children])`

If your data is already in a hierarchical format, such as JSON, you can pass it directly to `d3.hierarchy`; otherwise,

The specified children accessor function is invoked for each datum, 

也就是说，数据不一定要完全符合上面这个例子的结构。

The returned node and each descendant has the following properties:

- node.data - the associated data

- node.value - the summed value of the node and its descendants; optional.

You must call `node.sum` or `node.count` before invoking a hierarchical layout that requires `node.value`.

## Cluster

集群图

The cluster layout produces dendrograms 

## Pack

`pack(root)`

Lays out the specified root hierarchy, assigning the following properties on *root* and its descendants:

- node.x - 

You must call `root.sum` before passing the hierarchy to the pack layout.