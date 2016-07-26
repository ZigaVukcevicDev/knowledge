Table of content
================

-   [Code commenting](#code-commenting)
    -   [class](#class)
-   [JavaScript](#javascript)
    -   [Event listening and
        dispatching](#event-listening-and-dispatching)
-   [ECMAScript 6](#ecmascript-6)
    -   [Import and export](#import-and-export)
    -   [Template literals](#template-literals)
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
-   [React](#react)
    -   [JSX](#jsx)
    -   [Properties](#properties)
    -   [Events](#events)
    -   [State](#state)
    -   [Bind This](#bind-this)
-   [TypeScript](#typescript)
-   [Reactive programming](#reactive-programming)
    -   [Reactive programming in
        Angular 2](#reactive-programming-in-angular2)
    -   [Subject](#subject)
-   [Angular 2](#angular-2)
    -   [Components and directives](#components-and-directives)
    -   [ViewEncapsulation](#viewencapsulation)
    -   [HostListener](#hostlistener)
-   [JSON Web Token](#json-web-token)
-   [Design patterns](#design-patterns)
    -   [Subject/observer](#todo)
    -   [Publish/subscribe](#todo)

Code commenting
---------------

### Class

    /** Class representing a point. */
    class Point {
        /**
         * Create a point.
         *
         * @param {number} x - The x value.
         * @param {number} y - The y value.
         *
         * @return {number} The x value.
         */
        constructor(x, y) {
            // ...
        }

JavaScript
----------

### Event listening and dispatching

// TODO
https://developer.mozilla.org/en-US/docs/Web/API/MutationObserver
https://developer.mozilla.org/en-US/docs/Web/Guide/Events/Creating\_and\_triggering\_events

ECMAScript 6
------------

// TODO: check this samples: http://webapplog.com/es6/

A `transpiler` takes ES6 source code and generates ES5 code that can run
in every browser - e.g. Traceur or Babeljs.

### Import and export

#### Import

// TODO

import defaultMember from "module-name"; import \* as name from
"module-name"; import { member } from "module-name"; import { member as
alias } from "module-name"; import { member1 , member2 } from
"module-name"; import { member1 , member2 as alias2 , \[...\] } from
"module-name"; import defaultMember, { member \[ , \[...\] \] } from
"module-name"; import defaultMember, \* as name from "module-name";
import "module-name";

#### Export

// TODO

export { name1, name2, …, nameN }; export { variable1 as name1,
variable2 as name2, …, nameN }; export let name1, name2, …, nameN; //
also var export let name1 = …, name2 = …, …, nameN; // also var, const

export default expression; export default function (…) { … } // also
class, function* export default function name1(…) { … } // also class,
function* export { name1 as default, … };

export \* from …; export { name1, name2, …, nameN } from …; export {
import1 as name1, import2 as name2, …, nameN } from …;

### Template literals

By using `back-tick` you can use variables with strings.

    `${variable} and lorem ipsum.`

Or even write multi line text.

    `Lorem ipsum
    and another line.`

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

React
-----

### JSX

This is a sample of `JSX` (JavaScript XML).

    let HelloWorld = React.createClass({
      render: () => {
        return
          <div>
            <h1>Hello World</h1>
            <p>This is some text</p>
          </div>
      }
    });

    React.render(<Hello World />, document.body);

### Properties

This is sample of using `props`.

    let HelloWorld = React.createClass({
      render: () => {
        return
          <div>
            <h1>{this.props.text}</h1>
            <p>{this.props.children}</p>
          </div>
      }
    });

    React.render(
      <div>
        <Hello World text="Hello World" />
        <Hello World>
          This is some text
        </Hello World>
      </div>
      , document.getElementById('some-container')
    );

#### Types of properties

Example of determining types.

        propTypes = {
            propFunction: React.PropTypes.func,
            propObject: React.PropTypes.object,
            propWithinObject: React.PropTypes.shape({
                sampleProp: React.PropTypes.oneOfType([
                    React.PropTypes.number,
                    React.PropTypes.string
                ]).isRequired,
                anotherSampleProp: React.PropTypes.isRequired
            }).isRequired
        };

### Events

// @TODO

### State

// @TODO

### Bind this

It’s not always clear what `this` is going to refer to in your code. As
functions in JS are objects, every function has it own `this`. Samples:

#### Alias This

        var component = this;
        component.setState({ loading: true });

        fetch('/').then(function loaded() {
            component.setState({ loading: false });
        });

#### Bind This

        this.setState({ loading: true });

        fetch('/').then(function loaded() {
            this.setState({ loading: false });
        }.bind(this));

#### React Component Methods

React allows you to define arbitrary methods on your component classes
and these methods are automatically bound with the correct context for
`this` when you create your components with `React.createClass`. This
allows you move your callback code out onto your component.

    React.createClass({
      componentWillMount: function() {
        this.setState({ loading: true });

        fetch('/').then(this.loaded);
      },
      loaded: function loaded() {
        this.setState({ loading: false });
      }
    });

#### ES2015 Arrows

They always use the value of `this` from the enclosing scope.

        this.setState({ loading: true });

        fetch('/').then(() => {
            this.setState({ loading: false });
        });

TypeScript
----------

### Why TypeScript

There are two main goals of TypeScript:

-   Provide an optional type system for JavaScript.
-   Provide planned features from future JavaScript editions to current
    JavaScript engines

sample.js (JavaScript)

    let foo = 123;

sample.ts (TypeScript)

    let foo: number = 123

Types increase your agility when doing refactoring. Its better for the
**compiler to catch errors** than to have things **fail at runtime**.

### Types are structural

    interface Point2D {
      x: number;
      y: number;
    }
    interface Point3D {
      x: number;
      y: number;
      z: number;
    }

    var point2D: Point2D = { x: 0, y: 10, }
    var point3D: Point3D = { x: 0, y: 10, z: 20 }
    function iTakePoint2D(point: Point2D) { /* do something */ }

    iTakePoint2D(point2D); // exact match okay
    iTakePoint2D(point3D); // extra information okay
    iTakePoint2D({ x: 0 }); // Error: missing information `y`

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

### Subject

A `Subject` is a sort of bridge that is available in some
implementations of ReactiveX that acts both as an `observer` and as an
`Observable`. Because it is an observer, it can subscribe to one or more
Observables, and because it is an Observable, it can pass through the
items it observes by reemitting them, and it can also emit new items.

    spinner$: Subject<boolean> = new Subject();
    spinner: boolean = false;

    this.spinner$.next(this.spinner);

    this.spinner$.subscribe((spinner) => {
      console.log(spinner); // should output false
    });

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
4.  @View decorator or template url template are mandatory in
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
4.  Directive don’t have View.

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

In summary

Write a `component` when you want to create a reusable set of DOM
elements of UI with custom behaviour. Write a `directive` when you want
to write reusable behaviour to supplement existing DOM elements.

### ViewEncapsulation

// TODO: read this
https://toddmotto.com/emulated-native-shadow-dom-angular-2-view-encapsulation

### HostListener

Angular provides an easy way to listen to events on `window` or
`document`. Regular way `window.onScoll` will not work - it's because
the window object is instantiated outside Angular.

    import { HostListener } from 'angular2/core';

    class SomeClass {
      @HostListener('window:scroll', ['$event'])
      onScroll(event) {
        if ((window.innerHeight + window.scrollY) >= document.body.scrollHeight) {
          console.log('Bottom of page');
        }
      }
    }

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

Design patterns
---------------

### Subject / observer

The Observer is a design pattern where an object (known as a `subject`)
maintains a list of objects depending on it (`observers`), automatically
notifying them of any changes of state.

In the Observer/Observable pattern, the observers are aware of the
observable.

// ConcreteSubject: broadcasts notifications to observers on changes of
state, stores the state of ConcreteObservers // ConcreteObserver: stores
a reference to the ConcreteSubject, implements an update interface for
the Observer to ensure state is consistent with the Subject's

// There are no topics, subject calls method on all observers.

#### Subject

Maintains a list of observers (can add or remove them).

// observable calls the appropriate method of all its observers when
some event occurs. The

#### Observer

Provides an update interface for objects that need to be notified of a
Subject's changes of state.

// TODO //Observer, or Observable/Observer: // A design pattern by which
an object is imbued with the ability to notify others of specific events
- typically done using actual events, which are kind of like slots in
the object with the shape of a specific function/method. The observable
is the one who provides notifications, and the observer receives those
notifications. In .net, the observable can expose an event and the
observer subscribes to that event with an "event handler"shaped hook. No
assumptions are made about the specific mechanism which notifications
occur, nor about the number of observers one observable can notify.

### Publish / subscribe

This pattern uses an `event system` that sits between the objects
wishing to receive notifications (`subscribers`) and the objects firing
the events (`publishers`).

    class PublishSubscribe {
        constructor() {
            this.topics = [];
        }

        subscribe(topic, callback) {

            // Create the topic if not yet created
            if(!this.topics[topic]) {
                this.topics[topic] = [];
            }

            // Add the callback to specific topic
            this.topics[topic].push(callback);
        }

        publish(topic, data) {

            // Returned false if the topic doesn't exist or there are no callbacks
            if(!this.topics[topic] || this.topics[topic].length === 0) {
                return false;
            }

            // Calling all callbacks for specific topic and passing data
            this.topics[topic].forEach((callback) => {
                callback(data || {});
            });
        }
    }

    const tryIt = new PublishSubscribe;

    tryIt.subscribe('my-topic', alert);
    tryIt.publish('my-topic', 'Hello World!');

The goal is to avoid dependencies between `publisher` and `subscriber`
(so called `decoupling`).

Resources
---------

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
-   [Difference between component and directive in Angular
    2](http://www.codeandyou.com/2016/01/difference-between-component-and-directive-in-Angular2.html)
-   [JSON Web Token introduction](https://jwt.io/introduction/)
-   [TypeScript Deep
    Dive](https://basarat.gitbooks.io/typescript/content/docs/why-typescript.html)
-   [@use JSDoc](http://usejsdoc.org/)
-   [6 Ways to Bind JavaScript's this Keyword in React, ES6 &
    ES7](https://www.sitepoint.com/bind-javascripts-this-keyword-react/)
-   [Decoupling JavaScript applications using the Publish/Subscribe
    pattern](http://dev.housetrip.com/2014/09/15/decoupling-javascript-apps-using-pub-sub-pattern/)
    \#\#\#\# How to merge all md files

`pandoc toc.md code-commenting.md javascript.md es6.md react.md typescript.md reactive-programming.md angular2.md jwt.md design-patterns.md resources.md note.md -f markdown -t markdown -s -o readme.md`
