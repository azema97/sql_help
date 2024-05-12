# ACID properties

ACID stands for Atomicity, Consistency, Isolation, and Durability. 
These are the four properties that ensure the reliability and consistency of transactions in a relational database system. 

- **Atomicity**: This property ensures that either all the operations within a transaction are completed successfully and the database is updated, or none of them are executed at all. In other words, a transaction is treated as a single unit of work that is either completed entirely or not at all.

- **Consistency**: This property ensures that the database remains in a consistent state before and after the execution of a transaction. This means that transactions must adhere to all defined rules and constraints, maintaining the integrity of the database.

- **Isolation**: This property ensures that the execution of multiple transactions concurrently does not interfere with each other. Each transaction should operate independently of and be unaware of the existence of other transactions executing concurrently.

- **Durability**: This property ensures that once a transaction is committed, the changes made by the transaction are permanently stored in the database and will survive any system failures, such as power outages or crashes. In essence, once a transaction is completed, its effects are permanent and cannot be undone.