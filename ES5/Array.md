Using forEach makes this code a little shorter, but there are other more important reasons why it is often a better choice.

        myString
            .split(",")
            .fiter(function() {})
            .map(function() {})
            .reduce(function() {})
            
This style of programming