# classes 
old syntax 
```js
function Circle(){
  // instance member
  this.radius = radius;
  
  // instance member
  this.move = function () {
    // ...
  }
}
```
classes syntax

```js
class Circle {
    constructor(radius) {
        this.radius = radius; 
    }

    // These methods will be added to the prototype.  which is available in the instance 
    draw() {
    }

    // This will be available on the Circle class (Circle.parse())
    static parse(str) {
    }
}

we can use `Circle.parse` any where 
```
--------------

- private members (abstraction)

Using symbols to implement private properties and methods

```js
const _size = Symbol();
const _draw = Symbol(); 
// each symbol is different  Symbol() === Symbol() // false 
```
```js
class Square {
    constructor(size) {
        // "Kind of" private property 
        this[_size] = size; 
    }

    // "Kind of" private method 
    [_draw]() {
    }

    // By "kind of" I mean: these properties and methods are essentally
    // part of the object and are accessible from the outside. But accessing
    // them is hard and awkward. 
}
```

- using WeakMaps to implement private properties and methods
const _width = new WeakMap();
```js
class Rectangle {
    constructor(width) {
        _width.set(this, width);
    }

    draw() {
        console.log('Rectangle with width' + _width.get(this));
    }
}
```
WeakMaps give us better protection than symbols. There is no way to access private members implemented using WeakMaps from the outside of an object. 


---------
-  Inheritance 
class Triangle extends Shape {
    constructor(color) {
        // To call the base constructor 
        super(color);
    }

    draw() {
        // Call the base method 
        super.draw();

        // Do some other stuff here
    }
}