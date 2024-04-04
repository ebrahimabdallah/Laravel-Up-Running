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















