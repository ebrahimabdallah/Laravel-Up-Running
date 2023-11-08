# Migrations
 single file that defibes teo things [up && Down ]
 
- migrations are always run in order by date

- up  :  to do 
- down : undo 

- create and run migration 
```
 php artisan make: migration 
```

- create table 
 ```
  
  --create=table_name

```
- modifiy table
```
  --table=table_name

```
To create new columns in a table 
- create table call or a modify table call,
- use Blueprint that’s passed into your closure

```
Schema::create('users',function(Blueprint $table){

$table->string('name');
});
```
# Column DataType
* integer          * tinyInteger
* smaillInteger    * mediumInteger
* bigInteger       * binary
* boolean          * datetime
* json(col)        * jsonb(col)
* text(colName)    * mediumText(col)
* longText(col)    * time(col)
* timestamp(col)   * uuid(col)
* increments(col)  * bigIncrements(col)
* timestamps()     * nullableTimestamps()
* rememberToken()  * softDeletes()
* morphs(col)

* take more one parameter
* string(col.len)                     * char(col,len)
* decimal(col,percision,scale)        * double(col,total digits,digits after decimal)
* enum (col,[choiceone,choiceTwo,.....])
* **Out book **
- in php 8.1+ you can create a file external enum and call when need it 
* float(colName,precision,scale)


* **Method Properties**

* nullable    * default('ex: false')
* unsigned()  * first()  
* after()     * unique()
* primary()   * index()

* **Modifying Columns**

* change()

```
Schema::create('users',function(Blueprint $table){

$table->string('name',1000)->change();

```

* **rename a column**
* renameColumn()

* **dropColumn**
* dropColumn()

* **Indexes and foreign key**

* $table->primary() //primary key &&  not primary() necessary if you’re using the increments() or bigIncrements() methods
* $table->primary(['',''])//Composite Key
* $table->unique()
* $table index() 

* adding and removing Foreign Key
```
$table->foreign('user_id')->references('id')->on('table_name')
```
* add constraints 
- onDelete('cascade')
```
$table->foreign('user_id')->refernces('id')->on(''table_name)->onDelete('cascade');
```

# Running Migrations

* migrate:install
Creates the database table

* migrate:refresh
Rolls back every database migration 

* migrate:reset
Rolls back every database migration

* migrate:fresh
Drops all of your tables and runs every migration again.

* migrate:rollback
Rolls back just the migrations that ran the last time you ran migrate

* migrate:status
Shows a table listing every migration

# Seeding 
 * tool for initializing your database with sample data, which is particularly useful during development, testing, or setting up default data in your application.


* Run 
```
php artisan migrate --seed
php artisan migrate:refresh --seed

```
*  run it independently
```
php artisan db:seed
php artisan db:seed --class=VotesTableSeeder

```

* create 
```
php artisan make:seeder TableNameSeeder
```
*  Calling a custom seeder from DatabaseSeeder.php

```
public function run ()
{
$this->call([TableName::class]); 
}

```
* ex

```

public function run ()
{
DB::table('name')->insert([
'name'=>'Ebrahim',
'email'=>'Ebrahim@gmail.com'
]);

}
```

# Factories

* patterns for creating fake entries for your data‐
base tables.

* create 
```
php artisan make:factory NameFactory
```
* to create one instance
```
$user=factory(User::class)->create
```
* to create many instance
```
factory(User::class,20)->create 
```
* function 
````
public function definition(): array
    {
        return [
            'name' => fake()->name(),
            'email' => fake()->unique()->safeEmail(),
            'email_verified_at' => now(),
            'password' => '$2y$10$92IXUNpkjO0', // password hash
            'remember_token' => Str::random(10),
        ];
    }
```

```
factory(User::class, 20)->create()->each(function ($u) use ($post) {
 $post->comments()->save(factory(Comment::class)->make([
 'user_id' => $u->id,
 ]));
});

```
