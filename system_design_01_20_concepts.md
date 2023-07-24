# System design concepts

### Vertical scaling

- Single server serving all users
- Increase resources on the single server

### Horizontal Scaling

- Add server replicas to serve multiple users
- Adds redundancy and fault tolerance
  
### Load Balancers

- A reverse-proxy server that direct incoming requests to the appropriate (load) server
- Routes requests to nearest locations

### Content Delivery Networks

- A CDN allows to serve static files (copy files across the world and serve by proximity)
- A technique for caching

### Caching

- Saves data for faster retrieval

### IP Address / TCPIP

- TCP/IP/UDP -> protocols that decide how we send data over the internet
  - TCP is reliable, resends ordered packages that are missing
    
### Domain Name System

- A record that translates a server's name to its IP address (A-record mapping)

### HTTP

- HTTP is higher-level than TCP (Application-Layer Protocol)
- Follows Client-Server model

### REST

- Most popular API paradigm
- Makes HTTP stateless
- Defined status codes and response data

### GraphQL

- API pattern intro'd by Facebook in 2015
- Single request (query) and chose which resources you want to fetch
  - limits overfetching 

### gRPC

- Framework by Google 2016
- Improvement over REST. Used for server-to-server communication
- Performance boost from Protocol Buffers
  - data is serialized in binary format (size efficient)
  - less readable than JSON 

### WebSockets

- Solves the POLLING issue of realtime apps
- Supports bidirectional communication
  
### SQL

- Used for storing data
- Efficient storage and fast retrieval of data

### ACID

- Atomicity (transactions are all or nothing)
- Consistency (foreign keys/constraints)
- Isolation (transactions)
- Durability

### NoSQL

- Consistency makes DBs hard to scale -> NOSQL drops this
- Allows for sharding (horizontal scaling of data)

### Sharding / Replication

- Uses shard key to partition the data
- Leader/Follower replica: read-only copies (followers only for reads)
- Leader/Leader replica: every replica can be used for write, but causes inconsistencies

### CAP Theorem

- Consistency, Availability, Partition
- "Pick two of three"
- Consistency is not the C in ACID
  
### Message Queues

- Durable storage, replicated for redundancies / shareded for scalability
- Data persisted before processing thanks to message queue
- Allows for decoupling of apps
