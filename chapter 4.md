
# Why Blade 

* Blade offers several advantages that make it a preferred choice for building web applications
1) Clean and Readable Syntax
2) Template Inheritance
3) Sections and Yielding
4) Includes and Components
5) Automatic Escaping
 
# Echo 
* In Blade templates in Laravel, you can use the {{ }} or {!! !!} syntax to output content to the HTML page

* **Control Structrue** 
 * Most control structure in blade will be vert familiar 
 * Many directly echo the name and structure of the same tag in Php 
 
# Conditionals 
```
@if (Condition)
 // print any result
@else
//
@end if 
```
# Loop 

* Forelse is a Foreach that allows you a program in afallback if the object you're iterating over is empty 

```
@foreach($users as $user)
{{$user->name}}
@endforeach

@while($user =array_pop($users)
{{$user->orSomethine()}}
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
