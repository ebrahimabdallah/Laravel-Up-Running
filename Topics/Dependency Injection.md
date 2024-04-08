# Dependency Injection
* a programming technique that allows you to decouple your software components from each other.

# Four Major Roles in DI
* **service** you want to use, such as a payment service or an email service.
* **client** that uses the service. This is the class that you'll inject the service into
* **interface** that's used by the client and implemented by the service "optional".
* **injector** creates a service instance and injects it into the client. This is usually known as a dependent injection container.

* **Inversion of Control (IoC)** is a design principle in which a software component is designed to receive its dependencies from an external source, rather than creating them itself.
* helps in designing loosely coupled classes which make them testable, maintainable and extensible.

* **Steps**
* Define the UserService interface
```
interface UserServiceInterface{
public function createUser(array $data);
}

```
* implement the UserService
```
class UserService implements UserServiceInterface{
public function createUser(array $data)
{
return User::create($data);
}
}
```
* Inject the UserService into the UserController

```
class UserController extends Controller {
    protected $userService;

    public function __construct(UserServiceInterface $userService) {
        $this->userService = $userService;
    }

    public function createUser(Request $request) {
        $data = $request->validate([
            'name' => 'required|string|max:255',
            'email' => 'required|string|email|max:255|unique:users',
            'password' => 'required|string|min:8',
        ]);

        $user = $this->userService->createUser($data);

        return response()->json(['user' => $user], 201);
    }
}
```
* Bind the UserService implementation to its interface in the service container 
```
class AppServiceProvider extends ServiceProvider {
    public function register() {
        $this->app->bind(UserServiceInterface::class, UserService::class);
    }
}
```

* **anthor example**
```
class UserService {
    private $userRepository;

    public function __construct(UserRepository $userRepository) {
        $this->userRepository = $userRepository;
    }

    public function getUsers() {
        return $this->userRepository->findAll();
    }
}

class UserRepository {
    public function findAll() {
        // fetch users from the database
    }
}
```






* Video 
* https://www.youtube.com/watch?v=BfAv2oAXHdA&list=PLdYYj2XLw5BnpInmR103TyVwFd_CLI6IS&index=18


