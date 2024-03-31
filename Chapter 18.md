 # Glossary

 * **accessor** :- A method defined on an Eloquent model that customizes how a given property will be returned
enable you to modify the data fetched from the database before it's accessed by your application's code
* Ex:-
```
    public function getFullNameAttribute($value)
    {
        return ucfirst($value); // Capitalize the first letter of the full name
    }
```

```
$user = User::find(1);
echo $user->full_name;
```

* **Active Record pattern**:- combines business logic and data manipulation in a single class, which makes code easier to understand and maintain

* **API** :-API is used to describe the set of interfaces, or affordances, any given package or library or class exposes to its consumers
* **application test**:- support for testing with Pest and PHPUnit is included out of the box and a phpunit. xml file is already set up for your application

* **Artisan** :- The tool that makes it possible to interact with Laravel applications from the command line
* **assertion** :- assertions are statements that verify the expected behavior of your application during the execution of your tests
* **authentication** :- Correctly identifying oneself as a member/user of an application is the act of authentication

* **authorization** :- defines what you’re allowed to do given your particular identification
* **Autowiring** :- is an exotic word that represents something very simple: the ability of the container to automatically create and inject dependencies. 

* **Beanstalk**:- is a fast and simple work queue. It allows you to run time consuming tasks asynchronously, such as sending emails, connecting to external APIs or processing images
* **Carbon** A PHP package that makes working with dates much easier and
more expressive

* **Cashier** :-  is a package provided by Laravel that simplifies the integration of Stripe billing services into Laravel applications.
* fluent interface to Stripe's subscription billing services. It handles almost all of the boilerplate subscription billing code you are dreading writing. In addition to basic subscription management, Cashier can handle coupons, swapping subscription, subscription "quantities", cancellation grace periods, and even generate invoice PDFs.

* **closures** are anonymous functions that can be used as callback functions or passed around as parameters to other functions or methods. 

* **contract** :- Another name for an interface.

* **controller** :-A class that is responsible for routing user requests through to the application’s services and data

* **CSRF** :- (cross-site request forgery) A malicious attack where an external site makes requests against your application by hijacking your users’ browsers 

* **Dependency injection (DI)** is a design pattern commonly used in software development, including in Laravel, to achieve loose coupling between components and improve the testability, flexibility, and maintainability of your code. Laravel's service container provides a powerful mechanism for implementing dependency injection throughout your application.


* **directive** Blade syntax options like @if , @unless , etc

* **dot notation** is commonly used to access nested arrays or objects within configuration files, language files, and other types of structured data. Dot notation provides a convenient way to access deeply nested values without having to manually traverse the entire structure

* **ager loading** Avoiding N+1 problems by adding a second smart query to your first query to get a set of related items

* **Envoy** A Laravel package for writing scripts to run common tasks on remote servers

* **Envoyer** A Laravel SaaS product for zero-down-time deployment, multiserver deployments, and se

* **event** events provide a simple observer implementation, allowing you to subscribe and listen for events that occur within your application.

* **facade** A tool in Laravel for simplifying access to complex tools,provide static access to core services in Laravel.
* **Faker** A PHP package that makes it easy to generate random data.
* **flag** A parameter anywhere that is on or off (Boolean)

 
* **Flysystem** is a filesystem abstraction library for PHP that provides a simple and unified way to interact with various filesystems, such as local filesystems, FTP servers, Amazon S3, and more.

* **Forge** Laravel product that makes it easy to spin up and manage virtual servers on major cloud providers like DigitalOcean and
AWS

* **Fortify** Laravel package designed to provide a simple and customizable authentication system for Laravel applications.


 
* **FQCN** helps Laravel locate and autoload classes without ambiguity, especially when dealing with classes that have the same name but exist in different namespaces


* **helper** A globally accessible PHP function

* **Homestead** pre-packaged Vagrant box for Laravel development. It's designed to provide a development environment that closely mirrors production environments, making it easier to develop Laravel applications locally.


* **Horizon** A Laravel package that provides tooling for managing queues
with greater nuance than Laravel’s defaults,

* **integration test** :- Integration tests test the way individual units work together and pass messages.

* **Inversion of Control (IoC)** is a design principle that promotes decoupling of components within the application. Laravel's IoC container is a powerful tool that manages class dependencies and performs dependency injection.

```
// Binding a concrete class to an interface
$this->app->bind(InterfaceName::class, ConcreteImplementation::class);

```

* **job**
A class that intends to encapsulate a single task.

* **JSON** (JavaScript Object Notation) A syntax for data representation

* **JWT** authentication provides a stateless and scalable authentication mechanism for your Laravel application. By using JWT, you can securely authenticate users and exchange information between client and server in a standardized format

* **mailable** An architectural pattern designed to encompass the functionality
of sending mail into a single “sendable” class


* **Markdown** A formatting language designed for formatting plain text and
outputting to multiple formats


* **mass assignment** The ability to pass many parameters at once to create or update
an Eloquent model

* **Memcached** An in-memory data store designed to provide simple but fast
data storage


* **middleware**
A series of wrappers around an application that filter and decorate its inputs and outputs.


* **Mockery**
A library included with Laravel that makes it easy to mock PHP
classes in your tests


* **mutator**
A tool in Eloquent that allows you to manipulate the data being
saved to a model property before it is saved to the database.

* **Nginx**
A web server similar to Apache.


* **notification**
A Laravel framework tool allowing a single message to be sent
via myriad notification channels

* **Nova**
A paid Laravel package for building admin panels for your Laravel apps.


* **NPM** (Node Package Manager)
A central web-based repository for Node packages

* **OAuth**
The most common authentication framework for APIs

* **ORM** (object-relational mapper)
A design pattern that is centered around using objects in a programming language to represent data, and its relationships, in a
relational database

* **PHPSpec**
A PHP testing framework.


* **preprocessor**
A build tool that takes in a special form of a language


* **Redis**
Like Memcached, a data store simpler than most relational databases but powerful and fast. Redis supports a very limited set of
structures and data types


* **S3** (Simple Storage Service)
Amazon’s “object storage” service


* **SaaS** (Software as a Service)
Web-based applications that you pay money to use.


* **Sanctum**
API token authentication system for single-page applications,
mobile applications, and simple token-based APIs


* **scope**
In Eloquent, a tool for defining how to consistently and simply
narrow down a query

* **Scout**
A Laravel package for full-text search on Eloquent models


* **serialization**
The process of converting more complex data

* **Socialite**
A Laravel package making it simple to add social authentication

* **soft delete**
Marking a database row as “deleted” without actually deleting it


* **Spark**
A Laravel tool that makes it easy to spin up a new subscriptionbased Saa


* **Telescope
A Laravel package for adding a debugging assistant to Laravel
apps

