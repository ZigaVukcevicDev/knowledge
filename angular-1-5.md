## Angular 1.5

### Components

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
"></div>
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

// TODO

#### $onChanges()

// TODO

#### $onDestroy()

// TODO

#### $postLink()

// TODO