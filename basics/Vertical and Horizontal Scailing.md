# 🏢 Vertical and Horizontal Scailing

Vertical scaling and horizontal scaling are two approaches used to increase the capacity and performance of relational databases:

1. **Vertical Scaling (Scaling Up)**:
   - Vertical scaling involves increasing the capacity of a single server by adding more CPU, memory, or storage resources to it.
   - In the context of relational databases, vertical scaling typically involves upgrading the hardware of the server hosting the database, such as adding more powerful processors, increasing RAM, or using faster storage devices.
   - Vertical scaling is often easier to implement initially because it doesn't require significant changes to the database architecture or application code.
   - However, there is a limit to how much a single server can be scaled vertically, and it can become expensive as the hardware upgrades become more substantial.

2. **Horizontal Scaling (Scaling Out)**:
   - Horizontal scaling involves distributing the workload across multiple servers or nodes.
   - In the context of relational databases, horizontal scaling typically involves sharding or partitioning the data across multiple servers or replicating the database across multiple nodes.
   - Horizontal scaling allows for better scalability and fault tolerance because the workload is distributed across multiple servers, reducing the risk of a single point of failure.
   - However, horizontal scaling can be more complex to implement initially because it often requires changes to the database schema, application code, and infrastructure to support data distribution and synchronization.
   - Horizontal scaling can also introduce additional complexities related to data consistency and synchronization, especially in distributed systems.

In summary, vertical scaling involves adding more resources to a single server, while horizontal scaling involves distributing the workload across multiple servers or nodes. Both approaches have their advantages and limitations, and the choice between them depends on factors such as the specific requirements of the application, the budget, and the scalability goals.