# [Scalability for Dummies] [Le Clound Blog]
url:http://www.lecloud.net/tagged/scalability

## Part 1: Clones/Instance
That leads to the first golden rule for scalability: **every server contains exactly the same codebase and does not store any user-related data, like sessions or profile picture, on local disc or memory.**
* "outsourcing" your session: an external database or an external presistent cache
* serving the same codebase: solved by the great tool Capistrano

## Part 2: Database
To fix the database preformance problems, you can choose from 2 paths:
* **Path #1** is to stick with MySQL and keep the "beast" running.
* **Path #2** means to denormalize right from the beginning and include no more Joins in any database query. 

## Part 3: Cache
"cache" mean in-memory caches like Memcached or Redis.
**Never do file-based caching**, it makes cloning and auto-scaling of your servers just a pain.
There are 2 patterns of caching your data. An old one and a new one:
* **Pattern #1** Cached Database Queries
* **Pattern #2** Cached Objects (That's  my strong recommendation and I always prefer this pattern.)

## Part 4: Asynchronism
To avoid such a "please wait a while" - situation, asynchronism needs to be done.
In general, there are two ways / paradigms asynchronism can be done.
* **Async #1** - "bake the breads at night and sell them in the morning" way, it means doing the time-consuming work in advance and serving the finished work with a low request time.
* **Async #2** - "start the task when the customer is in the bakery and tell him to come back at the next day", it means to handle task asynchronously.

**tutorials**
* [RabbitMQ](https://t.umblr.com/redirect?z=http%3A%2F%2Fwww.rabbitmq.com%2F&t=OTNhMmNkNTgwMjU3N2MwOTQyMzFiZDk1ZmI4OGMwZjE0MWZjMzdiYSxqbHhiaDBWZQ%3D%3D&b=t%3AeE4iDilbUfNhGIklAbjWYQ&p=http%3A%2F%2Fwww.lecloud.net%2Fpost%2F9699762917%2Fscalability-for-dummies-part-4-asynchronism&m=1) is one of many systems which help to implement async processing
* [ActiveMQ](https://t.umblr.com/redirect?z=http%3A%2F%2Factivemq.apache.org%2F&t=ZTFiYjYzYTFkZjQxODNiZTI1M2VkOGE0OWYyNTJiNTNlY2RjNDVhYSxqbHhiaDBWZQ%3D%3D&b=t%3AeE4iDilbUfNhGIklAbjWYQ&p=http%3A%2F%2Fwww.lecloud.net%2Fpost%2F9699762917%2Fscalability-for-dummies-part-4-asynchronism&m=1) and [Redis list](https://t.umblr.com/redirect?z=http%3A%2F%2Fredis.io%2Ftopics%2Fdata-types&t=Njg1MTAyMDc0MDdhNDdmMTA0ZTIxOGZkMmRkMmU3MDg4MjY3MjZmOSxqbHhiaDBWZQ%3D%3D&b=t%3AeE4iDilbUfNhGIklAbjWYQ&p=http%3A%2F%2Fwww.lecloud.net%2Fpost%2F9699762917%2Fscalability-for-dummies-part-4-asynchronism&m=1). The basic idea is to have a queue of tasks or jobs that a worker can process.
