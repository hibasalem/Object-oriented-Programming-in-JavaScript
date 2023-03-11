- What is Object-oriented Programming (OOP)?

Object-oriented programming (OOP) is a popular programming paradigm or style of programming. It’s been around since ‘70s, but unlike tools and frameworks that come and go, OOP is still very relevant today. That’s because it’s not a programming language or a tool. It’s a style of programming.

- Why learn OOP?

OOP helps you manage and reduce complexity in software by building re-usable building blocks (objects). Properly designed objects provide a simple interface and hide the unnecessary complexity from the outside,


- Object-oriented programming helps you:

  - Manage and reduce complexity
  - Eliminate redundant code
  - Build re-usable building blocks
  - Write cleaner code

----


// The simplest way to create an object is using an object literal 
```
const circle = { 
   radius: 1, 
   draw: function() {}
}; 
```
## factories 
To create multiple objects with the same structure and behaviuor (methods), use a factory or a constructor. 


is similar to constructor

instead of using new to create an object, factory functions simply set up and return the new object when you call the function.

```
const personFactory = (name, age) => {
  return {
    name, 
    age,
    sayHello : function(){
      console.log('hello!');
    } 
  };
};

const jeff = personFactory('jeff', 27);

```

## constructors  
we use it with new 

```
//Constructor
function User (name, age) {
  this.name = name;
  this.age = age;
}

var user1 = new User('Bob', 25);
var user2 = new User('Alice', 27);

```
```
class Polygon {
  constructor() {
    this.name = 'Polygon';
  }
}
```


Every object has a "constructor" property which returns the function that was used to construct or create that object.     
```
const x = {};  
x.constructor; // returns Object()   
```

In JavaScript, functions are objects. They have properties and methods. 
```
Circle.name; 
Circle.length;
Circle.constructor; // returns Function()
Circle.call({}, 1); // to call the Circle function 
Circle.apply({}, [1]);
```

## value vs reference types 

-Value types are copied by their value, reference types are copied by their reference. 
- Value types in JavaScript are: String, Number, Boolean, Symbol, undefined and null
- Reference types are: Object, Function and Array 


-------
JavaScript objects are dynamic. You can add/remove properties: 
```
circle.location = {};
circle['location'] = {};
                      
delete circle.location; 
```

To enumerate the members in an object: 
```
for (let key in circle) console.log(key, circle[key]);

Object.keys(circle); 
```

To see if an object has a given property
`if ('location' in circle)`

------------ 

## abstraction 
Abstraction means hiding the complexity/details and showing only the essentials. 

We can hide the details by using private members. Replace "this" with "let". 
```
function Circle(radius) { 
   // Public member 
   this.radius = radius; 

   // Private member                       
   let defaultLocation = {};                      
}    
```

To define a getter/setter, use `Object.defineProperty()`:
```
Object.defineProperty(this, 'defaultLocation', {
    get: function() { return defaultLocation; },
    set: function(value) { defaultLocation = value; }
});
```
