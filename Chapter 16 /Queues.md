# Queues 
* queue is a mechanism for deferring time-consuming and resource-intensive tasks, allowing them to be executed in the background. Using a queue system
* Queue workers in Laravel are designed to handle tasks asynchronously
# Why Queues?
1)  make it easy to remove a costly or slow process from any synchronous call(Improved Performance)
2)  don’t want your users to have to wait for mail to send in response to their actions.
3)  sometimes you may not be worried about saving your users time (Fault Tolerance)
4)  Decoupling Components\


# Steps 
* Step 1.
1) Creating Job
```
php artisan make:job NameJob
```
* Componenet template for jobs in Laravel
* Dispatchable gives it methods to dispatch
* InteractsWithQueue allows each job, while being handled, to control its relationship with the queue
* Queueable allows you to specify how Laravel should push this job to the queue
* SerializesModels gives the job the ability to serialize and deserialize Eloquent model
