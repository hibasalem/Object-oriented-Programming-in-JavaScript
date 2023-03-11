# prototypical inheritance

## creating our own prototypical inheritance

```js
function Shape() {}
function Circle() {}
```
- create object that inherits from shape 
- circle inherits from shape and shape inherits from the objects root

```js
Circle.prototype = Object.create(Shape.prototype);
//the best practice is to whenever we reset the prototype we should set the constructor , this is related to using the new operator 
Circle.prototype.constructor = Circle;
```

## calling the super constructor 

```js
function Rectangle(color) {
  // To call the super constructor , so the new Rectangle can have the   color property from the shape 
  Shape.call(this, color);
} 
```
## Method overriding 

```js
Shape.prototype.draw = function() {}
Circle.prototype.draw = function() {
    // Call the base implementation using call this 
    Shape.prototype.draw.call(this);

    // Do additional stuff here 
}
```

## polymorphism 
describes situations in which something occurs in several different forms. In computer science, it describes the concept that you can access objects of different types through the same interface.
 

-------------

- Don't create large inheritance ***hierarchies***. 
- One level of inheritance is fine. 
- favor composition over inheritance

## mixin 
Use mixins to combine multiple objects and implement ***composition*** in JavaScript. 

```js
const canEat = { 
  eat: function() {}
};

const canWalk = {
  walk: function() {}
};

function mixin(target, ...sources) {
  // Copies all the properties from all the source objects to the target object. 
  Object.assign(target, ...sources);
}

function Person() {}

mixin(Person.prototype, canEat, canWalk);
```
