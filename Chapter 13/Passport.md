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
* in config/auth.php
```
'guards' => [
    // ...
    'api' => [
        'driver' => 'passport',
        'provider' => 'users',
    ],
],

```
* route
```
Route::middleware('auth:api')->group(function () {
    // Your API routes here
});

```
* Client UUIDs
```
php artisan passport:install --uuids
```
* Deploying Passport
```
php artisan passport:keys
```
* Loading Keys From The Environment
```
php artisan vendor : publish --tag=passport-config
```
* Token Lifetimes
```
Passport::tokensExpireIn(now()->addDays(15));
```
* CREATING A PERSONAL ACCESS CLIENT
```
php artisan passport:install

php artisan passport:client --personal
```
* Passport  authenticate users in four different
* Two are traditional OAuth 2.0 grants (the password grant and authorization code grant)
* two are convenience methods that are unique to Passport (the personal token and synchronizer token)

