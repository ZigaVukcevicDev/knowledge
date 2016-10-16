## Design patterns

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

This pattern uses an `event system` that sits between the objects wishing to receive notifications (`subscribers`) and the objects firing the events (`publishers`).

```
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
```
The goal is to avoid dependencies between `publisher` and `subscriber` (so called `decoupling`).
