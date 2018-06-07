## Regular Expressions

什么是正则表达式？

Regular expression are extremely useful in extracting information from text such as code, log files, or even documents.

We are writing patterns to match a specific sequence of characters.

Regular expressions are patterns used to match character combination in strings.

正则是用来匹配字符串中模式(特定的字符组合)的。

In JavaScript, regular expressions are also objects.

在JS中，正则也是对象。

These patterns are used with the `exec` and `test` methods of `RegExp`, and with the `match`, `replace`, `search`, 

### Creating a regular expression

You construct a regular expression in one of two ways:

正则表达式字面量

Using a regular expression literal, which consists of a pattern enclosed between slashes, as follows:

        var re = /ab+c/;
    
Or calling the constructor function of the `RegExp` object, as follows:

        var re = new RegExp('ab+c');

### Writing a regular expression pattern

正则表达式模式

A regular expression pattern is composed of simple characters, such as `/abc/`, or a combination of simple and special characters, such as `/ab*c/`

#### Using simple patterns

最简单的正则表达式是特定字符组合的匹配，比如我们想知道某字符串中是否存在hello：

    let myRe = /hello/;
    
    function hashello(str) {
      if(str.search(myRe) !== -1) {
        return true;
      } else {
        return false;
      }
    }

Simple patterns are constructed of characters for which you want to find a direct match.
 
For example, the pattern `/abc/` matches the character combinations in strings only when exactly the characters 'abc' occur together and in that order.

这种模式十分严格，很多时候我们

#### Using special characters

When the search for a match requires something more than a direct match, 

- `\ `: A backslash(反斜线) that precedes a special character indicates that the next character is not special and should be interpreted literally.

- `^`: Matches beginning of input. For example, `/^A/` does not match the 'A' in 'an A', but does match the 'A' in 'An E'

- `+`: 

- `\d`: Matches a digit character.

- `.`: (The decimal point) matches any single character except the newline character.

You may notice that this actually overrides the matching of the period character, so 

##### Using parentheses

如何使用正则表达式

Regular expressions are used with 

RegExp



