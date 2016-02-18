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

### Default parameters and values

TODO.

### Promises

The Promise object is used for deferred (postponed) and asynchronous computations. A Promise represents an operation that hasn't completed yet, but is expected in the future.

A Promise is in one of these states:

- `pending`: initial state, not fulfilled or rejected.
- `fulfilled`: meaning that the operation completed successfully.
- `rejected`: meaning that the operation failed.

```
let promise = new Promise(function(resolve, reject) {
  // do something

  if (true) {
    resolve('It worked!');
  }
  else {
    reject('An error.'));
  }
});
```

Here's how you use that promise:

```
promise
  .then(function(result) {
    console.log(result); // It worked!
  })
  .catch(function(err) {
    console.log(err); // An error.
  });
```

<div id="disqus_thread"></div>
<script>
/**
* RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR PLATFORM OR CMS.
* LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: https://disqus.com/admin/universalcode/#configuration-variables
*/
/*
var disqus_config = function () {
this.page.url = PAGE_URL; // Replace PAGE_URL with your page's canonical URL variable
this.page.identifier = PAGE_IDENTIFIER; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
};
*/
(function() { // DON'T EDIT BELOW THIS LINE
var d = document, s = d.createElement('script');

s.src = '//be-codified.disqus.com/embed.js';

s.setAttribute('data-timestamp', +new Date());
(d.head || d.body).appendChild(s);
})();
</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript" rel="nofollow">comments powered by Disqus.</a></noscript>
