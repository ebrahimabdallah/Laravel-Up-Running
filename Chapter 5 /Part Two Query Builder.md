
# Query Builder 

* tool for constructing SQL queries in a programmatic and fluent way. The Query Builder provides a simple, convenient way to interact with your database.

* Fluent Vs. Non Fluent 

* Fluent
```
$user=User::where('status','active')->orderBy('name','asc')->()get()
```
* Non-Fluent

```
$query=User::query()
$query->where('status','active');
$query->orderBy('name','asc');
$user=$query->()get()
```
______________________________________________________________
# Constraining method 

Ex:-

- Where ()
- Select()
- orWhere()
- whereIn()
- Limit()
- groupBy()
- whereExists()
- whereNull()
- whereRow()
- orderBy()
- havingRow() //filter result 
- skip() // typically used for pagination or limiting the number of results returned
- inRandomOrder() // sort result random 


______________________________________________________________
# Consitional Method

- when() //method adds a constraint to the query based on a condition 
- unless() //opposite When()

______________________________________________________________
# Endinf/Returning method

- first()
- get()
- finOrFail()
- value()
- count()
- min() && max()
- sum() && avg

______________________________________________________________
# join 

- inner join()
- Left join()

______________________________________________________________
* unions

* is used to combine the results of two or more queries into a single result set
* can use union or unionAll()
```
$firstQuery = DB::table('users')->where('name', 'John');
$secondQuery = DB::table('employees')->where('name', 'Jane');
$users = $firstQuery->union($secondQuery)->get();
```
- insert()
- update() 
- delete()


* construct database queries using a fluent and chainable syntax.
* particularly useful when you need to build complex or custom queries that might not fit neatly 
* used when you need to create dynamic queries, perform raw SQL operations, or work with tables that don't have corresponding Eloquent models
* Query Builder is used when you need to construct custom or complex SQL queries with greater control. 
___________________________________________________________________
