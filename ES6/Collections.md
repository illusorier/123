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
        
The two objects `x` and `y` both stringify to `"[object Object]"`, so only that one key is being set in `m`.
        
As of ES6, just use `Map(..)`:

        let m = new Map();
        
        let x = { id: 1 },
        let y = { id: 2 };
                    
        m.set(x, "foo");
        m.set(y, "bar");
        
        m.get(x); // "foo"
        m.get(y); // "bar"
        
        
The only drawback is that you can not use `[]` bracket access syntax for setting and retrieving values.

But `get(..)` and `set(..)` work perfectly suitably instead.

To delete an element from a map, do not use the `delete` operator, but instead use the `delete(..)` method:

        m.delete(y)
        
You can clear the entire map's contents with `clear()`. 
        
## Set

A set is a collection of unique values(duplicates are ignored).

