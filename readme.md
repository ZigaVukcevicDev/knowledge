Notes from resources:
    - [Become a ninja with Angular2](https://books.ninja-squad.com/angular2)
    - [The introduction to Reactive Programming you've been missing](https://gist.github.com/staltz/868e7e9bc2a7b8c1f754)

Table of content
================

-   [ECMAScript 6](#ecmascript-6)
    -   [let](#let)
    -   [Constants](#constants)
    -   [Creating objects](#creating-objects)
    -   [Destructuring assignment](#destructuring-assignment)
    -   [Default parameters and values](#default-parameters-and-values)
-   [Reactive programming](#reactive-programming)
    -   [Reactive programming in
        Angular 2](#reactive-programming-in-angular2)

ECMAScript 6
------------

A `transpiler` takes ES6 source code and generates ES5 code that can run
in every browser - e.g. Traceur or Babeljs.

### let

In pretty much any other languages, a variable is declared where the
declaration is done. But in JS, there is a concept, called `hoisting`,
which actually declares a variable at the top of the function, even if
you declared it later. [See
more](http://www.w3schools.com/js/js_hoisting.asp)

By using `let` the variable `name`﻿ is now restricted to its block.

    function getPonyFullName(pony) {
      if (pony.isChampion) {
        let name = 'Champion ' + pony.name;
        return name;
      }
      // name is not accessible here
      return pony.name;
    }

### Constants

When you declare a variable with const﻿, it has to be initialized and
you can’t assign another value later.

    const PONIES_IN_RACE = 6;

### Creating objects

Example:

    function createPony() {
      let name = 'Rainbow Dash';
      let color = 'blue';
      return { name: name, color: color };
    }

can be simplified to

    function createPony() {
      let name = 'Rainbow Dash';
      let color = 'blue';
      return { name, color };
    }

### Destructuring assignment

There is now a shortcut for assigning variables from objects or arrays.

In ES5:

    var httpOptions = { timeout: 2000, isCache: true };
    // later
    var httpTimeout = httpOptions.timeout;
    var httpCache = httpOptions.isCache;

Now, in ES6, you can do:

    let httpOptions = { timeout: 2000, isCache: true };
    // later
    let { timeout: httpTimeout, isCache: httpCache } = httpOptions;

And you will have the same result. The cool thing is that it also works
with nested objects:

    let httpOptions = { timeout: 2000, cache: { age: 2 } };
    // later
    let { cache: { age } } = httpOptions;
    // you now have a variable named 'age' with value 2

### Default parameters and values

TODO.

Reactive programming
--------------------

It is a way to build an app using events and reacting to them, using
Reactive Extensions﻿ library like RxJS (RxJava...).

`Listener` is called an `observer`﻿, and the `stream`, `an observable`﻿.
A stream is an ordered sequence of events. This is well-known design
pattern: the observer﻿ pattern.

Observables are very close to arrays. An array is a collection of
values, like an observable. An observable only adds the concept of
values over time: in an array, you have all the values at once, while
the values will come over time in an observable, maybe every few
minutes.

Every observable, just like every array, can be transformed:

-   `take(n)`﻿ will pick the n first events
-   `map(fn)`﻿ will apply fn﻿ to each event and return the result
-   `filter(predicate)`﻿ will only let through the events that fulfill
    the predicate
-   `reduce(fn)`﻿ will apply fn﻿ to every event to reduce the stream to
    a single value
-   `merge(s1, s2)`﻿ will merge the streams
-   `subscribe(fn)`﻿ will apply fn﻿ to each event it receives
-   and much more...

<!-- -->

    [1, 2, 3, 4, 5]
      .map(x => x * 2)
      .filter(x => x > 5)
      .forEach(x => console.log(x)); // 6, 8, 10

RxJS let us build an observable from an array.

    Observable.fromArray([1, 2, 3, 4, 5])
      .map(x => x * 2)
      .filter(x => x > 5)
      .subscribe(x => console.log(x)); // 6, 8, 10

But an observable is more than a collection. It is an asynchronous
collection, where the events arrive over time.

    let input = $('input');

    Observable.fromEvent(input, 'keyup')
      .subscribe(() => console.log('keyup!'));

      input.trigger('keyup'); // logs "keyup!"
      input.trigger('keyup'); // logs "keyup!"

You can build observables from AJAX requests, browser events, Web
sockets responses, a promise, whatever you can think of.

Observable.create﻿ takes a function that will emit events on the
observer﻿ given as parameter. Here it simply emits one event for the
demonstration.

    let observable = Observable.create((observer) => observer.next('hello'));

    observable.subscribe((value) => console.log(value));
    // logs "hello"

Here, the range﻿ method we are using to create the events will iterate
from 1 to 5 and then emit the 'completed' signal:

    Observable.range(1, 5)
      .map(x => x * 2)
      .filter(x => x > 5)
      .subscribe(x => console.log(x), error => console.log(error), () => console.log('done'));
    // 6, 8, 10, done

### Reactive programming in Angular 2

The EventEmitter﻿ has a method `subscribe()`﻿ to react to events and
this method can receive three parameters:

-   a method to react on `events`
-   a method to react on `errors`
-   a method to react on `completion`

<!-- -->

    let emitter = new EventEmitter();

    emitter.subscribe(
      value => console.log(value),
      error => console.log(error),
      () => console.log('done')
    );

    emitter.emit('hello');
    emitter.emit('there');
    emitter.complete();

    // logs "hello", then "there", then "done"

#### How to merge all md files

`pandoc toc.md es6.md reactive-programming.md note.md -f markdown -t markdown -s -o readme.md`
