Lexical environments - a mechanism used in some languages to manage the static scoping.

Lexical environments was introduced in ECMA-262-5 specifications,though this is an independent from ECMAScript theoretical concept which is used in many languages.

lexical environments与变量对象等概念的关系？

Strictly speaking,lexical environments in this case are just more theoretically suited and more highly-abstracted replacement of the previous ES3 concepts.

Since ES5 era,in discussions and explanations of ECMAScript,I recommend to use exactly these new definitions.

Though,more generic concepts,such as an activation record(which is an activation object in ES3) of a call-stack(which is an execution context stack in ES)


Scope

Typically,scope is used to manage the visibility and accessibility of variables from different parts of a program.

Static(lexical) scope 词法作用域

The word "static"

Always the nearest lexical scope containing the variable is considered.The own scope has the highest priority and is considered the first.

Resolution of an identifier is independent from the environment of a caller.

