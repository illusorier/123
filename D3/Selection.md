Selections allow powerful data-driven transformation of the document object model(DOM):

选择集

Selection methods come in two forms: select and selectAll:

the former selects only the first matching element, while the latter selects all matching elements in document order.

`d3.select(selector)`

Selects the first element that matches the specified selector string.

If no elements match the selector, returns an empty selection.

`d3.selectAll(selector)`

调用这两个函数后，返回的结果为选择集。

After selecting elements, use the selection's transformation methods to affect document content.

`selection.text(value)`

If a *value* is specified, sets the text content to the specified value on all selected elements.

If the *value* is a function, it is evaluated for each selected element, in order, being passed the current datum(d), the current index(i), and the current group(nodes), with this as the current DOM element(node[i]).
 
The function's return value is then used to set each element's text content.

`selection.append(type)`

在选择集末尾插入元素

`selection.data(data[,key])`

绑定一个数组到选择集上，数组各项的值分别与选择集的各元素绑定

Joins the specified array of *data* with the selected element, returning a new selection that represents the *update* selection: the elements successfully bound to data.

The specified *data* is an array of arbitrary values (e.g., numbers or objects), or a function that returns an array of values for each group.

If a *key* function is not specified, then the first datum in *data* is assigned to the first selected element.

当数组data中的元素数量与选择集中的元素数量不一致时？

`selection.enter()`

Returns the enter selection: placeholder nodes for each datum that had no corresponding DOM element in the selection.(The enter selection is empty for selections not returned by *selection.data*.)
  
The enter selection is typically used to create "missing" elements corresponding to new data.

当数据比选择集中的元素多时，需要用到enter，会创建新的元素并和相应的数据进行绑定，这一部分就称为enter，然后需用append插入到文档中。