# Modular Angular App Design

### Directory Structure

Each module then has its own sub-directory and a file for directives, controllers, filters and services and a directory for views
#### The meaning of files and folders are as follows:
```
your-project/
  |- doc/
  |- node_modules/
  |- test/
  |- src/
  |  |- assets/
  |  |  |- <static files>
  |  |- common/
  |  |  |- <reusable code>
  |  |- modules/
  |  |  |- home
  |  |  |  |- config.js
  |  |  |  |- controllers.js
  |  |  |  |- directives.js
  |  |  |  |- services.js
  |  |  |  |- filters.js
  |  |  |  |- views/
  |  |  |- login
  |  |  |- app.js
  |  |  |- main-ctrl.js
  |  |- styles/
  |  |  |- main.styl
  |- vendor(bower_components)/
  |  |- angular-bootstrap/
  |  |- bootstrap/
  |  |- placeholders/
  |- .bowerrc
  |- bower.json
  |- Gruntfile.js
  |- index.html
  |- package.json
```

### Defining The Modules

```sh
// Define all your commons components
angular.module('app.resources', []);
angular.module('app.securities', []);
angular.module('app.directives', []);

// Define your modules 
angular.module('app.modules', [
   'app.home',
   'app.login'
]);

// Define your 3rd Party Modules 
angular.module('app.third-party', [
 'ui.bootstrap'
]);

// Lastly, define your "main" module and inject all other modules as dependencies
angular.module('YourApp', [
    'app.third-party',
    'app.resources',
    'app.securities',
    'app.directives',
    'app.modules'
  ]
);

```

Creating a YourApp Modules allows us to inject all our other modules which in turn allows each of our other modules to access each other
The YourApp also allows us to do routing and use ui-view in our index.html file:

```sh
<!DOCTYPE HTML>
<html lang="en-US" data-ng-app="YourApp">
<head>
  <meta charset="UTF-8">
  <title>Your App</title>
</head>
<body data-ng-controller="MainCtrl">
    <div ui-view></div>
</body>
</html>
```

Then you defined your routes on the other modules

```sh
// src/modules/home/config.js
angular.module(‘module.home’, []) //define your module
  .config(
    [‘$stateProvider’,
      function($stateProvider) {
        $stateProvider
          .state(‘/home’, {
            templateUrl: ‘modules/home/views/home.html’,
            controller: 'HomeCtrl’
          })
   // ...
```

### Implementing Your Modules

Now when we go to add a controller/directive/service/filter to a module, we open up the appropriate file within that module and simply use the appropriate module name when we define it.

```sh
// app/modules/home/controllers.js
angular.module(‘module.home’)
  .controller(‘HomeCtrl’, function($scope) {
     $scope.patients = ‘something’;
  });
```
