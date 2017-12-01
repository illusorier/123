## Map

Objects are the primary mechanism for creating unordered key/value-pair data structures.

The major drawback with objects-as-maps is the inability to use a non-string value as the key.

对象的属性名必须是字符串。

        var m = {};
        
        var x = { id: 1 },
            y = { id: 2 };
        
        m[x] = "foo";
        m[y] = "bar";
        
        m[x];	// "bar"
        m[y];	// "bar"
        
## Set

A set is a collection of unique values.