# Modular Angular App Design

## Directory Structure

Each module then has its own sub-directory and a file for directives, controllers, filters and services and a directory for views
The meaning of files and folders are as follows:
•	vendor: contains folders for the various vendor libraries such as AngularJS, and 3rd party libraries managed via Bower
•	doc: Clear One web-component
•	node_modules: Node.js modules for various Grunt tasks, usually you don’t have to do anything about this folder
•	test: contains folders for the files like karma tests
•	src: with app.js and module folders
o	assets: contains font folder, img folder and locales etc.
o	commons: contains directives, config, metadata, services, filters and related files to reuse through modules.
o	modules
	home: a module of app
•	config.js: configuration app such as routes
•	controllers.js: home module’s controller
•	directives.js: directives just using in this module
•	services.js: services just using in this module
•	views: contains folder for the templates of home module
•	style: contains folder for the stylesheet of home module
	app.js: defining your main modules
	main-ctrl.js: main controller
o	styles: main stylesheets files
•	.bowerrc: bower configuration file
•	bower.json: bower dependencies
•	package.json: npm packages dependencies
•	Gruntfile.js: grunt file with various automation tasks defined in it
•	index.html: home page for your app.

##
