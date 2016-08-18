## React

### JSX

This is a sample of `JSX` (JavaScript XML).

```
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

```

### Properties

This is sample of using `props`.

```
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
```

#### Types of properties

Example of determining types.

```
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
```

### Events

// TODO

### State

// TODO

### Bind this

It’s not always clear what `this` is going to refer to in your code. As functions in JS are objects, every function has it own `this`. Samples:

#### Alias This

```
    var component = this;
    component.setState({ loading: true });

    fetch('/').then(function loaded() {
        component.setState({ loading: false });
    });
```

#### Bind This

```
    this.setState({ loading: true });

    fetch('/').then(function loaded() {
        this.setState({ loading: false });
    }.bind(this));
```

#### React Component Methods

React allows you to define arbitrary methods on your component classes and these methods are automatically bound with the correct context for `this` when you create your components with `React.createClass`. This allows you move your callback code out onto your component.

```
React.createClass({
    componentWillMount: function() {
        this.setState({ loading: true });

        fetch('/').then(this.loaded);
    },
    loaded: function loaded() {
        this.setState({ loading: false });
    }
});
```

#### ES2015 Arrows

They always use the value of `this` from the enclosing scope.

```
    this.setState({ loading: true });

    fetch('/').then(() => {
        this.setState({ loading: false });
    });
```

### Stateless functional components

A simpler way to define components called `stateless functional components`. These components use plain JavaScript functions. Stateless functional components `don’t support state or lifecycle methods`.

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

These methods are executed at specific points in a component's lifecycle.

#### componentWillMount

Invoked only once, both on the client and server, immediately before the initial rendering occurs.

[See sample](http://codepen.io/be-codified/pen/YWRgBd?editors=0011)

If you call `setState` within this method, `render()` will see the updated state and will be invoked only once (ignoring that state changed).

[See sample](http://codepen.io/be-codified/pen/dXQLrA?editors=0010)

Params: none

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
