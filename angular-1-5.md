## Angular 1.5

### Components

Component is normally build out of `controller` and `template`.

#### Component file 
_e.g. avatar.component.js_

```
(function() {
    'use strict';

    angular
        .module('SomeModule')
        .component('avatar', {
            controller: 'AvatarController',
            controllerAs: 'avatarCtrl', // alias for controller name in view instead of $ctrl
            template: function($templateCache) {
                return $templateCache.get('./some-path/avatar.component.html');
            },
            transclude: true,
            bindings: {
                url: '@'
            }
        });

})();
```

#### Controller file 
_e.g. avatar.controller.js_

```
(function() {
    'use strict';

    angular
        .module('SomeModule')
        .controller('AvatarController', AvatarController);

    function AvatarController() {
        var vm = this;
        vm.userAvatar = {};
        vm.hasAvatar = hasAvatar;

        function hasAvatar() {
            return !_.isUndefined(vm.url) && 
                   !_.isNull(vm.url) && 
                   vm.url.length > 0;
        }
    }

})();
```

#### View file 
_e.g. avatar.component.html_

```
<div 
    class="user__avatar" 
    ng-if="avatarCtrl.userAvatar"
    ng-style="{'background-image': avatarCtrl.hasAvatar() ? 
               'url(' + avatarCtrl.url + ')' : 
               'url(/images/profile-avatar-placeholder.png)'}
">{{ avatarCtrl.someProperty }}</div>

// or two way data binding
<input type="text" ng-model="avatarCtrl.anotherProperty" />

// or event handling
<button ng-click="avatarCtrl.someFunction()"></button>

```

### Lifecycle Hooks

#### $onInit()

This lifecycle hook will be executed when all controllers on an __element have been constructed__ and __after their bindings are initialized__. This hook is meant to be used for any kind of initialization work of a controller.

```
    function SomeController() {
        var vm = this;
    
        vm.$onInit = function() {
            vm.foo = 'bar';
            vm.bar = 'foo';    
        };
    }
};
```

#### $onChanges(changes)

This hook allows us to react to changes of one-way bindings of a component.

In component

```
    bindings: {
        user: '<'
    }
```  
            
In controller

```            
    this.$onChanges = function(changes) {
        this.user = changes.user.currentValue;
    };
```

#### $onDestroy()

A hook that is called when its containing scope is __destroyed__. We can use this hook to release external resources, watches and event handlers.

#### $postLink()

// TODO

### Bindings

```
    bindings: {
        user: '<' // For one-way bindings, using expression
        user: '=' // For two-way binding, using expression
        title: '@' // For attribute hardcoded value
        onDelete: '&' // Callbacks for component event 
    }
```

### Three types of components 
    
1. Presentation (stateless) component
    - display user interface
    - stateless (dumb / pure)
    - data arrives __via bindings__ (inputs), leaves __via events__ (outputs)

2. Business (stateful) component
    - access service & state
    - stateful (smart / impure / container)
    - do not provide interactive user interface
    - render other components

3. View (router) component
    - build the current view (from URL)
    - specialist (smart / router) components
    - create components dynamically (via a Router)
    - can be entry points to the application

### Communicating between components

<img src="/images/angular-1-5-communication-components.png" />

### Standard transcludion

It is transplanting DOM nodes into another component.

_View file of controller_ 
 
```
<modal heading="Here goes some heading">
    <p>Here goes some content.</p>
    <p>
        <a href="#">With some more content.</a>
    </p>
</modal>
```

_View file of modal component_

```
<div>
    <h2>{{modalCtrl.heading}}</h2>
    <a href="#" ng-click="modalCtrl.close()">X</a>
    <div ng-transclude></div> // NOTE: This will output content of modal component 
</div>
```

_Component file_

```
bindings: {
    heading: '@'
},
controllerAs: modalCtrl,
transclude: true,

```

_Controller file_ 

```
vm.close = function() { ... }
```

### Multi-Slot transcludion

// TODO
