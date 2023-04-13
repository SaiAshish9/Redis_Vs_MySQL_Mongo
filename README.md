```
Let's say we've a web application running inside the server or a docker 
container, and a mysql or microsoft sql server.

Waiting 30s or 60s for reading data from the db is not a great user experience 
using a query. 

Lets say user wants to retrieve report from the db in about 30s or 60s with the
help of a query. It could be possible to return the same data in about 5s.

Instead of querying directly we can store data inside a redis cache instance and
retrieval of that data occured directly from memory or RAM from a server that is running
the redis service.

Web Server can check from the redis if it has data or else redis cache can be populated 
from the database

Everytime a user performs a query, web service need not to got at db, it can make use of
redis instead.

When we deploy a redis server for the first time, redis instance itself doesn't have any data
except the default configuration set for the redis engine.

One of the ways to populate redis cache is to populate upon first instance at the redis data.

Redis can throw cache miss if required data is present, it can go to the database server and retrieve
the data it needs and put that back into the cache so that with next time with that same server, db query
can be avoided.

Instead for web server going to the db for the data via redis we can plugin a cache worked in between a redis and database

Cache worker has only one job it will monitor the changes at the db and if there's any if will update the redis cache.
So the next time webserver requests the data it's ready.

One of the easiest way of deploying redis is to make use of docker container. Redis can be easily deployed as a standalone
docker container.

Another way is to deploy inside a managed service. There are many diff. cloud vendors for this such as AWS, Azure and GCP. They 
will provide redis managed services that will automatically maintains , upgrades and monitors redis cache instance. So if they don't
need to worry about monitoring and high availability.

We can deploy in a highly available fashion. First of all we deploy a master node and we can replicate data with one or more
slave nodes or read replicas.

Data structured supported by redis instance: 
```

<img width="1772" alt="Screenshot 2023-04-13 at 10 41 27 AM" src="https://user-images.githubusercontent.com/43849911/231659681-28273ccf-fdea-4256-9c8d-96b5ac063801.png">

<img width="1784" alt="Screenshot 2023-04-13 at 10 43 26 AM" src="https://user-images.githubusercontent.com/43849911/231659965-5b3ca941-fd85-4a2b-abc8-d5444182fec9.png">

<img width="1782" alt="Screenshot 2023-04-13 at 10 48 19 AM" src="https://user-images.githubusercontent.com/43849911/231660632-c317018c-d4f3-48f8-86f3-224603e2c23b.png">

<img width="1789" alt="Screenshot 2023-04-13 at 10 54 46 AM" src="https://user-images.githubusercontent.com/43849911/231661528-f414856a-d944-4612-8d95-16eacbadf86b.png">

<img width="1790" alt="Screenshot 2023-04-13 at 10 59 32 AM" src="https://user-images.githubusercontent.com/43849911/231662211-dafa1565-7aea-4595-96c1-3609e0419363.png">
