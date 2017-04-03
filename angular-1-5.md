## Angular 1.5

### Components



```
(function () {
    'use strict';
        angular
            .module('SomeModule')
            .controller('SomeControllerName', SomeController);

            function SomeController() {
                var vm = this;

                vm.something = {};
                vm.someFunction = someFunction;

                function someFunction() {
                    var something = false;
                    return something;
                }
            }
    
})();
```
