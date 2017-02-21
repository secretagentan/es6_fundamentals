# ES6-Workshop2

## Spread Operator And Destructuring 

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
first
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

PAUSE READ DIGEST

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

```javascript
let living = {name: 'Tree', age: '350'};
let someVar = 20;
displayLiving(someVar, living);

function displayLiving(x, {name, age}) {
  return name + age + 'Here is someVar: ' + x;
}
```
PAUSE READ DIGEST

```javascript
let person = {
    name: 'Gabriel García Márquez',
    age: 87,
    address : {
        city: 'Bogotá',
        state: 'Cundinamarca',
        country: 'Colombia'
    }
}

let {name, age, address: {city, state, country}} = person;
```
### ARRAY Destructuring

```javascript
let nums = [1,2,3];

let [first, second, third] = nums;
console.log(first);
// => 1

```

```javascript
var a = 1; var b =2;

//old way
var temp = a; a=b; b = temp;

//new way
[b,a] = [a,b];

console.log([a,b])
// => [2,1]
```

```javascript
let nums = [1,2,3,4];
doSomething(nums);

function doSomething([first, second, ...others]){
// '...others' is a spread operator (not rest)
// because it's in the array and not a param
    console.log(first);
    console.log(second);
    console.log(others);
}
```

```javascript
var nums = [1,2,[3,4,[5,6]]];

var[one,,[three,,[,six]]] = nums;

console.log(one);
// => 1

console.log(three);
// => 3

console.log(six);
// => 6
```

### PRACTICE

Use the ...rest operator

```js
var someArray = ['A', 'B', 'C', 'D', 'E'];

var fn7 = ([first, second, ...rest]) => {
    // let [first, second, ...rest] = someArray;
    //console.log goes here
    console.log(first);
    console.log(second);
    console.log(rest);
}

fn7(someArray);

//Output
"A"
"B"
["C", "D", "E"]
```

object destructuring

```js
let node = { 
    type: "Identifier", 
    name: "foo" 
};

let {type, name} = node;

console.log(type);
// => Identifier
console.log(name);
// => foo

```
```js
let node = { 
    type: "Identifier", 
    name: "foo", 
    loc: { 
        start: { 
            line: 1, 
            column: 1 
        }, 
        end: { 
            line: 1,
            column: 4 
            }
    } 
};

let {type: t, name: n, loc: {start: {line: l1, column: c1}, end: {line: l2, column: c2}}} of node;

console.log(start);

```
array destructuring

```js
let colors = [ "red", [ "green", "lightgreen" ], "blue" ];

let [first, [second, third], fourth] = colors;

console.log(first);
// => red
console.log(second);
// => green
console.log(third);
// => lightgreen
console.log(fourth);
// => blue

```

### Challenge

Mixed Destructuring

```js
let node = { 
    type: "Identifier", 
    name: "foo", 
    loc: { 
        start: { 
            line: 1, 
            column: 1 
        }, 
        end: { 
            line: 1, 
            column: 4 
        } 
    },
    range: [0, 3] 
};
```
---

