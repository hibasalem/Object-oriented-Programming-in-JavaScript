# modularity  
- maintainability 
- reuse
- abstract 

# Module formats
 - AMD / Asynchronous Module Definition (Browser)
 - CommonJS (Node)
 - UMD / Universal Module Definition (Browser + Node)
 - ES6 Modules 

-----------
## CommonJS (Used in Node)

- Exporting 
`module.exports.Cirlce = Circle; `
- Importing 
`const Circle = require('./circle');`

```js
// circle.js 
// Implementation Detail 
const _radius = new WeakMap();

// Public Interface
class Circle {
  constructor(radius) {
    _radius.set(this, radius);
  }

  draw() {
    console.log('Circle with radius ' + _radius.get(this));
  }
}

module.exports = Circle;
```
```js
// index.js 
const Circle = require('./circle');

const c = new Circle(10);
c.draw();
```
--------------

## ES6 Modules (Used in Browser)
- Exporting
`export class Square {}`
- Importing 
`import {Square} from './square'; `


```js
// circle.js 
const _radius = new WeakMap();

export class Circle {
  constructor(radius) {
    _radius.set(this, radius);
  }

  draw() {
    console.log('Circle with radius ' + _radius.get(this));
  }
}
```

```js
// index.js 
import {Circle} from './circle.js';

const c = new Circle(10);
c.draw();
```
---------
- ***transpiler*** is translator + compiler ( modern js to es5  for example)
- We use ***Babel*** to transpile our modern JavaScript code into code that browsers can understand (typically ES5). 

- ***bundler*** 
- We use ***Webpack*** to combine our JavaScript files into a bundle.

---------
