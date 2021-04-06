Since my first day at the company I have asked myself: why does Vendasta use so many different “flavors of databases”? It took me a long time to fully understand, for example, why CS uses one storage flavor to store its data and Web-Crawler uses a totally different database approach to save basically the same data, and to be honest, it started to make much more sense a few months ago when I started to deepen my knowledge of GCP, i broke through the barrier of just being a user.

Being a user of any technology is part of our constant evolution as a developer. Usually it’s the first step we take when learning something new, but you have to recognize when the time to become more than a user has arrived. So if you feel like this is your next step, I strongly recommend you to take some formal GCP training courses, it will blow your mind and will make your life easier, for sure.

Today I’ll try to enumerate the main characteristics of some storage & database options available to developers on GCP, this way I believe I’ll help you to make the best decision when storing (And reading) your data on GCP.

# Cloud Storage: binary large-object storage
- Fully managed scalable service, in other words, you don't need to worry about capacity ahead of time.
- There you can store website static files, backups, or large data files.
- It’s not supposed to be used as a file system.
- It consists of globally unique names called buckets that are geographically located.
- Stored objects are encrypted and immutable that could be versioned if you want to.
- Cloud Storage also offers lifecycle management policies
- Multi-regional storage is a broad geographical location that stores your data in at least two geographic locations separated by at least 160 kilometers.

![](https://raw.githubusercontent.com/Ruscigno/personal-assets/master/gcp-storage-types/cloud-storage.png)

> Egress and data transfer charges may also apply
  
## Cloud storage works with other GCP services
- BigQuery & CloudSQL: import and export tables
- App Engine: object storages, logs, and datastore backups
- Compute Engine: startup scripts, docker images, and general objects storage

# Cloud BigTable: managed NoSQL database
- Fully managed, scalable, NoSQL, wide-column database service for petabytes applications.
- Composed of sparsely populated tables that can scale to billions of rows and thousands of columns.
- It's ideal for data that has a single lookup key, for storing large amounts of data with very low latency, and It supports high throughput, both read and write.
- Single-digit millisecond latency and over 2X the performance per dollar of unmanaged NoSQL alternatives.
- Encrypted both in-flight and at rest.

![](https://raw.githubusercontent.com/Ruscigno/personal-assets/master/gcp-storage-types/cloud-bigTable.png)

# Cloud SQL: fully-managed RDBMS
- Offers MySQL and PostgreSQL database as a service
- Uses database schema for consistency
- Atomic transactions: Database changes as all or nothing
- Provides several replica services like read, failover, and external replicas.
- Managed backups
- Vertical scaling (read and write)
- Horizontal scaling (read)

# Cloud Spanner: horizontally scalable RDBMS
- Strong global consistency and petabytes of capacity
- Auto-managed instances with high availability
- ANSI 2011 SQL queries
- Designed to handle outgrown relational databases and high
- Offers transactional consistency at a global scale, schemas, SQL, and automatic synchronous replication for high availability.
- Consider using Cloud Spanner if you have outgrown any relational database, or sharding your databases for throughput high performance, need transactional consistency, global data and strong consistency, or just want to consolidate your database.

# Cloud Datastore: horizontally auto-managed NoSQL database
- Designed for backend applications.
- Automatically handles sharding and replication, providing you with a highly available and auto-scalable.
- Atomic transactions: unlike Cloud Bigtable, it also offers transactions that affect multiple database rows.

# Firestore: scalable NoSQL database to store and sync data
- Designed for mobile, web, and server development
- It keeps your data in sync across client apps through realtime listeners
- Offline support, works regardless of network latency or Internet connectivity
- Allows you to run sophisticated ACID transactions against your document data
![](https://raw.githubusercontent.com/Ruscigno/personal-assets/master/gcp-storage-types/firestore.png)

# Comparing storage options
![](https://raw.githubusercontent.com/Ruscigno/personal-assets/master/gcp-storage-types/storage-options-1.png)
![](https://raw.githubusercontent.com/Ruscigno/personal-assets/master/gcp-storage-types/storage-options-2.png)

## Conclusion
Finally, I tried to compile a table to compare costs of usage of all listed options, however, there are a lot of variables in the cost calculation and it’s very hard to run the same test on each of them. Also, I couldn’t find any comparison between all options I listed here, so I gave up. In the end, the most important thing is to choose the most suitable option for your solution, by doing that I believe you are going to extract the best of your solution for the budget you have, in the end, the storage cost isn’t the only thing you have to consider.

> Special thanks to Dale Birtch for his help.

### Source of inspiration and Image sources:
[https://cloudplatform.googleblog.com/2015/05/introducing-Google-Cloud-Bigtable.html](https://cloudplatform.googleblog.com/2015/05/introducing-Google-Cloud-Bigtable.html)
Cloud Architecture with Google Cloud Professional Certificate Course