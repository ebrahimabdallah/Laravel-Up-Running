# Collecting and Handling User Data
 
# Injecting a Request Object

* $request->all() retrieves an associative array containing all the input data from the request.

* $request->except() used to retrieve all of the input data from the request except for the specified parameter

```
 $filteredData = $request->except(['password', 'user_id']);
// output all expect passwors && user_id
```
* $request->->only() sed to retrieve a subset of the input data from the request based on specified keys.

```
    $selectedData = $request->only(['username', 'email']);

// output 
"username" => "Ebrahim"
"email" => "ebrahim@email.com"
```
* $request->has() used to check if the request contains a given input key
*  return a boolean value
```
if ($request->has('username')) {
         
        return 'Username is exist in the request';
    } else {
         
        return 'Username is not exist in the request';
    }
```
* $request->missing() is its inverse
* $request->whenHas()  you can define the behavior when the request either does or doesn’t 
* first parameter return when field exists
* second is returned when it doesn’t

* $request->whenFilled() method allows you to define the values either when the field is filled or when it isn’t.
* return first parmeter when field
* return Seceond parmeter when Not field

* mergeIfMissing() method you can add a field to the request when it is not present and while defining its value
```
$shouldSend = $request->mergeIfMissing('send_newsletter', 0);
```

* $request->method() returns the HTTP verb for the request 
* $request->isMethod() checks whether it matches the specified verb.

* different $request->dump() && $request->dd

* $request->dump()  continues execution of the script 
* $request->dd() dumps and then stops execution of the script

* Uploaded File 
* use enctype="multipart/form-data" in form

# Validation

* validate() .
* validate() method checks the incoming data from
```
public function store ()
{
$request->validate([
'title'=>'required',
'body'=>'required'
]);
}
```
```
fieldname': 'rule|otherRule|anotherRule'

OR

'fieldname': ['rule','otherRule', 'anotherRule'] .
```
* safe method is used for validation within the Eloquent ORM 

# Custom Rule Objects

* If the validation rule you need doesn’t exist in Laravel

```
php artisan make:rule RuleName
```
* in app/Rules/{RuleName}.php.
```
public function passes($attribute , $value)
{
return strpos($value ,'example') !==false ;
}
```
* in Controller 
```
Public function store()
{
$request->validate([
'value'=>['required',now RuleName];
]);
}
```

# Create a Request 

```
php artisan make:request CreateNameRequest
```
* to use in controller
  ```
public function store($request NameRequest)
{
//
}
  ```
