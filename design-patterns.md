## Design patterns

### Subject / observer

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


### Publish / subscribe

// TODO

// By subscribing to a publisher, you pass topic name and pass a callback which will be called lately.

https://msdn.microsoft.com/en-us/library/ff649664.aspx
http://stackoverflow.com/questions/15594905/difference-between-observer-pub-sub-and-data-binding

