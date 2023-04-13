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
```
