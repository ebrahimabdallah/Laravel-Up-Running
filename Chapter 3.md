# Chapter 3
# Mvc
* Three Primary Concepts :
1) Model
 * Repersents an individual database table 
2) Controller 
  * handles the application's logic and acts as an intermediary between the models and views.
3) View
  * Repersents an template that outputs your data 

# Http Verbs:

1) Get==> Request a resourse 
2) Head==>Ask for a headeer only version Get response
3) Post==>create a resourse 
4) Put==>overwrite a resourse 
5) Put==>Modify a resourse  
6) delete==>delete
7) options==> ask server which verbs are allowed at this url

* A Clouser is type of anonymous function that you can pass around an object ,assign to a varaible,pass a parameter to other function a method or even serialize 

# Route

* Route Static => Route::get();
* non-static => $route->get();

 ```
Route::get('/', function () {
 return 'Hello, World!';
});

```
* **REST**

* Focuses on one resource at a time
* Work with predictable URL structures using HTTP verbs.
* Returns a JSON response
_________________________________

* you can create a route simple && optional parameter used question mark ? && you can use regular exprssions(regexes) 
 
* Route parameters
```
Route::get('users/{id}/friends', function ($id) {
 
});

```

* Optional route parameters

```
Route::get('users/{id?}', function ($id = 'fallbackId') {
 
});
```

* regular expressions 
```
Route::get('posts/{id}/{slug}', function ($id, $slug) {
 
})->where(['id' => '[0-9]+', 'slug' => '[A-Za-z]+'])
```
_____________________________________

* Path Perfix 
 group of routes that share a segment of their path
```
Route::prefix('dashboard')->group(function () {
 Route::get('/', function () {
  
 });
 Route::get('users', function () {
  
 });
});
```
* Fallback Routes
  which you need to define
at the end of your routes file to catch all unmatched paths
```
Route::fallback(function () {
     
});
```

* Rate Limiters
If you need to limit users to only accessing any give route(s) a certain number of
times in a given time frame

```
* RateLimiter::for('global', function (Request $request) {
        return Limit::perMinute(1000);
    });
```

* Subdomain Routing is the same as route prefixing, but it’s scoped by subdomain
instead of route prefix

```
Folio::domain('admin.example.com')
    ->path(resource_path('views/pages/admin'));

Folio::domain('{account}.example.com')
    ->path(resource_path('views/pages/admin'));
```

* Namespace Prefixes grouping routes it’s likely their controllers have a similar PHP namespace.

```
Route::prefix('dashboard')->group(function () {
 Route::get('/', function () {
  
 });

```
* Signed Routes
 provide a way to generate tamper-proof URLs or routes that include a signature. This signature is used to verify the integrity and authenticity of the route parameters.

```
URL::signedRoute('invitations', ['invitation' => 12345, 'answer' => 'yes']);
```

* Route Helper
```
route("members.show", ["id" => 10])
```
* **Rate limiting**
  
* It is used to limit a user to access the page for specified number of times
```
* Route->middleware("auth:api", "throttle:60,1")->group()
```
_______________________________________
# View

* **views** : files that describe what some particular output should look like
You might have views for JSON or XML or emails, but the most common views in a web framework output HTML

* Simple view
```
Route::get('/', function () {
 return view('home');
});
```

* Passing variables to views
```
Route::get('tasks', function () {
 return view('tasks.index')
 ->with('tasks', Task::all());
});
```
* Sometimes it can become a hassle to pass the same variables over and over

* It’s possible to share certain variables with every template or just certain templates

```
view()->share('variableName', 'variableValue');
```

# controllers
* are essentially classes that organize the logic of one or more routes together in one place

* Like as the traffic cops that route HTTP requests around
your application

* Command
```
php artisan make:controller NameContoller 
```
* **Artisan** can be used to run migrations, create users and other
database records manually, and perform many other manual, one time tasks

* request() helper to represent the HTTP request
* only() method allows you to retrieve only the specified keys from the request's
* get() is used when you want to add queries and all() is used to get all data, without using any condition.

* **Typehints in PHP** putting the name of a class or inter‐
face in front of a variable in a method signature:
```
public function __construct(Logger $logger) 
{
}
```
* **Injecting Dependencies**
 is the process of providing the required dependencies to a class or component from an external source, typically through constructor parameters or method arguments. This enables the class or component to use the provided dependencies to perform its functionality.

* **Single Action Controllers**
when a controller should only service a single
route
* Using the __invoke() method
 
```
public function __invoke(User $user)
{

}
```
* Command
```
php artisan make:controller NameController --invokable
```
* Implicit Route Model Binding way to use route model binding is to name your route parameter some‐
thing unique to that model

```
Route::get('conferences/{conference}', function (Conference $conference) {
 return view('conferences.show')->with('conference', $conference);
});
```
* Custom Route Model Binding
To manually configure route model bindings,
```
Route::get('events/{event}', function (Conference $event) {
 return view('events.show')->with('event', $event);
});
```
_________________________________________________________

* **Route caching** is especially useful in production environments where performance is crucial
* It helps reduce the overhead of route resolution and can significantly improve the response time of your application.

```
php artisan route:clear


php artisan route:chace
```
# CSRF
* Cross Site Request forgey
* Protection is an important security feature provided by Laravel to prevent unauthorized requests from being processed by your application
* using in all routes in Laravel except **"read-only"** routes 
 ```
<form action="/tasks/5" method="POST">
 <?php echo csrf_field(); ?>
 <!-- or: -->
 <input type="hidden" name="_token" value="<?php echo csrf_token(); ?>">
 <!-- or: -->
 @csrf
</form>
```
* in javascript 
```
<meta name="csrf-token" content="<?php echo csrf_token(); ?>" id="token">
```
* When making AJAX requests
```
$.ajaxSetup({
 headers: {
 'X-CSRF-TOKEN': $('meta[name="csrf-token"]').attr('content')
 }
});
```
* With Axios
```
window.axios.defaults.headers.common['X-CSRF-TOKEN'] =
 document.head.querySelector('meta[name="csrf-token"]');
```
* Laravel will check the X-CSRF-TOKEN on every request, and valid tokens passed there
will mark the CSRF protection as satisfied


# Redirects
1) redirect()->to('')
2) redirect('')
3) Redirect::to('')
4) Route::redirect('redirect-by-route','')
5) redirect()->back()
6) redirect()->route()
7) redirect()->to()
8) redirect()->with()
9) redirect()->withInput()

* Other Redirect Method
* home()
* away() 
* secure() 
* action() : function is used to generate the URL for a given controller action.
 * guest() :middleware can be assigned to routes or controller actions either in the route definition or in the controller's constructor or method.
 * intended():Authentication successful   
* **Old** function retrieves an old input value flashed into the session  
* **abort function** throws an HTTP exception which will be rendered by the exception handler
* abort()
* abort_if()
* abort_unless()
```
abort(403);

abort_unless(Auth::user()->isAdmin(), 403);

abort_if(! Auth::user()->isAdmin(), 403);

```
* **assertDatabaseCount**
Assert that a table in the database contains the given number of records

* **assertDatabaseHas** Assert that a table in the database contains records matching the given key or value query constraints
* **assertDatabaseMissing**
Assert that a table in the database does not contain records matching the given key or value query constraints
