# Chapter 8. Artisan and Tinker


* artisan is a command-line interface (CLI) tool that comes bundled with Laravel. It provides a set of helpful commands for performing various tasks related to Laravel development. These commands allow developers to perform tasks such as generating code, running migrations, seeding databases, clearing caches, and more, all from the command line


```
php artisan make:model: Generates a new Eloquent model class.
php artisan make:controller: Creates a new controller class.
php artisan migrate: Runs any outstanding database migrations.
php artisan db:seed: Seeds the database with test data.
php artisan route:list: Lists all registered routes.

```
# clear-compiled
* Removes Laravel’s compiled class file, which is like an internal Laravel cache; run this as a first resort when things are going wrong
and you don’t know why

# down , up
* Puts your application in “maintenance mode” so you can fix an error, run migrations, or whatever else, and restores an application
from maintenance mode, respectively.

# dump-server
* Starts the dump server to collect and output dumped variables

# migrate
* Runs all database migrations.

# optimize
* Clears and refreshes the configuration and route files.

# serve
* Pins up a PHP server at localhost:8000 . (You can customize the
host and/or port with --host and --port .)

# stub:publish
* Publishes all stubs that are available for customization

# tinker
* command in Laravel is a powerful interactive shell that allows you to interact with your Laravel application directly from the command line. It provides a convenient way to interact with your application's models, database, and services without needing to create specific routes or controllers.


# docs
* Gives you quick access to Laravel docs



# Options


* -q :- Suppresses all output
* -v , -vv , and -vvv
Specifies the level of output verbosity (normal, verbose, and debug)
* --no-interaction
Suppresses interactive questions, so the command won’t interrupt
automated processes running it
* --env
Allows you to define which environment the Artisan command
should operate in ( local , production , etc.)
* --version
Shows which version of Laravel your application is running


* db:seed seeds your database, if you have configured database
seeders.

* key:generate creates a random application encryption key in
your .env file.

* In Laravel, the "cache" command provides a set of helpful commands for managing various aspects of the application's cache. These commands are useful for developers to clear and manage the cached data stored within their Laravel application.

```
Clear Cache: clear command is used to clear the application cache. This command removes all cached data 

Clear Route Cache:  command generates a route cache file for faster route registration. This command should be run whenever changes are made to routes.

Clear Configuration Cache:  cache command generates a cache file for the application's configuration files, resulting in faster configuration loading. It should be executed whenever configuration changes are made.

Clear Compiled Views:clear command removes the compiled views, which are stored in the storage/framework/views directory. This command can be helpful if you're experiencing issues with your compiled Blade views.

Clear Compiled Classes:   removes the compiled class file, which is usually stored in the bootstrap/cache directory. This command is useful if you're encountering issues related to compiled classes.

Cache Configuration:  command caches the application configuration for faster loading. This is particularly useful in production environments to improve performance.

Cache Routes:  command caches the application's routes, improving route registration performance. Again, this is beneficial in production environments.

```

* notifications
notifications:table generates a migration that creates the table for database notificati


* route
If you run route:list , you’ll see the definitions of every route
defined in the application

* session:table creates a migration for applications using database-backed sessions.
* storage:link creates a symbolic link from public/storage to storage/app/public 






