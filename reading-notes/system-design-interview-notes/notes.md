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
   - File system / Blob storage
   <br> Save media file : image , audio, video
   <br> Example: Amazon S3
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
### Cache 
   - Temporary storage area that stores the result of expensive responses or frequently accessed data in memory.
   - Cache tier: temporary data store layer
   - Cache only store data temporarily
   - Need to implement an expiration policy
   - SPOF (single point of failure). Need to avoid SPOF, multiple cache servers across different data centers will be helpful.
   - LRU cache[leetcode No.146](https://leetcode.com/problems/lru-cache/)
---
### CDN (Content delivery network)
   - CDN servers cache static content like images, videos, CSS, JavaScript files, etc.
   - Low latency : cache server close to user geographically.
   - Autoscaling : adding or removing web servers automatically based on the traffic load.
---
### Multi-data Center
   - Coult help with with technial challenges:  
     - Traffic redirection
     - Data synchronization
     - Test and deployment.
--- 
### Message queue
   - Durable component, stored in memory, that supports asynchronous communication
   - When the size of the queue becomes large, more workers are added to reduce the processing time. However, if the queue is empty most of the time, the number of workers can be reduced.
---
### Logging, metrics, automation
   - Logging: Monitoring error logs is important because it helps to identify errors and problems in the system.
   - Metrics: Collecting different types of metrics help us to gain business insights and understand the health status of the system . 
     - Host level matricss: CPU, memory, disk I/O, etc.
     - Aggregated level metrics: performance of the entire database tier, cache tier, etc.
     - Key business metrics: daily active users, retention, revenue, etc.
   - Automation: build or leverage automation tools to improve productivity
---
### Database Scaling
   - Sharding is a great technique to scale the database but it is far from a perfect solution.
     - Resharding data
     - Celebrity problem
     - Join and de-normalization
    - Shard databases to support rapidly increasing data traffic
---
### How we scale system to support millions of users
   - Keep web tier stateless
   - Build redundancy at every tier
   - Cache data as much as you can
   - Support multiple data centers
   - Host static assets in CDN
   - Scale your data tier by sharding
   - Split tiers into individual services
   - Monitor your system and use automation tools
---
### Calculate data volume
- Data volume unit:
  - 2 ^ 10, 1 Thounsand, 1 Kilobyte, 1 KB
  - 2 ^ 20, 1 Million, 1 Megabyte, 1 MB
  - 2 ^ 30, 1 Billion, 1 Gigabyte, 1 GB
  - 2 ^ 40, 1 Trillion, 1 Terabyte, 1 TB
  - 2 ^ 50, 1 Quadrillion, 1 Petabyte, 1 PB
---
## 4-step process for effective system design interview
- Step1 - Understand the problem and establish design scope
  - Ask questions to clarify requirement:
    - What specific features are we going to build?
    - How fast does the company anticipate to scale up? What are the anticipated scales in 3 months, 6 months, and a year? 
- Step2 - Propose high-level design and get buy-in
  - Initial blueprint for the designraw
- Step3 - Desgin deep dive
  - Identify and prioritize components in the architecture.
- Step4 - Wrap up
  - follow-up questions or give you the freedom to discuss other additional points
---
## Rate Limiter
- Used to control the rate of traffic sent by a client or a service
- Benefits :
  - Prevent resource starvation caused by Denial of Service (DoS) attack
  - Reduce cost : fewer server
  - Prevent servers from being overloaded
- In Microservices: API gateway
- Algorithm : 
  - Token bucket
  - Leaking bucket
  - Fixed window counter (based on timestamp)
  - Sliding window log
  - Sliding window counter
- Redis is a popular option to implement rate limiting. It is an inmemory store that offers two commands: INCR and EXPIRE.
  - INCR: It increases the stored counter by 1.
  - EXPIRE: It sets a timeout for the counter. If the timeout expires, the counter is automatically deleted.
- Example:
```
domain: auth
descriptors:
   - key: auth_type
   Value: login
   rate_limit:
   unit: minute
   requests_per_unit: 5
```
---
## Design Consistent Hashing
- Common way to balance the load is to use the following hash method:   
  - serverIndex = hash(key) % N, where N is the size of the server pool.
- Consistent hashing : when a hash table is re-sized and consistent hashing is used, only k/n keys need to be remapped on average, where k is the number of keys, and n is the number of slots.
   - Use Hash ring : if add or remove server, will update client key and re-distribute
---
## Desgin A Key-Value Store
- Distributed key-value store
  - Also called a distributed hash table, which distributes keyvalue pairs across many servers
  - Important to understand CAP (Consistency, Availability, Partition Tolerance) theorem.
  - Real-world distributed systems In a distributed system, partitions cannot be avoided, and when a partition occurs, we must choose between consistency and availability.
- Data partition
  - Infeasible to fit the complete data set in a single server.
  - Split the data into smaller partitions and store them in multiple servers
- Consistency models
  - Strong consistency: any read operation returns a value corresponding to the result of the most updated write data item. A client never sees out-of-date data.
  - Weak consistency: subsequent read operations may not see the most updated value. 
  - Eventual consistency: this is a specific form of weak consistency. Given enough time, all updates are propagated, and all replicas are consistent.
- Inconsistency resolution: versioning
  - Versioning system can detect conflicts and reconcile conflicts
  - Vector clock：
    - [server, version] pair associated with a data item
- Handling failures
  - Failure detection
  - Handling temporary failures
    - Sloppy quorum ：used to improve availability. Instead of enforcing the quorum requirement, the system chooses the first W healthy servers for writes and first R healthy servers for reads on the hash ring. Offline servers are ignored.
  - Handling permanent failures
    - Anti-entropy protocol：comparing each piece of data on replicas and updating each replica to the newest version. A Merkle tree is used for inconsistency detection and minimizing the amount of data transferred.
  - Handling data center outage
    - Important to replicate data across multiple data centers
- Summary: 
  1. Ability to store data: Use consistent hasing to spread the load across servers
  2. High availability read: Data replication multi-data center setup
  3. Highly available writes: Versioning and conflict resolution with vertor clocks
  4. Dataset partition: Consistent Hashing
  5. Incremental scalability: Consistent Hashing
  6. Heterogeneity: Consistent Hashing
  7. Tunable consistency: Quorum consensus
  8. Handling temporary failures: Sloppy quorum and hinted handoff
  9. Handling permanent failures: Merkle tree
  10. Handling data center outage: Cross-data center replication
---
## Design A Unique ID Generator in Distributed Systems
- Step 1 Understand the problem and establish design scope
  - Feature for IDs 
  - The create rules : increase by 1 ? number or characters ? length ?
  - Scale of the using system
- Step 2 Propose high-level design and get buy-in
  - Multi-master replication
    - Use MySQL 'auto_increment' feature, increase by k(number of database in use)
    - Drwabacks :
       1. Hard to scale with multiple data centers
       2. IDs do not go up with time across multiple servers.
       3. It does not scale well when a server is added or removed.
  - Universally unique identifier (UUID) 128bits
    - can be generated independently without coordination between servers.
  - Ticket server
    - Use a centralized auto_increment feature in a single database server
    - single database server means not stable and could not tolerate failure
  - Twitter snowflake approach
    - Divide an ID into different sections
    - Each section is explained below:
       1. Sign bit: 1 bit. It will always be 0. This is reserved for future uses. It can potentially be used to distinguish between signed and unsigned numbers.
       2. Timestamp: 41 bits. Milliseconds since the epoch or custom epoch. We use Twitter snowflake default epoch 1288834974657, equivalent to Nov 04, 2010, 01:42:54 UTC.
       3. Datacenter ID: 5 bits, which gives us 2 ^ 5 = 32 datacenters.
       4. Machine ID: 5 bits, which gives us 2 ^ 5 = 32 machines per datacenter.
       5. Sequence number: 12 bits. For every ID generated on that machine/process, the sequence number is incremented by 1. The number is reset to 0 every millisecond.
- Step 3 Design deep dive
   - As timestamps grow with time, IDs are sortable by time.
   - After 69 years, we will need a new epoch time or adopt other techniques to migrate IDs.
- Step 4 Wrap up
  - Clock synchronization
  - Section length tuning
  - High availability
---
## Design A Notification System
- IOS push notification:
 - Provider -> APNs -> IOS Device
 - Provide: builds and send notification
 - APNs: Apple Push Notification Service, remote service provided by Apple
- Android push notification:
  - Provider -> FCM -> Android Device
  - FCM: Firebase Cloud Messaging
- SMS message:
  - Provider -> SMS service -> SMS
- Email:
  - Provider -> Email servers/ service -> Email
- Services -> Notification System -> APNs/ FCM etc. -> clients
- For scalebility:
  - add cache and db for noification service 
  - add message queue and service before sent to third party service
  - add database to save the fail operation 
- Rate limiting 
- Retry mechanism
- Horizental scaling: automatic add or remove service if there is too many queries 
- Analytics service: need to have events tracking. like open ? click ? unsubscribe?
---
## Design A Chat System
- Time-tested HTTP protocol
- Polling: technique that the client periodically asks the server if there are messages available
- Long polling: a client holds the connection open until there are actually new messages available or a timeout threshold has been reached
- WebSocket connection: solution for sending asynchronous updates from server to client. Once connection estimated. Could still work using port 80 and 443 for both sender and receiver
- Storge: Two types of data exist in a typical chat system
  - Generic data: User profile, setting, friends list. Data replication and sharding satisfy availability and scalability
  - Chat history data: key-value stores. 
    - allow easy horizontal scaling
    - provide low latency 
    - Relational databases do not handle long tail of data well. When the indexes grow large, random access is expensive.
    - Adopted by other proven reliable chat applications.
- Service discovery
  - Apache Zookeeper: open-source solution for service discovery
- Message flows
  - when A send message to chat server . server will get an ID for the message and save the value<ID, message> in KV store.
  Then put id in message queue. Then presen sever will check user B is online / offline. online : send ID to server 2 and user B could get message. offline : send notification to user B .
- Message synchronization across multiple devices
  - The recipient ID is equal to the currently logged-in user ID.
  - Message ID in the key-value store is larger than cur_max_message_id .
- Heartbeat mechanism
  - an online client sends a heartbeat event to presence servers. If presence servers receive a heartbeat event within a certain time, say x seconds from the client, a user is considered as online. Otherwise, it is offline.