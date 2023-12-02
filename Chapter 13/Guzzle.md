# Guzzle
* Guzzle is a widely used HTTP client library in PHP, and you can use it in Laravel for making HTTP requests to external APIs or services.
* enhances code readability, and provides a robust set of features for handling HTTP requests and responses
  # install
  ```
  composer require guzzlehttp/guzzle
  ```
  * Use Guzzle in a Controller
  ```
  public function makeRequest()
  {
   $response = Http::get('http://.................');
   if($response->successful())
  {
  $data=$response->json();
  }
  else
  {
  $statusCode =$response->status();
  $errorData=$response->json();
  }
   return view('my.view', compact('data'));

  }
  ```
  * Dumping
  ```
  return Http::dd()->get('http://...........');
  ```
  * Request Data
``` 
$response = Http::post('http://...............', [
    'name' => 'ebrahim',
    'role' => 'admin',
]);
```
* get Request
```
$response = Http::get('http://......', [
    'name' => 'Ebrahim',
    'page' => 1,
]);
```
