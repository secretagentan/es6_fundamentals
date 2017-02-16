# ES6-Workshop2

## Spread Operator, Destructuring and Arrow functions

---
### Spread Operator
PAUSE READ DIGEST

```javascript
var nums = [1,2,3];

console.log(nums);
console.log(...nums);
```

```javascript
function returnTwo(a,b) {
  return [b,a];
}
var a = [1,2,3];
var b = returnTwo(a[0], a[1]);
var c = returnTwo(...a);
```
### Combine arrays

```javascript
let nums = [1,2,3];
let abcs = ['a', 'b', 'c'];

let alphanum = [...nums, ...abcs];
```

### Return Values

```javascript
function getNums() {
  return [1,2,3];
}

var b = [0, ...getNums()];
console.log(b);
```

### Destructuring

**Destructuring allows you to bind a set of variables to a corresponding
set of values anywhere that you can normally bind a value to a single 
variable**

What are we trying to destructure, when it comes to objects and arrays?

Two Approaches 
  - Destructuring Objects
  - Destructuring Arrays

```javascript
let address = {
  city: 'Los Angeles',
  state: 'California',
  zip: 90027
};

let {city: c, state: s, zip: z} = address;

console.log(c, s, z);

```

```javascript
var living = {name: 'Tree', age: '350'};
displayLiving(living);

function displayLiving(l) {
  var name = l.name;
  var age = l.age;
  
  return name + age;
}
```

```javascript
let living = {name: 'Tree', age: '350'};
displayLiving(living);

function displayLiving(l) {
  let {name, age} = l;
  
  return name + age;
}
```

```javascript
let living = {name: 'Tree', age: '350'};
displayLiving(living);

function displayLiving({name, age}) {
  return name + age;
}
```
---

