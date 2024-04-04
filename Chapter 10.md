# Laravel’s Request Lifecycle

* **Entry Point**:

The request enters the application either through the index.php file in the public directory (for web requests) or through the artisan command-line tool (for console requests).

* **Routing**:
The request is matched to a route defined in the routes/web.php or routes/api.php file or any custom route files.
Routes define the URI pattern and associated controller method or closure.

* **Middleware**:
Middleware can intercept the request before it reaches the route handler.
Middleware can perform tasks like authentication, logging, modifying request data, etc.

* **Controller Dispatch**:
If the route points to a controller, Laravel dispatches the controller action associated with the route.
The controller action handles the request logic, such as fetching data, processing it, and preparing a response.

* **Request Lifecycle within the Controller**:
Inside the controller, additional tasks can be performed, such as validating the request data, interacting with models, invoking services, etc.

* **Model Interaction**:
If the controller needs to interact with the database, it typically does so through Eloquent models.
Models encapsulate the application's data structure and provide an abstraction layer for database operations.

* **Response Creation**:
After the controller has processed the request and gathered any necessary data, it returns a response.
Responses can be in various formats, such as HTML, JSON, etc.

* **Middleware (Outgoing)**:
After the controller generates the response, it passes through middleware again.
Middleware can modify the response or perform additional tasks before sending it back to the client.

* **Sending Response**:
Finally, Laravel sends the response back to the client, whether it's a web browser, mobile app, or any other client application.



# User and request state

```
<form method="POST" action="/form">
 @csrf
 <input name="name"> Name<br>
 <input type="submit">
</form>
```

* method()
- GET 
- POST 
- PATCH .... 


* path()
Returns the path (without the domain) used to access this page

* url()
Returns the URL (with the domain) used to access this page

* is()
Returns a Boolean indicating whether or not the current page request fuzzy-matches a provided string 
 
* ip()
Returns the user’s IP address.

* header()
Returns an array of headers 

* server()
Returns an array of the variables traditionally stored in $_SERVER

* secure()
Returns a Boolean indicating whether this page was loaded using
HTTPS

* pjax()
Returns a Boolean indicating whether this page request was loaded
using Pjax


* wantsJson()
Returns a Boolean indicating whether this request has any json
content types in its Accept headers

* accepts()
Returns a Boolean indicating whether this page request accepts a
given content type


# Files

- file()Returns an array of all uploaded files, or, if a key is passed (the file upload field name)
- allFiles()Returns an array of all uploaded files
- hasFile()Returns a Boolean indicating whether a file was uploaded at the specified key

# Persistence





* JSON responses
  common way to send structured data back to the client in response to an HTTP request. Here's a summary of how JSON responses are handled in Laravel
```
return response()->json(Model::all());
```
* **persistence** refers to the process of storing and retrieving data in a database, ensuring that the data remains available even after the application is shut down or restarted. Laravel provides several tools and techniques for working with databases and ensuring data persistence

* flash()
Flashes the current request’s user input to the session

* flashOnly()
Flashes the current request’s user input for any keys in the provided array.


* flashExcept()
Flashes the current request’s user input, except for any keys in the
provided array.

* old()
Returns an array of all previously flashed user input 

* flush()
Wipes all previously flashed user input.

* cookie()
Retrieves all cookies from the request 

* hasCookie()
Returns a Boolean indicating whether the request has a cookie for the given key



# Middleware 
- acts as a bridge between the incoming HTTP request and your application's logic. It provides a way to filter and modify requests and responses in a flexible and centralized manner.

* Creating Custom Middleware

You can create custom middleware in Laravel by implementing the handle method in a middleware class. This method receives the request, performs any necessary processing, and optionally passes the request to the next middleware in the stack.

* Global Middleware:

Global middleware applies to all HTTP requests handled by your application. These are registered in the $middleware property of the App\Http\Kernel class.
Global middleware is suitable for tasks that need to be performed on every request, such as logging or setting headers.


* Using middleware groups
Middleware groups are essentially prepackaged bundles of middleware
that make sense to be together in specific contexts


* Middleware Parameters:

Middleware can accept parameters, allowing you to customize their behavior based on specific conditions or configurations.

```
public function handle(Request $request, Closure $next, $role): Response
{
 if (auth()->check() && auth()->user()->hasRole($role)) {
 return $next($request);
 }
 return redirect('login');
}
```

* rate limiting middleware
- allows you to control the rate at which clients can access certain routes or endpoints within your application


```
php artisan make:middleware RateLimitMiddleware

```
```
class RateLimitMiddleware
{
    public function handle($request, Closure $next)
    {
        $ip = $request->ip();
        $key = "rate_limit:$ip";

        $limit = 100; // Example: allow 100 requests per hour
        $interval = 3600; // 1 hour in seconds

        $requests = Redis::get($key) ?: 0;

        if ($requests >= $limit) {
            return response()->json(['message' => 'Too many requests'], 429);
        }

        Redis::incr($key);
        Redis::expire($key, $interval);

        return $next($request);
    }
}
```

```
Route::middleware('rate.limit')->get('/example', function () {
    return response()->json(['message' => 'This route is rate-limited']);
});

```































