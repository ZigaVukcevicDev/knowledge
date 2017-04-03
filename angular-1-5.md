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
            controllerAs: 'avatarCtrl',
            template: function($templateCache) {
                return $templateCache.get('./app/platform/components/avatar/views/avatar.component.html');
            },
            transclude: true,
            bindings: {
                url: '@'
            }
        });

})();
```

#### Controller file (e.g. avatar.controller.js)

```
(function () {
    'use strict';

    angular
        .module('SomeModule')
        .controller('AvatarController', AvatarController);

    function AvatarController() {
        var vm = this;
        vm.userAvatar = {};
        vm.hasAvatar = hasAvatar;

        function hasAvatar() {
            return !_.isUndefined(vm.url) && !_.isNull(vm.url) && vm.url.length > 0;
        }
    }

})();
```

#### View file (e.g. avatar.component.html)

```
<div 
    class="user__avatar" 
    ng-if="avatarCtrl.userAvatar"
    ng-style="{'background-image': avatarCtrl.hasAvatar() ? 'url(' + avatarCtrl.url + ')' : 'url(/images/profile-avatar-placeholder.png)'}">
    </div>
```