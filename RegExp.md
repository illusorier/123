## Regular Expressions

什么是正则表达式？

Regular expression are extremely useful in extracting information from text such as code, log files, or even documents.

We are writing patterns to match a specific sequence of characters.

Regular expressions are patterns used to match character combination in strings.

正则是用来匹配字符串中模式(特定的字符组合)的。

In JavaScript, regular expressions are also objects.

在JS中，正则也是对象。

These patterns are used with the `exec` and `test` methods of `RegExp`, 

### Creating a regular expression

You construct a regular expression in one of two ways:

正则表达式字面量

Using a regular expression literal, which consists of a pattern enclosed between slashes, as follows:

        var re = /ab+c/;
    
Or calling the constructor function of the `RegExp` object, as follows:

        var re = new RegExp('ab+c');

### Writing a regular expression pattern

模式

A regular expression pattern is composed of simple characters, such as `/abc/`, or a combination of simple and special characters, such as `/ab*c/`

#### Using simple patterns

Simple patterns are constructed of 

#### Using special characters

When the search for a match requires something more than a direct match, 

- `\ `: A backslash that precedes a 

- `+`: 

- `\d`: Matches a digit character.

- `.`: (The decimal point) matches any single character except the newline character.

You may notice that this actually overrides the matching of the period character, so 

##### Using parentheses

