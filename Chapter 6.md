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
