## ECMAScript 6

A `transpiler` takes ES6 source code and generates ES5 code that can run in every browser - e.g. Traceur or Babeljs.

### let

In pretty much any other languages, a variable is declared where the declaration is done. But in JS, there is a concept, called `hoisting`, which actually declares a variable at the top of the function, even if you declared it later. [See more](http://www.w3schools.com/js/js_hoisting.asp)

By using `let` the variable `name`﻿ is now restricted to its block.

```
function getPonyFullName(pony) {
  if (pony.isChampion) {
    let name = 'Champion ' + pony.name;
    return name;
  }
  // name is not accessible here
  return pony.name;
}
```

### Constants

When you declare a variable with const﻿, it has to be initialized and you can’t assign another value later.

```
const PONIES_IN_RACE = 6;
```

### Creating objects

Example:

```
function createPony() {
  let name = 'Rainbow Dash';
  let color = 'blue';
  return { name: name, color: color };
}
```

can be simplified to

```
function createPony() {
  let name = 'Rainbow Dash';
  let color = 'blue';
  return { name, color };
}
```

### Destructuring assignment

There is now a shortcut for assigning variables from objects or arrays.

In ES5:

```
var httpOptions = { timeout: 2000, isCache: true };
// later
var httpTimeout = httpOptions.timeout;
var httpCache = httpOptions.isCache;
```

Now, in ES6, you can do:

```
let httpOptions = { timeout: 2000, isCache: true };
// later
let { timeout: httpTimeout, isCache: httpCache } = httpOptions;
```

And you will have the same result. The cool thing is that it also works with nested objects:

```
let httpOptions = { timeout: 2000, cache: { age: 2 } };
// later
let { cache: { age } } = httpOptions;
// you now have a variable named 'age' with value 2
```
