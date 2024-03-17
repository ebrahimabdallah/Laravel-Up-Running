 
# Chapter 17. Helpers and Collections

* Arr::pluck($array, $value, $key = null)
Returns an array of the values corresponding to the provided key

Ex:

```
array = [
 ['owner' => ['id' => 4, 'name' => 'Tricia']],
 ['owner' => ['id' => 7, 'name' => 'Kimberly']],
];
$array = Arr::pluck($array, 'owner.name');
// Returns ['Tricia', 'Kimberly'];
```

* Arr::random($array, $num = null)
Returns a random item from the provided array.

* Arr::join($array, $glue, $finalGlue = '')
Joins the items from $array into a string

* str($string)
Used for casting stringables; is an alias for Str::of($string) 

```

str('http') === Str::of('http');
// true
```

```
Str::startsWith($haystack, $needle) ,
Str::endsWith($haystack, $needle) ,
Str::contains($haystack, $needle, $ignoreCase)

```

```
if (Str::startsWith($url, 'https')) {
 // Do something
}

...etc
```
* Limits a string to the provided number of characters.
```
Str::limit($value, $limit = 100, $end = '...')

$abstract = Str::limit($loremIpsum, 30);
// Returns "Lorem ipsum dolor sit amet, co..."

$abstract = Str::limit($loremIpsum, 30, "&hellip;");
// Returns "Lorem ipsum dolor sit amet, co&hellip;

```

```
Str::words($value, $words = 100, $end = '...')
Limits a string to the provided number of words

$abstract = Str::words($loremIpsum, 3);
// Returns "Lorem ipsum dolor..."

```

* Str::before($subject, $search) 
* Str::after($subject,$search) 
* Str::beforeLast($subject, $search) 
* Str::afterLast($subject, $search)
* Returns the subsections of a string before or after another string, or the last instance of another string.

* Str::is($pattern, $value)

* Returns a Boolean indicating whether or not a given string matches a given pattern

*  PASS A REGEX TO STR::IS()

* EX:-

```
public function is($pattern, $value)
{
 if ($pattern == $value) return true;
 $pattern = preg_quote($pattern, '#');
 $pattern = Str::replace('\*', '.*', $pattern);
 if (preg_match('#^'.$pattern.'\z#u', $value) === 1) {
 return true;
 }
 return false;
}

```

* Str::isUuid($value)
Determines whether the value is a valid UUID:

* Str::random($length = n)
Returns a random string of alphanumeric mixed-case characters of
the length specified

* Str::slug($title, $separator = '-', $language = 'en')
Returns a URL-friendly slug from a string—often used for creating
a URL segment for a name or title

* Ex:- 
```
Str::slug('Ebrahim Reda Backend Developer');
// Returns 'ebrahim-reda-backend-developer'


```

* Str::plural($value, $count = n)
Converts a string to its plural form. This function currently only
supports the English language

* return (string) Str::of(' Go to town!! ')
 ->trim() //lower
 ->replace('town', 'bed') //replace 
 ->slug(); // Returns "go-to-bed" 


* app_path($append = '')
Returns the path for the app directory


* config_path();
* database_path($path = '') :- Returns the path for database files in your app
* storage_path($path = ''):- Returns the path for the storage directory in your app
* lang_path($path = ''):- Returns the path for the lang directory in your app

* route($name, $parameters = [], $absolute = true)
If a route has a name, returns the URL for that route


* url()->current();

* url()->full();

* url()->previous();

* auth()
Returns an instance of the Laravel authenticator

```

if (auth()->check()) {
 // Do something
}

```

* back()Generates a “redirect back” response

* The dump() function is used to output the contents of a variable or expression to the browser's console or standard output 

* dd($variable...):- The dd() function stands for "Dump and Die." It does the same thing as dump()

* Both dump() and dd() are handy tools for debugging and understanding the flow of your application, especially during development. 

* old($key = null, $default = null) Returns the old value (from the last user form submission) for this form key

* redirect($path) Returns a redirect response to the given path

* fake():- Returns an instance of Faker

* chunk() makes it easy to split your collection into groups of a predefined size 

```
$users = collect([...]);
$rowsOfUsers = $users->chunk(3); // Separates into groups of 3

```

* take() pulls just the provided number of items
```
$topThree = $users->take(3); // Pulls the first 3
```


* skip() returns a new collection without the given number of
items


```
$numbers = collect([1, 2, 3, 4, 5]);
$numbers->skip(3)->values(); // [4, 5]
```























