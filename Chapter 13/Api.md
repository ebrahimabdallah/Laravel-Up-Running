# Writing Api 
* Why do we use Api ...???
* I will not talk much, but I will describe you through this talking picture

  
![What-Is-API-Development](https://github.com/ebrahimabdallah/Laravel-Up-Running/assets/119238955/c3f1dcb0-fca1-4674-b2da-a313bc9cffa2)

* What is a Api
* An API (Application Programming Interface) is a set of rules and protocols that allows one software application to interact with another. 

 ![images](https://github.com/ebrahimabdallah/Laravel-Up-Running/assets/119238955/60c21d2a-fed8-42ea-bd6f-b7c249d0b120)

* Get :Retrieves all items
* Post: create resources
* Update :Update a specific item by ID.
* delete:Deletes a specific item by ID.

-----------------------
* **Status**
* 200: OK
* 201: Object created
* 204: No content
* 400: Bad request.
* 401: Unauthorized
* 403: Forbidden
* 404: Not found
* 503: Service unavailable

# REST
* **Representational state transfer** architectural style for building APIs

* designed to be stateless. 
* Stateless means that each request from a client to a server must contain all the information needed to understand and fulfill that request. The server does not store any information about the client's state between requests

* Laravel’s API resource controllers are like normal resource controllers but expacted 
create() && edit() functions

* to create Api resource
```
php artisan make:controller Api/DogController --api
```
* Model
```
php artisan make:model Dog --api
```

* headers play a crucial role in handling various aspects of the HTTP request and response cycle.

* JSON API is a standard for how to handle many of the most common tasks in building JSON-based APIs
# Generated API resource collection
* looking to generate an API resource collection for a model in Laravel
```
php artisan make:resource NameCollection
```
* Path [app/Http/Resources/NameCollection.php],
```
public function toArray(Request $request): array
 {
return [
'name' => $this->name,
 'breed' => $this->breed,
 'friends' => ModelName::collection($this->friends),
];
}
```

#  loading API relationship
```
return [
   'bones' => BoneResource::collection($this->whenLoaded('bones')),
  'bones' => $this->when(
 $request->get('include') == 'bones',
 BoneResource::collection($this->bones)
 ),];
```
# API Authentication

* provides two primary tools for authenticating Api Request
* Sanctum
* Passport
  

# Passport
* Laravel Passport is a full OAuth2 server implementation; it provides a convenient way to build a full authentication system for your Laravel application
* Why ?
*  because APIs are stateless, we can’t rely on the same session-based authentication that we do in normal
* To install
```
composer require laravel/passport

php artisan migrate

php artisan passport:install

```
* in Kernel.php
```
'web' => [
     \Laravel\Passport\Http\Middleware\CreateFreshApiToken::class,
],
```
* Passport  authenticate users in four different
* Two are traditional OAuth 2.0 grants (the password grant and authorization code grant)
* two are convenience methods that are unique to Passport (the personal token and synchronizer token)

 
# Helpers Function To enhancement
* This functions is not a rule that is binding on you, but it will improve the way you present the data and make it easier for other developers to read it and to make all same format

* Autoloading the Helper Function
* in composer.json
```
"autoload": {
    "files": [
        "app/helpers.php"
    ],
    
},
```
```
composer dump-autoload
```

* Successful Helper && SendResponse
* take three parameter
* Status && Msg && data
```
  public function sendResponse($code=200,$msg=null,$data=null)
  {
      $response=[
      'status'=>$code,
      
      'msg'=>$msg,
      
      'data'=>$data,
      
      ];
      return response()->json($response)
  }
```
* Error Function
```
     public function errorRespose($msg="Error" ,$status=500)
    {
    $response=([
    'success'=>false,
    'msg'=>$msg
    ]);
    return response()->json($response); 
    }
```

 * After Used Formatter Helper
![apitest](https://github.com/ebrahimabdallah/Laravel-Up-Running/assets/119238955/2ca92188-f73f-49dd-bba4-f2b30c6f0d10)

* Without Used
   ![api2](https://github.com/ebrahimabdallah/Laravel-Up-Running/assets/119238955/f854655f-7407-405c-9470-e86735d1fd88)

   
