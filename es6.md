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
