## JavaScript (ES5 or lower)

<!---
### Primitives and object wrappers

// TODO 15
-->

### Truthy & Falsy

#### Truthy

In JavaScript, a `truthy value` is a value that translates to true when evaluated in a Boolean context. All values are **truthy** unless they are defined as **falsy**.

Examples

    if (true)
    if ({})
    if ([])
    if (42)
    if ('foo')
    if (new Date())
    ... and everything else (unless defined as falsy)


#### Falsy

A `falsy value` is a value that translates to false when evaluated in a Boolean context.

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

Functions can be combined to form new functions through function composition. The function `addThenSquare` is made by combining the functions `add` and `square`.

    const add = function(x, y) {
        return x + y;
    };

    const square = function(x) {
        return x * x;
    };

    const addThenSquare = function(x, y) {
        return square(add(x, y));
    };

<!---
### Prototype

// TODO
-->
