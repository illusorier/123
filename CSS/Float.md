浮动

A float is a box that is shifted to the left or right on the current line.

把浮动元素也当作一个盒子来看待。

浮动元素或者说浮动盒子会脱离普通文档流。

In the float model, a box is first laid out according to the normal flow, then taken out of the flow and shifted to the left or right as far as possible.

If there is a line 

当一个元素的float属性被设置为非none时，其临近的元素根据其类型（行内还是块级），会有不同的反应。

Since a float is not in the flow, non-positioned block boxes created before and after the float box flow vertically as if the float did not exist.

