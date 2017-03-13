Table of content
================

-   [Code commenting](#code-commenting)
    -   [class](#class)
-   [JavaScript (ES5 and lower)](##javascript-es5-or-lower)
    -   [Primitives and object
        wrappers (TODO)](#primitives-and-object-wrappers)
    -   [Truthy & falsy](#truthy--falsy)
    -   [Event listening and
        dispatching (TODO)](#event-listening-and-dispatching)
    -   [IIFE (TODO)](#iife)
    -   [Closures (TODO)](#closures)
    -   [Understanding difference between function, method and
        constructor
        call (TODO)](#understanding-difference-between-function-method-and-constructor-call)
    -   [Higher order functions (TODO)](#higher-order-functions)
    -   [Function composition](#function-composition)
    -   [Prototype](#prototype)
-   [ECMAScript 6](#ecmascript-6)
    -   [Modules (import and export)](#modules-import-and-export)
    -   [Class](#class)
    -   [Template literals](#template-literals)
    -   [let](#let)
    -   [Constants](#constants)
    -   [Creating objects](#creating-objects)
    -   [Destructuring assignment](#destructuring-assignment)
    -   [Default parameters and values](#default-parameters-and-values)
    -   [Promises](#promises)
    -   [Arrow functions](#arrow-functions)
-   [React](#react)
    -   [JSX](#jsx)
    -   [Properties](#properties)
    -   [Events (TODO)](#events)
    -   [State (TODO)](#state)
    -   [Bind This](#bind-this)
    -   [Stateless functional
        components](#stateless-functional-components)
    -   [Lifecycle methods](#lifecycle-methods)
    -   [Animations](#animations)
-   [Git (TODO)](#git)
-   [Git Flow (TODO)](#git-flow)
-   [TypeScript](#typescript)
-   [Reactive programming](#reactive-programming)
    -   [Reactive programming in
        Angular 2](#reactive-programming-in-angular2)
    -   [Subject](#subject)
-   [Angular 2](#angular-2)
    -   [Components and directives](#components-and-directives)
    -   [ViewEncapsulation](#viewencapsulation)
    -   [HostListener](#hostlistener)
-   [CSS](#css)
    -   [BEM](#bem)
-   [JSON Web Token](#json-web-token)
-   [Design patterns](#design-patterns)
    -   [Subject/observer](#subject--observer)
    -   [Publish/subscribe](#publish--subscribe)
-   [Unix commands](#unix-commands)
-   [Mongo](#mongo)
-   [Not to neglect](#not-to-neglect)

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
         *
         */
        constructor(x, y) {
            // ...
        }

JavaScript (ES5 or lower)
-------------------------

<!---
### Primitives and object wrappers

// TODO 15
-->
### Truthy & Falsy

#### Truthy

In JavaScript, a `truthy value` is a value that translates to true when
evaluated in a Boolean context. All values are **truthy** unless they
are defined as **falsy**.

Examples

    if (true)
    if ({})
    if ([])
    if (42)
    if ('foo')
    if (new Date())
    ... and everything else (unless defined as falsy)

#### Falsy

A `falsy value` is a value that translates to false when evaluated in a
Boolean context.

Seven cases

    if (false)
    if (null)
    if (undefined)
    if (0)
    if (NaN)
    if ('')
    if ("")

<!---
### Event listening and dispatching

// TODO
https://developer.mozilla.org/en-US/docs/Web/API/MutationObserver
https://developer.mozilla.org/en-US/docs/Web/Guide/Events/Creating_and_triggering_events

### IIFE

// TODO 46

### Closures

// TODO 39

### Understanding difference between function, method and constructor call

// TODO 57

### Higher order functions

// TODO 60
-->
### Function composition

Functions can be combined to form new functions through function
composition. The function `addThenSquare` is made by combining the
functions `add` and `square`.

    const add = function(x, y) {
        return x + y;
    };

    const square = function(x) {
        return x * x;
    };

    const addThenSquare = function(x, y) {
        return square(add(x, y));
    };

### Prototype

Every JavaScript object has a prototype which is also an object. All
JavaScript objects inherit their properties and methods from their
prototype.

    function Something() {} // note capital letter and fact that function is an object in JS

    Something.prototype.bar = true; // this could also be a method/function
    let something = new Something();

    something.bar; // true
    something instanceof Something; // true

ECMAScript 6
------------

A `transpiler` takes ES6 source code and generates ES5 code that can run
in every browser - e.g. Traceur or Babeljs.

### Modules (import and export)

#### Export

Export statement is used to export functions, objects or primitives from
a given file.

    export { name1, name2 };
    export { variable1 as name1, variable2 as name2 };
    export let name1, name2;
    export let name1 = ..., name2 = ...

There are two different types of export:

a)  `Named` exports:

    export { myFunction }; // exports a function declared earlier export
    const foo = Math.sqrt(2); // exports a constant

b)  `Default` exports (only one per script):

    export default function() {} export default function name() {}
    export { name1 as default, name2 };

Re-exporting means adding another module’s exports to those of the
current module.

    export * from 'other-module-name';
    export { name1, name2 } from 'other-module-name';

#### Import

The import statement is used to import functions, objects or primitives
that have been exported from an external module, another script.

    import nameForDefault from 'module-name';
    import * as name from 'module-name';
    import { name } from 'module-name';
    import { name as anotherName } from 'module-name';
    import { name1, name2 } from 'module-name';

### Class

#### Class definition

    class Shape {
        constructor (id, x, y) {
            this.id = id
            this.move(x, y)
        }
        move (x, y) {
            this.x = x
            this.y = y
        }
    }

#### Class inheritance, base class access

    class Shape {
        ...
        toString() {
            return `Shape(${this.id})`;
        }
    }

    class Rectangle extends Shape {
        constructor (id, x, y, width, height) {
            super(id, x, y)
            ...
        }
        toString() {
            return "Rectangle > " + super.toString();
        }
    }

#### Using extends with built-in objects

    class myDate extends Date {
        constructor() {
            super();
        }

        getFormattedDate() {
            const months = ['Jan', 'Feb', 'Mar', etc.];
            return this.getDate() + "-" + months[this.getMonth()] + "-" + this.getFullYear();
        }
    }

#### Static members

    class Circle extends Shape {
        ...
        static defaultCircle() {
            return new Circle('default', 0, 0, 100)
        }
    }

    const defCircle = Circle.defaultCircle();

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

There is a shortcut for assigning variables from objects or arrays.

    const { something, somethingElse } = object;

Will produce the same as:

    const something = object.something;
    const somethingElse = object.somethingElse;

#### Spread operator

The spread syntax allows an expression to be expanded.

    function myFunction(x, y, z) {}

    let args = [0, 1, 2];
    myFunction(...args);

Or

    let parts = ['shoulders', 'knees'];
    let lyrics = ['head', ...parts, 'and', 'toes']; // ["head", "shoulders", "knees", "and", "toes"]

You can also use it for shallow copy of object

    const shallowSomeObject = {...someObject};
    shallowSomeObject.newProperty = 'some string';

### Default parameters and values

    const link = function(color = 'red', url = 'http://some-url.com') {
        ...
    }

### Promises

The Promise object is used for deferred (postponed) and asynchronous
computations. A Promise represents an operation that hasn't completed
yet, but is expected in the future.

A Promise is in one of these states:

-   `pending`: initial state, not fulfilled or rejected.
-   `fulfilled`: meaning that the operation completed successfully.
-   `rejected`: meaning that the operation failed.

a)  Example

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

b)  Another example:

<!-- -->

    function msgAfterTimeout(msg, time) {
        return new Promise((resolve, reject) => {
            setTimeout(() => resolve(msg), time)
        })
    }

    msgAfterTimeout("Breakfast is served.", 500).then(result => console.log(result));

### Arrow functions

The new arrow function syntax is the `fat arrow` operator (⇒﻿). It is
useful for callbacks and anonymous functions.

In ES5:

    getUser(login)
        .then(function(user) {
            return getRights(user);
        })
        .then(function(rights) {
            return updateMenu(rights);
        })

Using `fat arrow` operator in ES6:

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

<!--
### Events

// TODO

### State

// TODO
-->
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

### Stateless functional components

A simpler way to define components called
`stateless functional components`. These components use plain JavaScript
functions. Stateless functional components
`don’t support state or lifecycle methods`.

Samples:

    const ListItem = (props) => <li>{props.item.name}</li>;

or

    const List = ({ items }) => (
        <ul>
            {items.map((item) => <ListItem item={item} />)}
        </ul>
    );

or

    const Body = (props) => {
        let items = transformItems(props.rawItems);

        return (
            <div>
                <h1>{props.header}</h1>
                <List items={items} />
            </div>
        );
    };

    Body.propTypes = {
        rawItems: React.PropTypes.array.isRequired,
    };

### Lifecycle methods

These methods are executed at specific points in a component's
lifecycle.

#### componentWillMount

Invoked only once, both on the client and server, immediately before the
initial rendering occurs.

[See sample](http://codepen.io/be-codified/pen/YWRgBd?editors=0011)

If you call `setState` within this method, `render()` will see the
updated state and will be invoked only once (ignoring that state
changed).

[See sample](http://codepen.io/be-codified/pen/dXQLrA?editors=0010)

Params: none

<!--
#### componentDidMount
// TODO

#### componentWillReceiveProps
// TODO

#### shouldComponentUpdate
// TODO

#### componentWillUpdate
// TODO

#### componentDidUpdate
// TODO

#### componentWillUnmount
// TODO
-->
#### Animations

    componentWillMount() {
        this.animationValue = new Animated.Value();

        this.animationValue.addListener(value => {
            this.animationStep(value);
        });
    }

    componentDidMount() {
        this.animateIt();
    }

    animateIt() {
        this.animationValue.setValue(0);

        Animated.timing(this.animationValue, {
            toValue: 100,
            duration: this.props.animationDuration,
            easing: Easing.linear
        }).start();
    }

    animationStep(value) {
        // value will be between 1 - 100
        // use reference on element and change its data, e.g.
        ref.setAttribute('d', somethingCalculatedBasedOnValue);
    }

See more at: -
https://facebook.github.io/react-native/docs/animations.html -
https://facebook.github.io/react-native/docs/animated.html

Git
---

### Init

Initializes a repository in an existing directory. This will create
`.git` hidden folder, a location where Git operates.

    git init

### Status

Shows the working tree status.

    git status

### Add

This command updates the index using the current content found in the
working tree, to prepare the content `staged` for the next commit.

    git add some-file.txt

Wildcards are supported, e.g. `git add '*.txt'` or you can add all files
by `git add .`

### Commit

Check how to properly write a git [commit
message](http://chris.beams.io/posts/git-commit/).

Records changes to the repository. By using `-m` flag, a custom message
will be added with commit.

    git commit -m "Some message"

By using `-a` flag, command will also do `git add .`

    git commit -a -m "Some message"

### Log

Shows local commit logs.

    git log

Shows remote commit logs.

    git log origin/master

Shows local commit logs in one line / commit.

    git log --oneline

Shows local commit logs with graphic appearance.

    git log --graph

Shows files changed in local commit logs

    git log --name-only

### Remote add

Manages set of tracked repositories.

    git remote add origin some-url

### Push

Updates remote refs along with associated objects. The flag `-u` tells
Git to remember the parameters, so that next time we can simply run git
push and Git will know what to do.

    git push -u origin master

### Pull

Fetches from and integrate with another repository or a local branch.

    git pull origin master

### Diff

Show changes between commits, commit and working tree, etc.

    git diff

Shows difference of most recent commit, which is referred using the HEAD
pointer.

    git diff HEAD

Shows staged difference.

    git diff --staged

### Clean

Removes untracked files from the working tree.

    git clean -f

Flag `f` will force deletion, otherwise git will refuse it.

### Reset

Unstages files.

    git reset some-file.txt

Flag `soft` will move HEAD 1 commit back and put changes as they were
not commited yet, so you can commit them again.

    git reset --soft HEAD~1

Flag `hard` will move HEAD 1 commit back and delete changes.

    git reset --hard HEAD~1

### Revert

It will revert commit by adding a commit (so you can see the history of
what has been reverted).

    git revert commitId

### Checkout

Changes file back to how it was at the last commit.

    git checkout -- some-file.txt

### Branches

Creates new branch

    git branch new_branch_name

Deletes branch

    git branch -d branch_name

Checkouts to new branch

    git checkout new_branch_name

Merges branch into checkouted branch (e.g. first checkout to master
branch, then merge develop branch into)

    git merge name_of_branch

Shows merged branches that had been merged at any time

    git branch --merged

### Clone

It will clone remote repository to local one.

    git clone some-url

### Remote

Set remote repository

    git remote add origin some-url

Show remote repository

    git remote -v

### Tags

Listing tags

    git tag

Creating annotated tag

    git tag -a v1.4 -m "my version 1.4"
    git push origin --tags

Deleting tag

    git tag -d v1.4

### Submodules

Go to root folder.

    git submodule add some-repo-url some-folder

<!---

// TODO: table of contents
https://github.com/robbyrussell/oh-my-zsh/wiki/Plugin:git

### Merge

git merge --abort

Reset, Checkout, and Revert
https://www.atlassian.com/git/tutorials/resetting-checking-out-and-reverting/commit-level-operations

https://chrisjean.com/git-submodules-adding-using-removing-and-updating

-->
<!---
    // TODO: cheatsheet

    http://danielkummer.github.io/git-flow-cheatsheet/
-->
Git Flow
--------

Git-flow are a set of git extensions to provide high-level repository
operations for Vincent Driessen's branching model.

### Init

Start using git-flow by initializing it inside an existing git
repository

    git flow init

### Feature

This action creates a new feature branch based on `develop` and switches
to it:

    git flow feature start new-branch-name

Finish the development of a feature. This action performs the following:

-   merges `existing-branch-name branch` into `develop branch`
-   removes the `existing-branch-name branch`
-   switches back to `develop branch`

<!-- -->

    git flow feature finish existing-branch-name

Publish a feature to the remote server so it can be used by other users:

    git flow feature publish existing-branch-name

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

`Listener` is called an `observer`﻿, and the `stream`, an `observable`﻿.
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

        input.trigger('keyup'); // logs 'keyup!'
        input.trigger('keyup'); // logs 'keyup!'

You can build observables from AJAX requests, browser events, Web
sockets responses, a promise, whatever you can think of.

Observable.create﻿ takes a function that will emit events on the
observer﻿ given as parameter. Here it simply emits one event for the
demonstration.

    let observable = Observable.create((observer) => observer.next('hello'));

    observable.subscribe((value) => console.log(value));
    // logs 'hello'

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

    // logs 'hello', then 'there', then 'done'

### Subject

A `Subject` is a sort of bridge that is available in some
implementations of ReactiveX that acts both as an `Observer` and as an
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

<!---
### ViewEncapsulation

// TODO: read this https://toddmotto.com/emulated-native-shadow-dom-angular-2-view-encapsulation
-->
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

CSS
---

### BEM

Blocks, Elements and Modifiers

#### A) Block

Standalone entity that is meaningful on its own.

Examples: `header`, `container`, `menu`, `checkbox`, `input`

#### B) Element

A part of a block that has no standalone meaning and is semantically
tied to its block.

Examples: `menu item`, `list item`, `checkbox caption`, `header title`

#### C) Modifier

A flag on a **block** or **element**. Use them to change appearance or
behavior.

Examples: `disabled`, `highlighted`, `checked`, `fixed`, `size big`,
`color yellow`

------------------------------------------------------------------------

#### Usage

The naming rules tell us to use `block--modifier` syntax.

**HTML**

    <button class="button button--state-success">
        Success button
    </button>
    <button class="button button--state-danger">
        Danger button
    </button>

**CSS**

    .button { // rules for button }
    .button--state-success { // rules for state-success modifier }
    .button--state-danger  { // rules for state-danger modifier }

If there would be an `element` involved, we would use
`block__elem--modifier` syntax.

How to correctly work with children selectors:

**HTML**

    <div class="card">
        <div class="card__header">
            <h2 class="card__title">Title text here</h2>
        </div>
        <div class="card__body">
            <img class="card__img" src="some-img.png">

            <p class="card__text">Lorem ipsum dolor sit amet, consectetur</p>
            <p class="card__text">Adipiscing elit.
                <a href="/somelink.html" class="card__link">Pellentesque amet</a>
            </p>
        </div>
    </div>

Don't use `card__body__text__link` as this will quickly get out of hand.

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
        alg: 'HS256',
        typ: 'JWT'
    }

### Payload

The second part of the token is the payload, which contains the claims.
There are three types of claims: `reserved`, `public`, and `private`
claims.

An example of payload could be:

    {
        sub: '1234567890',
        name: 'John Doe',
        admin: true
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

<!---
### Subject / observer

**--- NOTE: NOT FINISHED YET ---**

The Observer is a design pattern where an object (known as a `subject`) maintains a list of objects depending on it (`observers`), automatically notifying them of any changes of state.

In the Observer/Observable pattern, the observers are aware of the observable.

// ConcreteSubject: broadcasts notifications to observers on changes of state, stores the state of ConcreteObservers
// ConcreteObserver: stores a reference to the ConcreteSubject, implements an update interface for the Observer to ensure state is consistent with the Subject's

// There are no topics, subject calls method on all observers.

#### Subject

Maintains a list of observers (can add or remove them).

// observable calls the appropriate method of all its observers when some event occurs. The

#### Observer

Provides an update interface for objects that need to be notified of a Subject's changes of state.

// TODO
//Observer, or Observable/Observer:
// A design pattern by which an object is imbued with the ability to notify others of specific events - typically done using actual events, which are kind of like slots in the object with the shape of a specific function/method. The observable is the one who provides notifications, and the observer receives those notifications. In .net, the observable can expose an event and the observer subscribes to that event with an "event handler"shaped hook. No assumptions are made about the specific mechanism which notifications occur, nor about the number of observers one observable can notify.
-->
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
            if (!this.topics[topic]) {
                this.topics[topic] = [];
            }

            // Add the callback to specific topic
            this.topics[topic].push(callback);
        }

        publish(topic, data) {

            // Returned false if the topic doesn't exist or there are no callbacks
            if (!this.topics[topic] || this.topics[topic].length === 0) {
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

Unix commands
-------------

### Basics

#### cat

Show contents of the file.

    cat some-file.txt

#### pwd

Show the name of the current working directory.

    pwd

#### cd

Change the current working folder.

    cd some-folder

    cd ..    // move one folder up
    cd /     // move to home folder
    cd ~     // move to root

#### cp

Copy the file `some-file-1.txt` to the file `some-file-2.txt` in the
current working folder.

    cp some-file-1.txt some-file-2.txt

#### mv

Move or rename files.

    mv some-file-1.txt some-file-2.txt    // Changes the names from "some-file-1.txt" to "some-file-2.txt"
    mv /some-folder/some-file .           // Move the file from "some-file" from the folder "/some-folder" 
                                             to the current working folder.

#### rm

Remove the folder. Flag means remove recursively (deleting everything in
folder)

    rm -r folder

#### locate

Locates file or folder.

    locate partial-name

#### ll

List all files in the current working directory in long listing format
showing permissions, ownership, size, and time and date stamp.

    ll

Using flag `a` will also show hidden files/folders.

    ll -a

Mongo
-----

Running services

    sudo service mongodb start
    sudo service mongodb stop
    sudo service mongodb restart

or

    brew services start mongodb
    brew services stop mongodb

Client
------

Run client

    mongo

### Showing databases (with at least one record)

    show dbs

### Using specific database

    use myDatabase

### Showing collections

    show collections

### Create collection

    db.createCollection("users", { autoIndexID : true })

### Insert document

    db.users.insert({"name" : "John"})

### Showing documents

    db.users.find().pretty()

Not to neglect
--------------

This title could also be
`What I've learned on my way  from respective senior developers`.

-   Writing clean and "cached" code is important. It doesn't really
    matter if a user sees his site in 30 ms (instead of 20 ms) but it
    matters if we can serve 800 sites/second (instead of just 500).

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
-   [Learn Git Branching](http://learngitbranching.js.org/)
-   [ES6 Cheatsheet](https://es6cheatsheet.com)
-   [Battling BEM – 5 common problems and how to avoid
    them](https://medium.com/fed-or-dead/battling-bem-5-common-problems-and-how-to-avoid-them-5bbd23dee319#.or1bepw1m)
-   [BEM — Block Element Modifier](http://getbem.com/)
-   [Learn git branching](http://learngitbranching.js.org/)

#### How to merge all md files

`pandoc toc.md code-commenting.md javascript.md es6.md react.md git.md git-flow.md typescript.md reactive-programming.md angular2.md css.md jwt.md design-patterns.md unix-commands.md mongo.md not-to-neglect.md resources.md note.md -f markdown -t markdown -s -o readme.md`
