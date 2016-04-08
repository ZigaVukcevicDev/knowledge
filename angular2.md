## Angular 2

### Components and directives

#### Components

1. For register component we use `@Component` meta-data annotation.
2. Component is a directive which use shadow DOM to create encapsulate visual behavior called components. Components are typically used to create UI widgets.
3. Component is used to break up the application into smaller components.
4. @View decorator or template url template are mandatory in the component.

```
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
```

#### Directives

1. For register directives we use `@Directive` meta-data annotation.
2. Directives is used to add behavior to an existing DOM element.
3. Directive is use to design re-usable components.
4. Directive don’t have View.

```
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
```
In summary

Write a `component` when you want to create a reusable set of DOM elements of UI with custom behaviour.
Write a `directive` when you want to write reusable behaviour to supplement existing DOM elements.

### ViewEncapsulation

// TODO: read this https://toddmotto.com/emulated-native-shadow-dom-angular-2-view-encapsulation
