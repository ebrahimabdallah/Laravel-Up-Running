# User Authentication and Authorization
* **Authentication** means verifying who someone is and allowing them to act as that person in your system.
* **Authorization** means determining whether the authenticated user is allowed (authorized) to perform a specific behavior. 
* **Authorizable** contract requires a method ( can() ) that allows the
framework to authorize instances of this model for their access permissions in different contexts

* **The auth()** global helper is the easiest way to interact with the status of the authenticated user throughout your app
* auth()->check()
* auth()->guest():returns to suitable for non-authenticated users && opposite
* Attempting a user authentication with the user-provided information **such** :-
* provides you with a user login that lasts as long as the user’s session.
```
if (auth()->attempt([
 'email' => request()->input('email'),
 'password' => request()->input('password'),
])) {
   return view('');
}
```
* **: auth()->viaRemember()** returns a Boolean, indicating whether or not the current user authenticated via a remember token. This allows you to prevent certain higher-sensitivity features from being accessible by remember token

* **auth.password_timeout** configuration setting is used to define the number of minutes before the password reset
* four methods that make Auth
```
auth()->loginUsingId(4) // passing id
auth()->login($user); // user
auth()->once(['username'=>'role']); //choose to auth given user 
Or
auth()->onceUsingId(4);
auth()->once([
'last_name'=>'name',
'code'=>number, 
]); //pass multiple keys and values
```
* If you’d like to log out a user’s current session on any other devices **logoutOtherDevices()**
```
public function logout(Request $request)
{
$request->user()->logoutOtherDevices($request->password);
return redirect()->route('');
}

```
* have to apply the **auth.session** middleware to any routes you want them logged out of
```
auth()->logoutOtherDevices($password);
```
* Auth : Restricts route access to authenticated users
* Auth.basic : Restricts access to authenticated users using HTTP Basic Authenticatio
* Auth.session : Makes routes viable to be disabled using **Auth::logoutOtherDevices()**
* can : Used for authorizing user access to given routes
* guest : Rstricts access to unauthenticated users
* password.confirm : Requires users to have recently reconfirmed their password

# Email Verification
* Auth::routes() in your routes file with the verify parameter set to true
```
Auth::routes(['verify' => true]);
```
# Guards
* defines how users are authenticated for each request
* two pieces : a driver that defines how it persists and retrieves the authentication state (session)
* provider : that allows you to get a user by certain criteria (users)
* you’d change providers if you wanted to change the storage type or retrieval methods for your users
* most laravel apps just use one guard
* 
