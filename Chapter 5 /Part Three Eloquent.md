
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

____________________________________
# Accessors , Mutators and Atrribute Casting 

* **Accessors** :  allow you to define custom attributes change how a particular column is output,  you want to create a custom
attribute that doesn’t exist in the database table at all , how data output reading 


in Model create a function as accessors 

```
public function getNameAttribute($name)
{
 return strtoupper($name)
}

```
* method is automatically called when you access the name attribute, and it modifies the value before returning it
```
$user =User::find(1);
return $user->name;
```

* **Mutators** : same accessors but except they’are for determining how to process setting the data instead of getting it.

```
public function setAmountAttribute($value)
{
 $this->attributes['amount']=$value > 0 ? $value : 0 ; 
}
```

* it's powerful tools for keeping your data consistent and ensuring that certain actions are taken before data is persisted. They provide a way to encapsulate logic related to attribute manipulation within your model.

* **Casting**
Using casts can help ensure that your data is always in the expected format, and it can simplify your code by eliminating the need for manual type-checking and conversion in various parts of your application.
```
  protected $casts = [
        'is_admin' => 'boolean',
        'age' => 'integer',
        'data' => 'array',
    ];

```

* casting, mutators, and accessors are features specific to Eloquent, Laravel's ORM (Object-Relational Mapping) system. 
* These features are not directly applicable to the Laravel Query Builder.

# Eloquent Serialization
*  process of converting Eloquent model instances or collections of instances into a format that can be easily converted to JSON or other response formats

```
$user = User::find(1);
$json = $user->toJson();
```


# Relationships

* ont-to-one
```
public function User()
{
return $this->hasOne(User::class,'user_id');
}
```
* to access it 
```
$user=User::first();
$userPhone=$user->User;
```

* one-to-many

```
public function User()
{
return $this->hasMany(User::class)
}
//belongsTo can use it 


public function User()
{
return $this->belongsto(User::class)
}
```
* access same as one-to-one


* **attaching** and **detaching** refer to the actions of associating and dissociating related models in a many-to-many relationship

* **Many-to-Many**
```
public function User()
{
return $this->belongsToMany(User::class);
}
```

* **Pivot Table** is an intermediate table that connects the related models. This table is used to store the relationships between the models involved in the many-to-many relationship
* name it take both table name such : table user && table role  Pivot Table [user_role]

```
 public function roles()
    {
        return $this->belongsToMany(Role::class, 'user_role', 'user_id', 'role_id');
    }


     public function users()
    {
        return $this->belongsToMany(User::class, 'user_role', 'role_id', 'user_id');
    }


public function up()
{
    Schema::create('user_role', function (Blueprint $table) {
        $table->unsignedBigInteger('user_id');
        $table->unsignedBigInteger('role_id');
        $table->timestamps();

        $table->primary(['user_id', 'role_id']);
    });
}
```

* **Polymorphic relationships** in Laravel allow a model to belong to more than one other type of model on a single association.
* single database table is used to store the relationships between the models, along with additional columns to identify the type of the related model.
 
