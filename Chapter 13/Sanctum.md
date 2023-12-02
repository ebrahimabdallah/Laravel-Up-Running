# Sanctum
* Sanctum is an API authentication system for Laravel
* built for two tasks:
* **generating simple tokens** for your power users to use to interact with your API
* allowing **SPA Authentication** and mobile apps to latch onto your existing authentication system
* Sanctum comes preinstalled with new Laravel projects.
* if not install ,You need Manually install
```
composer require laravel/sanctum
php artisan vendor:publish --provider="Laravel\Sanctum\SanctumServiceProvider"
php artisan migrate
```
* in Kernel.php
```
'api' => [
    
    EnsureFrontendRequestsAreStateful::class,    
],
```
* any route You want to protect with sanctum
* add middleware('auth:sanctum'); to route
# Sanctum tokens manually
* Example
```
public function createToken()
{
    $user = Auth::user();
    $token = $user->createToken('api-token');

    return response()->json([
        'token' => $token->plainTextToken,
        'token_type' => 'Bearer',
    ]);
}
```
* To Check it Token
```
public function checkToken()
{
     if (Auth::guard('sanctum')->check()) {
         return response()->json(['message' => 'Token is valid']);
    } else {
         return response()->json(['message' => 'Invalid token'], 401);
    }
}
* LOOK 

![to](https://github.com/ebrahimabdallah/Laravel-Up-Running/assets/119238955/bcba622a-b03b-4dcc-95bc-d97202d0231b)
```
* Sanctum tokens never expire and may only be invalidated by revoking the token. However, if you would like to configure an expiration time for your application's API tokens,

* 'expiration' => 525600,
* you may also wish to schedule a task
```
* $schedule->command('sanctum:prune-expired --hours=24')->daily();
```
# Project
* go to Repo
https://github.com/ebrahimabdallah/Laravel-Crud-API.git
