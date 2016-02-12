## Reactive programming

It is a way to build an app using events and reacting to them, using Reactive Extensions﻿ library like RxJS (RxJava...).

`Listener` is called an `observer`﻿, and the `stream`, `an observable`﻿. A stream is an ordered sequence of events. This is well-known design pattern: the observer﻿ pattern.

Observables are very close to arrays. An array is a collection of values, like an observable. An observable only adds the concept of values over time: in an array, you have all the values at once, while the values will come over time in an observable, maybe every few minutes.

Every observable, just like every array, can be transformed:

- `take(n)`﻿ will pick the n first events
- `map(fn)`﻿ will apply fn﻿ to each event and return the result
- `filter(predicate)`﻿ will only let through the events that fulfill the predicate
- `reduce(fn)`﻿ will apply fn﻿ to every event to reduce the stream to a single value
- `merge(s1, s2)`﻿ will merge the streams
- `subscribe(fn)`﻿ will apply fn﻿ to each event it receives
- and much more...

```
[1, 2, 3, 4, 5]
  .map(x => x * 2)
  .filter(x => x > 5)
  .forEach(x => console.log(x)); // 6, 8, 10
```

RxJS let us build an observable from an array.

```
Observable.fromArray([1, 2, 3, 4, 5])
  .map(x => x * 2)
  .filter(x => x > 5)
  .subscribe(x => console.log(x)); // 6, 8, 10
```

But an observable is more than a collection. It is an asynchronous collection, where the events arrive over time.

```
let input = $('input');

Observable.fromEvent(input, 'keyup')
  .subscribe(() => console.log('keyup!'));

  input.trigger('keyup'); // logs "keyup!"
  input.trigger('keyup'); // logs "keyup!"
```

You can build observables from AJAX requests, browser events, Web sockets responses, a promise, whatever you can think of.

Observable.create﻿ takes a function that will emit events on the observer﻿ given as parameter. Here it simply emits one event for the demonstration.

```
let observable = Observable.create((observer) => observer.next('hello'));

observable.subscribe((value) => console.log(value));
// logs "hello"
```

Here, the range﻿ method we are using to create the events will iterate from 1 to 5 and then emit the 'completed' signal:

```
Observable.range(1, 5)
  .map(x => x * 2)
  .filter(x => x > 5)
  .subscribe(x => console.log(x), error => console.log(error), () => console.log('done'));
// 6, 8, 10, done
```

### Reactive programming in Angular 2

The EventEmitter﻿ has a method `subscribe()`﻿ to react to events and this method can receive three parameters:

- a method to react on `events`
- a method to react on `errors`
- a method to react on `completion`

```
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
```
