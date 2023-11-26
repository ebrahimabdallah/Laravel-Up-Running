# Chapter 6. Frontend Components
 
# Breeze && Jetstream
* are used for authentication scaffolding in Laravel
* Breeze is more minimal and straightforward 
* Jetstream is more feature-rich and suitable for larger projects with more complex authentication requirements

* **Inertia**  is a JavaScript framework that allows you to build modern, single-page apps (SPAs) using server-side such frameworks Laravel
 

* **install Breeze**

```
composer require laravel/breeze --dev

php artisan breeze:instal

php artisan migrate

npm install

npm run dev

```

* **Jetstream** requires interactivity, so there’s no
Blade-only stack. Instead, you have two choices or Inertia/Vue 
* no React form for Jetstream

* installing 
* create project laravel

```
composer require laravel/jetstream

php artisan jetstream:install livewire

php artisan jetstream:install livewire --teams

npm install

npm run build

php artisan migrate
```

* **Laravel Fortify** is a frontend agnostic authentication backend implementation for Laravel

* **Vite** is a modern frontend build tool that provides an extremely fast development environment and bundles your code for production that combines a dev
server and Rollup-based build tooling chain
# Pagination
* when you are  the results of a database too many used it to divide a large set of results into smaller, more manageable chunks, often displayed across multiple pages

```
DB::table('posts')->paginate(number) 
```
* onEachSide() : concept of displaying a certain number of pages on each side of the current page in a pagination control.
```
Total Pages: 10

Current Page: 6

1 ... 4 5 [6] 7 8 ... 10

DB::table('posts')->paginate(10)->onEachSide(3);

```
* **LengthAwarePaginator** needs to know the length of the full result so
that it can generate links for each individual page

* Message Bag
* used to pass messages between different parts of a web application
* such : Validation Errors && Flashing Messages
* ithErrors() : send errors along with a redirect
```
redirect('dashboard')->withErrors($validator, 'login')
```

# helper 

* Checks a string (F parameter) to start with ends with or contains another string (second parameter).
```
 Str::startsWith() , Str::endsWith() , Str::contains()
```
* Str::is: used to perform wildcard pattern matching on strings. This method allows you to check if a given string matches 

* Str::slug(): Converts a string to a URL-type slug with hyphens.

* Str::after() returns everything after a given string
* Str::before() returns everything before a given string 
* Str::limit() truncates a string
```
Str::after() , Str::before() , Str::limit()
```
* Localization enables you to define multiple languages and mark any strings as targets for translation.

