### Classes

`class`

At the heart of the new ES6 class mechanism is the `class` keyword,which identifies a block where the contents define the members of a function's prototype.

    class Foo {
      constructor(a,b) {
        this.x = a;
        this.y = b;
      }
      
      gimmeXY() {
        return this.x * this.y;
      }
    }

- `class Foo` implies creating a (special) function of the name

`extends` and `super`

ES6 classes also have syntactic sugar

    class Bar extends Foo {
      constructor(a,b,c) {
        super(a,b);
        this.z = c;
        
        
        
In constructor, `super` automatically refer to the "parent constructor".In a method

Class的静态方法

The **static** keyword defines a static method for a class.