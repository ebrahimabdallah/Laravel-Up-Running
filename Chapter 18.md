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



