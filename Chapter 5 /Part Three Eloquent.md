
# Transaction
* context of databases is a sequence of one or more operations that are executed as a single indivisible unit of work.

______________________________

# Eloquent
* is more suitable for straightforward CRUD operations and complex relationships

* Eloquent impelemention of the Active Record Pattern and ORM  
* interact with your database tables using PHP objects
* provides an intuitive and expressive way to work with your database, where you can define relationships between models.
* useful when you need to handle complex relationships between tables.
* first() //get only first record
* find()
* findOrFail()
* firstOrFail()
* get() // method is more versatile and is used to retrieve records from a database table with optional conditions
* all() // method is used to retrieve all records from a database table. It doesn't take any conditions
* chunk() //  method will keep retrieving records in batches
* create()//create a new instance of an Eloquent model and save it to the database
* make() //method is used for creating instances of a class 
* aggregates are functions used to perform operations on a set of database records and return a single calculated value.
_____________________________________________

# Mass assignment
* a technique for quickly saving multiple attributes on a model at once. It allows you to assign an array of data to a model without the need to individually set each attribute.

* Fillable Attributes: In the model class, you can define a protected $fillable property, which is an array containing the names of attributes that can be mass-assigned

```
protected $fillable = ['name', 'email', 'password'];

```
* Guarded Attributes: Alternatively, you can use a protected $guarded property to specify attributes that should not be mass-assigned

* Soft delete 

* mark database rows as deleted wuthout acually deleting them from the database

* **Note**

* Soft deletes increases storage requirements, which might be a concern if you have large datasets.
* Not Suitable for All Scenarios:


# Scope 
* is a way to define query constraints that can be easily reused throughout your application.
* allowing you to make your code more readable, maintainable, and DRY
* Scopes are particularly useful for defining query filters and constraints that are frequently used in your application.

* There are two main types of scopes 
* **Local Scopes** defined as public methods within your Eloquent model

* **Global Scopes** used to automatically apply constraints to all queries performed on a particular Eloquent model.

* Scopes are a powerful feature in Laravel, enabling you to keep your code clean and your queries consistent.

* Removing Scope
* ways to remove a global scope
use the withoutGlobalScope() && withoutGlobalScopes()  
