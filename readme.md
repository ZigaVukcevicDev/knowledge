Notes from resources:

-   [Become a ninja with
    Angular2](https://books.ninja-squad.com/angular2)
-   [The introduction to Reactive Programming you've been
    missing](https://gist.github.com/staltz/868e7e9bc2a7b8c1f754)
-   [Taking advantage of Observables in Angular
    2](http://blog.thoughtram.io/angular/2016/01/06/taking-advantage-of-observables-in-angular2.html)
-   [JavaScript Promises, There and back
    again](http://www.html5rocks.com/en/tutorials/es6/promises/)
-   [Mozilla Developer
    Network](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
-   [JSON Web Token introduction](https://jwt.io/introduction/)

Table of content
================

-   [ECMAScript 6](#ecmascript-6)
    -   [let](#let)
    -   [Constants](#constants)
    -   [Creating objects](#creating-objects)
    -   [Destructuring assignment](#destructuring-assignment)
    -   [Default parameters and values](#default-parameters-and-values)
    -   [Promises](#promises)
    -   [Arrow functions](#arrow-functions)
    -   [Sets and Maps](#sets-and-maps)
    -   [Template literals](#template-literals)
    -   [Modules](#modules)
-   [Reactive programming](#reactive-programming)
    -   [Reactive programming in
        Angular 2](#reactive-programming-in-angular2)
-   [Angular 2](#angular2)
    -   [Components and directives](#components-and-directives)
-   [JSON Web Token](#json-web-token)

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

// @TODO

### Promises

The Promise object is used for deferred (postponed) and asynchronous
computations. A Promise represents an operation that hasn't completed
yet, but is expected in the future.

A Promise is in one of these states:

-   `pending`: initial state, not fulfilled or rejected.
-   `fulfilled`: meaning that the operation completed successfully.
-   `rejected`: meaning that the operation failed.

<!-- -->

    let promise = new Promise(function(resolve, reject) {
      // do something

      if (true) {
        resolve('It worked!');
      }
      else {
        reject('An error.'));
      }
    });

Here's how you use that promise:

    promise
      .then(function(result) {
        console.log(result); // It worked!
      })
      .catch(function(err) {
        console.log(err); // An error.
      });

### Arrow functions

The new arrow function syntax is the 'fat arrow' operator (⇒﻿). It is
useful for callbacks and anonymous functions.

In ES5:

    getUser(login)
      .then(function(user) {
        return getRights(user);
      })
      .then(function(rights) {
        return updateMenu(rights);
      })

Using 'fat arrow' operator in ES6:

    getUser(login)
      .then(user => getRights(user))
      .then(rights => updateMenu(rights))

No need to write user ⇒ return getRights(user)﻿. But if we did have a
block, we would need the explicit return:

    getUser(login)
      .then(user => {
        console.log(user);
        return getRights(user);
      })
      .then(rights => updateMenu(rights))

### Sets and Maps

// @TODO

### Template literals

// @TODO

### Modules

// @TODO

Reactive programming
--------------------

Reactive programming is a way to build an app using events and reacting
to them, using Reactive Extensions﻿ library like RxJS (RxJava...). Apps
have evolved to be more real-time: e.g. "likes" to some content can be
reflected in real time to other connected users.

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

JSON Web Token
--------------

JSON Web Token (JWT) is an open standard (RFC 7519) that defines a
compact and self-contained way for securely transmitting information
between parties as a JSON object.

This information can be verified and trusted because it is digitally
signed.

There are some scenarios where JSON Web Tokens are useful:

-   `Authentication`: This is the typical scenario for using JWT, once
    the user is logged in, each subsequent request will include the JWT,
    allowing the user to access routes, services, and resources that are
    permitted with that token.
-   `Information Exchange`: JSON Web Tokens are a good way of securely
    transmitting information between parties, because as they can be
    signed, for example using public/private key pairs, you can be sure
    that the senders are who they say they are.

JSON Web Tokens consist of three parts separated by dots `.`, which are:

-   Header
-   Payload
-   Signature

Therefore, a JWT typically looks like the following.

`xxxxx.yyyyy.zzzzz`

### Header

For example:

    {
      "alg": "HS256",
      "typ": "JWT"
    }

### Payload

The second part of the token is the payload, which contains the claims.
There are three types of claims: `reserved`, `public`, and `private`
claims.

An example of payload could be:

    {
      "sub": "1234567890",
      "name": "John Doe",
      "admin": true
    }

### Signature

To create the signature part you have to take the encoded header, the
encoded payload, a secret, the algorithm specified in the header, and
sign that.

For example if you want to use the HMAC SHA256 algorithm, the signature
will be created in the following way.

    HMACSHA256(
      base64UrlEncode(header) + "." +
      base64UrlEncode(payload),
      secret)

The signature is used to verify that the sender of the JWT is who it
says it is and to ensure that the message was't changed in the way.

Sample of encoded JWT:

    eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiYWRtaW4iOnRydWV9.TJVA95OrM7E2cBab30RMHrHDcEfxjoYZgeFONFh7HgQ

Angular 2
---------

### Components and directives

#### Components

1.  For register component we use `@Component` meta-data annotation.
2.  Component is a directive which use shadow DOM to create encapsulate
    visual behavior called components. Components are typically used to
    create UI widgets.
3.  Component is used to break up the application into
    smaller components.
4.  *Only one component* can be present per DOM element.
5.  @View decorator or template url template are mandatory in
    the component.

<!-- -->

    import { Component, View } from 'angular2/angular2';

    @Component({
      selector: 'message'
    })

    @View({
      template: `<h1>Hello Angular {{version}}</h1>`
    })

    class Message {
      constructor(public version: string) {}
    }

    <message></message>

#### Directives

1.  For register directives we use `@Directive` meta-data annotation.
2.  Directives is used to add behavior to an existing DOM element.
3.  Directive is use to design re-usable components.
4.  *Many directive* can be used in a per DOM element.
5.  Directive don’t have View.

<!-- -->

    import { Directive } from 'angular2/angular2';

    @Directive({
        selector: '[myDirective]',
        hostListeners: {
          'click': 'showMessage()'
        }
    })

    class Message {

        constructor() {}

        showMessage() {
          console.log('Hello Directive');
        }
    }

    <button myDirective>Click here</button>

#### How to merge all md files

`pandoc toc.md es6.md reactive-programming.md jwt.md angular2.md note.md -f markdown -t markdown -s -o readme.md`
