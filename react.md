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
        <h1>{ this.props.text }</h1>
        <p>{ this.props.children }</p>
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