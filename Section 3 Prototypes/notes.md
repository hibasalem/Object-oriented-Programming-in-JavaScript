## classical inheritances vs prototypical   
- inheritance is a mechanism for using the interface and implementation of one or more classes as the basis for another class. The inheriting class, also known as a subclass, inherits from one or more classes, known as superclasses
  ```
  base/super/parent 
      shape 

      circle      
  derived/sub/child 

  circle is a shape 
  ```

- Prototypical inheritance allows us to reuse the properties or methods from one JavaScript object to another through a reference pointer function.

- `__proto__ property`   
In Javascript, every object has its own hidden, internal property, [[Prototype]]. We can access that [[Prototype]] using the __proto__ property. This calls the program to mark the template object as a hidden type. JavaScript objects must be linked to this prototype object. Now, an object’s properties can be accessed by the inheritor object.   

- Using `hasOwnProperty`, we can test if an object contains a certain prototype property; the method will return true or false depending. This will help you clarify if an object has its own property or if it is inheriting instead. 
```js
obj.hasOwnProperty(prop)
```

- Every object (except the root object) has a prototype (parent). 
- To get the prototype of an object:
`Object.getPrototypeOf(obj);`

- In Chrome, you can inspect "__proto__" property. But you should not use that in the code. 

- Prototypal inheritance uses the concept of ***prototype chaining***. Let’s explore that concept. Every object created contains [[Prototype]], which points either to another object or null. Envision an object C with a [[Prototype]] property that points to object B. Object B’s [[Prototype]] property points to prototype object A. This continues onward, forming a kind of chain called the prototype chain.

-----------
- Constructors have a "prototype" property. It returns the object 
- that will be used as the prototype for objects created by the constructor. 
```js
Object.prototype === Object.getPrototypeOf({})
Array.prototype === Object.getPrototypeOf([])
```

- All objects created with the same constructor will have the same prototype. 
- A single instance of this prototype will be stored in the memory. 
```js
const x = {};
const y = {};
Object.getPrototypeOf(x) === Object.getPrototypeOf(y); // returns true 
```
------------
- To get the attributes of a property property descriptor 
Object.getOwnPropertyDescriptor(obj, 'propertyName');
 
```js
let person = {name : 'aa'}
let objectBase = Object.getPrototypeOf(person)
let descriptor = Object.getOwnPropertyDescriptor(objectBase , 'tosSrting')
```
this will get us some properties  

```
{
  "writable": true,  // we can overwrite it 
  "enumerable": false, // we cant iterate over it 
  "configurable": true // we can delete it 
}
```

we can set those attributes when creating our own objects 
```
Object.defineProperty(person , 'name', {
  "writable": false, // read only 
  "enumerable": false, // we cant iterate over it 
  "configurable": true // we can delete it 
})
```
--------
- Any changes to the prototype will be immediately visible to all objects referencing this prototype. 

- When dealing with large number of objects, it's better to put their  methods on their prototype. This way, a single instance of the methods will be in the memory.     
```js
// prototype 
Circle.prototype.draw = function() {}

function Circle(){
  // instance member
  this.radius = radius;
  
  // instance member
  this.move = function () {
    // ...
  }
}
```
- To get the own/instance properties:
Object.keys(obj);

- To get all the properties (own + prototype): 
for (let key in obj) {}

-------
- dont modify objects that you dont own like the array 

```js
// bad practice 
Array.prototype.Shuffle = function() {}
``` 
-------
