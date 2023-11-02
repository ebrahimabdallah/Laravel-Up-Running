
# Why Blade 

* Blade offers several advantages that make it a preferred choice for building web applications
1) Clean and Readable Syntax
2) Template Inheritance
3) Sections and Yielding
4) Includes and Components
5) Automatic Escaping
 
# Echo 
* In Blade templates in Laravel, you can use the {{ }} or {!! !!} syntax to output content to the HTML page
*  skip echo with @
  
# Control Structure
* Blade templates provide control structures that are similar to PHP, making them familiar to developers. 
* Conditionals 
```
@if (Condition)
 // print any result
@else
//
@end if 
```
* Loop 

* Forelse is a Foreach that allows you a program in afallback if the object you're iterating over is empty 

```
@foreach($users as $user)
{{$user->name}}
@endforeach

@while($user =array_pop($users)
{{$user->orSomething()}}
@endwhile
```
* when used within a foreach or forelse this variable will return a std Class object with these properties 
* $loop->index: The current iteration index (0-based).
* $loop->iteration: The current iteration index (1-based).
* $loop->first: A boolean indicating whether it's the first iteration.
* $loop->last: A boolean indicating whether it's the last iteration.
* $loop->even: A boolean indicating if the iteration is even (useful for zebra striping in tables, for example).
* $loop->odd: A boolean indicating if the iteration is odd.
* $loop->depth: The current depth of nested loops.
* $loop->parent: The parent property allows you to access the properties of the parent loop if you are within a nested loop.
* $loop->count: The count property provides the total number of items in the current loop

```
<ul>
@foreach ($pages as $page)
 <li>{{ $loop->iteration }}: {{ $page->title }}
 @if ($page->hasChildren())
 <ul>
 @foreach ($page->children() as $child)
 <li>{{ $loop->parent->iteration }}
 .{{ $loop->iteration }}:
 {{ $child->title }}</li>
 @endforeach
 </ul>
 @endif
 </li>
@endforeach
</ul>
```

# Template inheritance 
* is a powerful feature in Laravel Blade that allows you to create a master layout template and extend or override sections in child templates


```
* parent page 


<!DOCTYPE html>
<html>
<head>
    <title>@yield('title')</title>
</head>
<body>
    <header>
        @section('header')
            <h1>My Website</h1>
        @show
    </header>

    <div class="content">
        @yield('content')   // in this palce  write code page other and display in this 
    </div>

    <footer>
        @section('footer')
            &copy; {{ date('Y') }} My Website
        @show
    </footer>
</body>
</html>



* chiled page

@extends('layouts.app')

@section('title', 'Home Page')

@section('content')
    <h2>Welcome to the Home Page</h2>
    <p> content of the home page.</p>
@endsection


```

* **Extends**
directive in Blade templates promotes maintainability, reusability, and consistency in your web application's design and layout. It simplifies the process of creating and updating web pages while keeping your code organized.

* **include**
* includeWhen is used to conditionally include a view based on a specified condition
* includeFirst is used to include the first view that exists from a list of views
* includeIf is used to include a view if it exists. It's helpful when you want to include a subview only if the view file is present
```
{{-- Include a view if it exists --}}
@includeIf('sidebars.admin', ['some' => 'data'])

{{-- Include a view if a passed variable is truth-y --}}
@includeWhen($user->isAdmin(), 'sidebars.admin', ['some' => 'data'])

{{-- Include the first view that exists from a given array of views --}}
@includeFirst(['customs.header', 'header'], ['some' => 'data'])

```
* @each  directive allows you to iterate over a collection and render a Blade view for each item in the collection

```
<div class="sidebar">
 @each('partials.module', $modules, 'module', 'partials.empty-module')
</div>


<div class="sidebar-module">
 <h1>{{ $module->title }}</h1>
</div>


<div class="sidebar-module">
 No modules :(
</div>


```
# Stack 
* **Why**
*  can utilize stacks to manage CSS and JavaScript files for different sections or pages of your website without replacing the others

```
//push somethings to bottom of stack
@push('scripts')
//
@endpush

//push somethings to top of stack
@prepend 
//
@endprepend
```

Components and slots provide similar benefits to sections, layouts, and includes; however, some may find the mental model of components and slots easier to understand

```
php artisan make:component Alert

php artisan make:component Forms/Input
```
default slot is convenient for creating flexible and reusable components
multiple named slots in a component if you need to insert content into different areas of the component's view.

```
@slot('title')
 Password validation failure
 @endslot
```

# Aliasing a component to be a directive

can use to make your components even easier to call
```
Blade::component('partials.modal', 'modal');
 partials.modal=>the location of the component 
 model=>name of your desired directive
```


# Binding Data to Views Using View Composers

* Problem ? 
find yourself using a header partial or something similar that requires some data multiple
will you have to pass that data in from every
route definition that might ever load that header partial?

* Solution : **view composer**

* it allows
you to define that any time a particular view loads, it should have certain data passed
to it—without the route definition having to pass that data in explicitly

```
* Passing sidebar data in from every route

Route::get('home', function () {
 return view('home')
 ->with('posts', Post::recent());
});

Route::get('about', function () {
 return view('about')
 ->with('posts', Post::recent());
});

```

* **LooK**
* If you find yourself repeatedly passing the same data to multiple views in your application, using view composers or view creators will help you centralize this process and make your code more maintainable.

* Sharing a variable globally

* Steps 
1) Create a custom ViewComposerServiceProvider
2) Using view()->share() makes the variable accessible to every view
```
public function boot()
{
 ...
 view()->share('recentPosts', Post::recent());
}

* in view

<ul>
    @foreach ($recentPosts as $post)
        <li>{{ $post->title }}</li>
    @endforeach
</ul>

```
* **View-scoped view composers with closures**

* you can create a view composer with a closure to provide data to a specific view, rather than globally. 
* View scoped composers are useful when you only need to bind data to a single view or a limited set of views. 
```

    View::composer('myview', function ($view) {
        $view->with('customData', Post::recent());
    });


```

* **View-scoped view composers with classes**

* most flexible but also most complex option is to create a dedicated class
for your view composer

```
class ProfileComposer
{
    public function compose(View $view): void
    {
        $view->with('count', $this->users->count());
    }
}

```
* Attaching A Composer To Multiple Views
```
View::composer(
    ['profile', 'dashboard'],
    MultiComposer::class
);

```

# Blade Service Injection

* feature in Laravel that allows you to directly inject a service or a dependency into a Blade view without the need to resolve it explicitly in your view or controller

* first parameter of inject is the name of the variable you’re injecting, and
the second parameter is the class or interface that you want to inject an instance of.


```
*  direct in view 

@inject('userRepository', 'App\Repositories\UserRepository')

<ul>
    @foreach ($userRepository->getAllUsers() as $user)
        <li>{{ $user->name }}</li>
    @endforeach
</ul>
_______________________________
* route && view
Route::get('backend/sales', function (AnalyticsService $analytics) {
 return view('backend.sales-graphs')
 ->with('analytics', $analytics);
});


<div class="finances-display">
 {{ $analytics->getBalance() }} / {{ $analytics->getBudget() }}
</div>
```
_______________________________________
# Custom Blade Directives

* useful when they simplify some form of
repeated logic

```
public function boot()
{
 Blade::directive('ifGuest', function () {
 return "<?php //command?>";
 });
}

```
* Write a condition in one place and use it in any part

* Custom Directive Result Caching
```
// AppserviceProvider.php 


public function boot():void
{
Blade::directive('ٍslugify', function () {
 $slug = strtolower($text);

  #slug =str_replace("","-",$slug);

   return slug ;

});
}
```
* in web route
```
* create a clouser route

Route::get("cutom-directive",functio(){
 return view('user');

});
```
* in view user
```
@slugify("Ebrahim Reda Abdallah")
```
 * out_put
  
```
ebrahim reda abdallah 
```




* The problem with this idea is that it assumes this directive will be
recreated on every page load. However, Blade caches aggressively,
so you’re going to find yourself in a bad spot if you try this.

* Parameters in Custom Blade Directives

```
// Binding
Blade::directive('newlinesToBr', function ($expression) {
 return "<?php echo //command ?>";
});

// In use
<p>@newlinesToBr($message->body)</p>

```
* Easier way to create custom if directive

```
Blade::if('ifPublic', function () {
 return (app('context'))->isPublic();
});
```

# The End Chapter 4
* laravel up running
* Ebrahim reda
* backend developer
  
