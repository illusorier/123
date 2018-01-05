实际的页面中，类似table和ul标签中所需要呈现的数据往往保存在数组中，因此有关数组的算法十分重要。

场景1：删除某一行数据

Array.prototype.splice()

The `splice()` method changes the contents of an array

        var myFish = ['angel', 'clown', 'mandarin', 'sturgeon'];
        
        myFish.splice(2, 1); // remove 1 item at 2-index position (that is, "drum")
        // myFish is ["angel", "clown", "mandarin", "sturgeon"]
        
场景2：在某处插入数据

        var myFish = ['angel', 'clown', 'mandarin', 'sturgeon'];
                
        myFish.splice(2, 0, 'drum'); // insert 'drum' at 2-index position
        // myFish is ["angel", "clown", "drum", "mandarin", "sturgeon"]
        
场景3：是否有重复数据？

