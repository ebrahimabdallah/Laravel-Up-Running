
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
