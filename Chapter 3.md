# Chapter 3
 * Mvc You Have Three Primary Concepts :
1) Model
 * Repersents an individual database table 
2) Controller 
  * handles the application's logic and acts as an intermediary between the models and views.
3) View
  * Repersents an template that outputs your data 

* Http Verbs:

1) Get==> Request a resourse 
2) Head==>Ask for a headeer only version Get response
3) Post==>create a resourse 
4) Put==>overwrite a resourse 
5) Put==>Modify a resourse  
6) delete==>delete
7) options==> ask server which verbd are allowed at this url

* A Clouser is type of anonymous function that you can pass around an object ,assign to a varaible,pass a parameter to other function a method or even serialize 

 ```
Route::get('/', function () {
 return 'Hello, World!';
});

```
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
