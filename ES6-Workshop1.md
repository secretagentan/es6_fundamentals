# ES6-Workshop1

## Proper Tail Calls, VAR vs. LET vs. CONST, and Rest Parameters

**Proper tail recursion is a property of the asymptotic complexity of a language's runtime behavior. That is, in improperly tail recursive languages..."**
      -- Dave Herman(PR@Mozilla)

GROK THAT ^^

```javascript
function foo(num) {
  try{
    return foo((num||0) +1);
  }
  catch(e){return num;}
}

console.log(foo())
```

## Proper Tail Calls

```javascript
function greet() {
  return "Hello";  
  //last instruction to fire before return
}
```

```javascript
function greet() {
  return getSal()  
  //last instruction to fire before return
}

function getSal() {
  return "Hello";
}
```
Apparently this should work in ES6, does it?

```javascript
function fibonacci(x, y, limit, index) {
  if(arguments.length == 1) {
    if(x) 
      return fibonacci(0,1,x,1);
    
    return 0;
     }else{
      if(index<limit) {
        return fibonacci(y, (x+y), limit, ++index);
      }
      return y;
     }
}

console.log(fibonacci(12465));
```
### CONST, LET, and Blocks
"Don't grep-replace "var" with "let" or you will break the internet"
        - Yoda Crockford

The 'var' way is different than 'let' way! code will run different

## Variable Hoisting
PAUSE READ DIGEST

```javascript
function outer() {
  a = 0;
  inner();


  function inner() {
     b = 2;
  }
}

outer();
```
PAUSE READ DIGEST

```javascript
var foo = 2;

if(true) {
  var bar = 1;
}

console.log(foo+bar);

```
## Function Hoisting

PAUSE READ DIGEST

```javascript
function foo() {
  //code goes here
}

var bar = function() {
  //code goes here
}
```

## LET

```javascript
var foo = 1;
let foo = 2;

foo = 3
```

PAUSE READ DIGEST

```javascript
let foo = 2;

if(true) {
  let bar = 1;
}

console.log(foo + bar);
// "bar is undefined"
// "foo has already been declared"
```
```javascript
let a = 2;

if(true) {
  let a = 1;
  console.log(a);
}

console.log(a);
```

**WHAT IS A TEMPORAL DEAD ZONE"**

PAUSE READ DIGEST

```javascript
function doSomething() {
  console.log(a);
  
  let a = 1;
  // console.log(a);
}

doSomething()
```
## CONST

```javascript
const a = 0;

a = 1;
```

## BLOCK FUNCTIONS

```javascript
function doThat() {
  if(true) {
    let a = 0;
  }
  //console.log(a);
}

doThat()
// a is undefined 
```

## ...rest OPERATOR

PAUSE READ DIGEST

```javascript
function doThat(...bar) {

  console.log(bar.join(' '));
}

doThat('I', 'can', 'dance');
// logs "I can dance" 
```
WHAT! is this an 'arguments' object?

```javascript
function foo() {
  var output = "";
  
  for (var i = 0; i< arguments.length; i++) {
    output += arguments[i];
  }
  
  console.log(output);
}

foo('I ', 'can ', 'haz ', 'teh ', 'arguments');
```
NO -- 

PAUSE READ DIGEST

```javascript
function argumentSample(name){
  console.log(name, arguments);
}

function restSample(name, ...other) {
  console.log(name, other);
}

argumentSample('Boshika', "Tara", 'San Francisco', 'California');
// Boshika ["Boshika", "Tara", "San Francisco", "California"]

restSample('Boshika', "Tara", 'San Francisco', 'California');
// Boshika ["Tara", "San Francisco", "California"]

```

## Mo' Rulz

```javascript
function wayToManyArgs(...first, ...second) {
  console.log("First: " + first.join(" "));
  console.log("Second: " + second.join(" "));
}

wayToManyArgs("what", "is", "this", "does", "this", "make", "sense");
// Uncaught SyntaxError: Rest parameter must be **last** formal parameter
```

```javascript
function wayToManyArgs(...first, second) {
  console.log("First: " + first.join(" ") + second);
}

wayToManyArgs("what", "is", "this", "does", "this", "make", "sense");
// Uncaught SyntaxError: Rest parameter must be last formal parameter
```

```javascript
function wayToManyArgs(second, ...first) {
  console.log("Second: " + second + "\nFirst: " + first.join(" "));
}

wayToManyArgs("what", "is", "this", "does", "this", "make", "sense");
// "Second: what"
// "First: is this does this make sense"
```

```js
function wayToManyArgs(second, third, fourth, ...first) {
  console.log("Second: " + second + "\nThird: " + third + "\nFourth: " + fourth + "\nFirst: " + first.join(" "));
}

wayToManyArgs("what", "is", "this", "does", "this", "make", "sense");
// Second: what
// Third: is
// Fourth: this
// First: does this make sense
```



