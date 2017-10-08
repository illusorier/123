什么是正则表达式？

Regular expression are extremely useful in extracting information from text such as code, log files, or even documents.

We are writing patterns to match a specific sequence of characters.

Regular expressions are patterns used to match character combination in strings.

In JavaScript, regular expressions are also objects.

These patterns are used with the ``

#### Creating a regular expression

You construct a regular expression in one of two ways:

正则表达式字面量由包含在两个左斜杠之中模式组成。

Using a regular expression literal, which consists of a pattern enclosed between slashes, as follows:

    var re = /ab+c/;

#### Writing a regular expression pattern

##### Using special characters

- `\ `: A backslash that precedes a 

- `+`: 

- `\d`: Matches a digit character.

- `.`: (The decimal point) matches any single character except the newline character.

You may notice that this actually overrides the matching of the period character, so 

##### Using parentheses

