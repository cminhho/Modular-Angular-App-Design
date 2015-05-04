# Modular Angular App Design

### Directory Structure

Each module then has its own sub-directory and a file for directives, controllers, filters and services and a directory for views
#### The meaning of files and folders are as follows:
```
ng-boilerplate/
  |- grunt-tasks/
  |- karma/
  |- src/
  |  |- app/
  |  |  |- <app logic>
  |  |- assets/
  |  |  |- <static files>
  |  |- common/
  |  |  |- <reusable code>
  |  |- less/
  |  |  |- main.less
  |- vendor/
  |  |- angular-bootstrap/
  |  |- bootstrap/
  |  |- placeholders/
  |- .bowerrc
  |- bower.json
  |- build.config.js
  |- Gruntfile.js
  |- module.prefix
  |- module.suffix
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
angular.module('ClearOneApp', [
    'app.third-party',
    'app.resources',
    'app.securities',
    'app.directives',
    'app.modules'
  ]
);

```

### Implementing Your Modules

Now when we go to add a controller/directive/service/filter to a module, we open up the appropriate file within that module and simply use the appropriate module name when we define it.
