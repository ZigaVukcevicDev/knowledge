## Angular 1.5

### Components


```
(function () {
  'use strict';

  angular
      .module('SomeModuleName')
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
