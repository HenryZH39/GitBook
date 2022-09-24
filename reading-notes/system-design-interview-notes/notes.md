# Notes

### Traffic to web server
   1. _Web application: it uses a combination of server-side languages (Java, Python, etc.) to handle business logic, storage, etc., and client-side languages (HTML and JavaScript) for presentation._
   2. _Mobile application: HTTP protocol is the communication protocol between the mobile app and the web server. JavaScript Object Notation (JSON) is commonly used API response format to transfer data due to its simplicity._
----
### Relational database and Non - relational database
   -  _RDBMS : Relational database management system or SQL database._ Store data in table and rows.<br>Example : MySQL, Oracle database, PostgreSQL, etc.
   - _Non-Relational databases are also called NoSQL databases._
   <br>These databases are grouped into four categories: key-value stores, graph stores, column stores, and document stores.
   <br>Example : CouchDB, Neo4j, Cassandra, HBase, Amazon DynamoDB.
--- 
### Vertical vs horizontal scaling
   - _Vertical:_ adding more power (CPU, RAM, etc.) to your servers.
      - Good for low traffic service.
      - Has hard limitit. Impossible to add unlimited CPU and memory to a single server.
      - Does not have failover and redundancy. (No fault tolerate)
   - _Horizontal:_ scale by adding more servers into your pool of resources.
---
### Load balancer :
   - Deal with the problem if many users access the
   web server simultaneously and it reaches the web server’s load limit, users generally experience 
   - Client use public IP reach load balancer. Then load balancer will connet to different sever with pirvate IP.
   - Explanation:
     - If server 1 goes offline, all the traffic will be routed to server 2. This prevents the website from going offline. We will also add a new healthy web server to the server pool to balance the load.
     - If the website traffic grows rapidly, and two servers are not enough to handle the traffic, the load balancer can handle this problem gracefully. You only need to add more servers to the web server pool, and the load balancer automatically starts to send requests to them.
---
### Database replication
   - Master/slave relationship:
     - Master database: only supports write operations.
     - Slave database: gets copies of the data from the master database and only supports read operations.
   - Advantages:
     - Better performance : allows more queries to be processed in parallel.
     - Reliability : data is preserved multiple locations.
     - High availability : your website remains in
      operation even if a database is offline.
---
