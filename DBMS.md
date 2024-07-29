# Database Management Systems and Schema Design

## Table of Contents

* [What is DBMS?](#what-is-dbms)
* [Classification of Database Management Systems](#classification-of-database-management-systems)
* [Schema Design](#schema-design)
* [Best practices for data storage and retrieval](#best-practices-for-data-storage-and-retrieval)


<!-- ---------------------------------------------------------------------- -->

## What is DBMS?

Database Management Systems is an interface between end-user and database which allows users to create and maintain database. It is a computerized system that allows editing, updating, or deleting data from the database.

It is a software system that facilitates defining, constructing, manipulating, and sharing database among various users.

➢Defining a database: it is determining the data types, structures, and constraints of the data that will be stored in the database, It  helps provide data security, data integrity, concurrency, and uniform data administration procedures

➢Constructing the database: it is the process of storing the data on some storage medium.

➢Manipulating a database: it is retrieving, and modifying the data to reflect changes in the miniworld, and generating reports from the data.

➢Sharing a database: accessing the database across multiple users simultaneously.

**Example:** An application program sends queries or requests to the DBMS to access the database, this allows reading or writing data to the database. It also offers a protection system for the data against software or hardware crashes and security protection against unauthorized access.

<img src="https://www.researchgate.net/publication/326006960/figure/fig1/AS:641949367279620@1530064064883/Simplified-database-system-Risunok-1-Uprosennaa-sistema-baz-dannyh-Slika.png" width="400" height="400">

DBMS offers flexibility and a complex backup system which traditional filesystems can not offer especially for large projects that may have large quantities of data.

### When Not to Use a DBMS

It may be more desirable not to use a DBMS under the following circumstances:
• Simple, unchanging applications.
• Embedded systems with limited storage capacity, where a general-purpose DBMS would not fit.
• No multiple-user access to the data.

<!-- ---------------------------------------------------------------------- -->

## Classification of Database Management Systems

DBMS can be classified based on multiple criteria such as data model, user numbers, or data distribution.

### Classification Based on Data Model 

#### Relational data model (RDBMS)

The most widely used data model today is the relational data model (RDBMS) because of its user-friendly interface. It is based on normalizing data in the rows and columns of the tables. This is a viable option when you need a data storage system that is scalable, flexible, and able to manage lots of information. Oracle, MS SQL Server, DB2, and MySQL support this model.

<img src="https://www.boardinfinity.com/blog/content/images/2022/12/Your-paragraph-text--90-.jpg" width="500" height="300">

#### Hierarchical data models

There are other traditional models "they are called traditional as they preceded the relational" such as hierarchical data models and Network data models.

Hierarchical data models organize data in a tree-like structure. Data storage is either a top-down or bottom-up format and is represented using a parent-child relationship.

The data record here is represented by the node. The superior node that is common for all other nodes is the root. This data model is known for its simplicity and presents a logical method for data organization.

Although this approach ensures direct data retrieval, it consumes time while starting from the node and crossing many branches till reaching the layer of data we want.

<img src="https://files.prepinsta.com/2023/01/Hierarchical-Model-in-DBMS-img.webp" width="300" height="300">

**Features of the hierarchical model**

It is implemented based on one-to-many relationship. Any parent node should have more than one child node and the child node will have only one parent. Here the hierarchical data can be represented as relation tables and the link between these tables is maintained using a foreign key.

**Drawbacks of the hierarchical model** 

1. Limited flexibility: Not all real-life applications adhere to the linear configuration represented by this approach.

2. Complexity with some relationships: applications that require many to many relationaship when following this approach will struggle and many records will be replicated. So this redundancy can lead to potential inefficiencies.

3. Rigid structures: It is very challenging to modify this structure. 

4. Limited query capabilities: the constraints of this approach on query capabilities can make data retrieval slower and more complicated, especially for applications that require rapid data retrieval and analysis.

**When To Use Hierarchical Data Models**

1. Simple hierarchies:  Whether it’s the filing system on a computer, it starts with a root which is the highest level directory, where sub-directories emerge as you delve deeper.

<img src="https://assets.datamation.com/uploads/2023/10/dm_20231011-hierarchical-vs-relational-data-models-figure_d.jpg" width="500" height="500">

Also, organizational charts with the CEO on top then managerial departments, Such charts let companies effectively communicate the chain of command.

<img src="https://assets.datamation.com/uploads/2023/10/dm_20231011-hierarchical-vs-relational-data-models-figure_c.jpg" width="500" height="500">

2. Systems prioritizing data integrity: due to its strict one-parent rule, it ensures data consistency and to remain unambiguous, making it a prime choice for systems where the sanctity and authenticity of data relationships are paramount.

3. Applications needing defined access paths.

**When Other Models Might Be Better**

1. Complex data relationships: when there are  many-to-many relationships.

2. Flexible database structures: when data is modified and updated frequently. so (RDBMS) will be suitable here.

3. Advanced query requirements: when there’s a need for diverse querying capabilities, especially across non-hierarchical data points, relational or network databases often offer more efficient solutions.

#### Network data models

Network data models address the need for more complex relationships by allowing each child to have multiple parents. Entities are organized in a graph that can be accessed through several paths. This was the most widely used model before the relational database model was introduced. It is like a graph that reflects the inherent relationships between entities. Graph theory principles form the basis of the network data model, focusing on nodes, edges, vertices, and connectivity for constructing and querying data.

Specialized query languages like Cypher, Gremlin, and SPARQL are crucial for interacting with databases using network data modeling. They enable users to navigate graphs, retrieve specific data, and execute complex queries capturing entity relationships.

Nodes represent entities and branches represent the relations between nodes. Nodes can have attributes, edges can describe relationship nature in a graph structure.


<img src="https://assets.datamation.com/uploads/2023/12/dm_20231214-network-data-model-figure_a.jpg" width="400" height="300">


**Drawbacks of the Network Data Model**

1. Complexity In Modeling: Creating this model is challenging due to the complexity of managing numerous entities and relationships. Designing an effective model necessitates thoughtful consideration of relationships, redundancy, and overall structure.

2. Performance Scaling: Network data models are strong in relationships but can struggle with big data or complex graphs, So it requires careful database design.

3. Lack Of Standardization: Network databases, unlike relational databases, do not have a standardized query language like SQL. This lack of standardization can be a challenge when using different graph database systems.

**Benefits Of A Network Data Model**

1. Flexibility In Data Relationships: it offers flexibility in representing complex relationships, excelling at capturing intricate connections between entities that evolve over time, especially in dynamic scenarios.

2. Efficient Query Performance: Visualizing network data models with nodes and edges helps users grasp data structure easily. It represents entities and relationships clearly, aiding stakeholders such as analysts and developers in understanding data connections in a real-world context.

3. Better Support For Evolving Data Structures: The network data model adapts easily to changing structures, simplifying relationship modifications and supporting evolving data requirements for organizations.

<img src="https://files.prepinsta.com/2023/01/Network-Model-in-DBMS-img.webp" width="300" height="300">

**Example:**

**IT Infrastructure:** it represents devices as nodes and connections as edges. Device nodes have attributes like IP Address, Manufacturer, and Operating System, while edges represent connections like Connected to or Communicate with.

Hierarchical data models and Network data models are still used in the industry on mainframe platforms, but they are not common due to their complexity.

#### Object-oriented data model (OODBMS)

A few years ago, the object-oriented data model was represented. Object-oriented database management systems (OODBMS) combine database capabilities with object-oriented programming language capabilities so they store data in objects instead of rows and columns. It is based on object-oriented programming (OOP) that allows objects to have members such as properties, and methods. That model is not widely used as expected. Some examples of object-oriented DBMSs are O2, ObjectStore, and Jasmine.

<img src="https://files.prepinsta.com/2023/01/Object-Oriented-Database-Model-in-DBMS.webp" width="300" height="300">

During program execution, an object such as a task instance with properties like name and status exists. Methods like update task() and get task history() can be utilized. The initialized task object is accessible throughout the program.

When your program ends, your object is deleted. It's transient, not stored permanently. You'll have to fetch data like name and status from the database again to create a new task object.

When your program ends, your object is deleted. It's transient, not stored permanently. You'll have to fetch data like name and status from the database again to create a new task object.

Different from relational databases, document databases like MongoDB require less manual object composition from query results as document field mapping to class properties is similar in both types.

OODs have been around for decades. MongoDB Realm is one of the new and promising pieces of software in that field.

```
const myTask = realm.objectForPrimaryKey("Task", 12345);
```

**When To Use object-oriented databases**

OODs are commonly used in object-oriented programming languages such as Java, Kotlin, C#, Node JS (React), and Swift. Industries utilizing OODs are typically those based on an object-oriented language to enhance productivity when dealing with complex data structures. One example is CBT Nuggets, an online IT training provider that offers over 5,000 courses from basic computer skills to network management. They use Realm to provide streaming videos for subscribers to access content anytime, anywhere through desktop or a mobile app, with cross-platform SDKs developed using Realm and MongoDB Atlas Device Sync.

If your application is built with an object-oriented language, then there is likely an OOD or document DB that couples well with your language.

**The advantages of object-oriented databases**

The main advantage of Object-Oriented Databases (OOD) over Relational Databases (RDBMS) is the ability to quickly query complex relationships without slow "joins." The database structure closely mirrors programming objects, making the code simpler. For instance, in RDBMS, tasks must be decomposed into attributes for storage, while in OOD, the whole object can be stored directly. This eliminates the need for retrieval and composition processes, making data manipulation more efficient.

**The disadvantages of object-oriented databases**

1. Object-oriented databases (OOD) are beneficial for managing complex data in object-oriented programming but may have performance trade-offs for simpler operations. Unlike relational database users who benefit from SQL standards, OOD users may lack widely adopted standards and have language-dependent querying syntax. 

2. OOD users may also have a smaller community compared to the web development community using relational databases, but it is rapidly expanding and catching up.


### Classification Based on User Numbers

DBMS can be classified based on the number of users it supports, there are **Single User Systems** that support one at a time, and other **Multiple Users Systems** that support many users simultaneously.

### Classification Based on Database Distribution

Four main database distribution systems categorize DBMS based on usage:

#### Centralized systems

A centralized database system stores the DBMS and database at a single site used by multiple systems.

<img src="http://opentextbc.ca/dbdesign01/wp-content/uploads/sites/11/2013/12/Centralized-Systems-300x174.jpg" width="400" height="200">

#### Distributed database system

Database and DBMS software are distributed across sites connected by network.

<img src="http://opentextbc.ca/dbdesign01/wp-content/uploads/sites/11/2013/12/Distributed-Systems-300x217.jpg" width="400" height="200">

#### Homogeneous distributed database systems

Utilize identical DBMS software across multiple sites, enabling seamless data exchange.

<img src="https://www.researchgate.net/publication/51966036/figure/fig1/AS:669966093279232@1536743772007/Homogeneous-Distributed-Database-Self-Creation.png" width="300" height="300">

#### Heterogeneous distributed database systems

Different sites in a distributed database system may use various DBMS software, with common software for data exchange. Hence, translations are required for different sites to communicate.

<img src="https://www.oreilly.com/api/v2/epubs/9781787126992/files/assets/25e2d7f9-616a-4acf-8d0e-a8b02f297930.png" width="400" height="300">

<!-- ---------------------------------------------------------------------- -->

## Schema Design

A database schema is a description of how data is structured or organized in a database.
It is a formal description of the structure or organization of a particular database (DB). Database schema design impacts database efficiency and information retrieval speed.
There are six types of database schemas: flat, hierarchical, network, relational, star, snowflake.

The term database schema is widely used for relational database schema, which organizes information in tables and uses the SQL query language. Non-relational databases, such as NoSQL, have different formats and lack a traditional schema but still have an underlying structure.

**There are two fundamental components of any database schema:**

1. Physical database schema: it defines how you store data in the storage system,  and the used form of storage (files, key-value pairs, indices, etc.) 

2. Logical database schema: we define the constraints of data, tables, relations, views, and integrity. These constraints define how data is related to each other.

#### Types of Database Schemas

<img src="https://cdn.buttercms.com/bWoVhJqHQhe10KOj2Oab" width="500" height="300">

1. **Flat model:** It organizes data in a single, two-dimensional display such as Microsoft Excel spreadsheet or a CSV file. It is suitable for simple tables and databases without complex relationships between different entities.

2. **Hierarchical model:** It has a tree structure with child nodes branching out of it. It is ideal for storing nested data such as family tree.

3. **Network model:** It treats data as nodes connected to each other. It allows for more complex connections, such as many-to-many relationships and cycles. It can model the movement of goods and materials between locations or the workflows required to accomplish a particular task.

4. **Relational model:** This model uses tables to relate entities in rows and columns.

5. **Star schema:** is an evolution of the relational model that organizes data into facts and dimensions. Fact data is numerical (ex: the number of sales of a product), while dimensional data is descriptive (ex: a product’s price, color, weight, etc.).

6. **Snowflake schema:** It is a further abstraction on top of the star schema. The fact table in a snowflake schema connects to a dimensional table to enhance database descriptions. Named for snowflake patterns, it features smaller structures branching off central arms.

### Database Schema Design

Database schema design, also known as SQL schema design, involves creating a blueprint for storing large amounts of data in a database. It determines data types and relationships between them to make data retrieval, manipulation, and interpretation easier. This design organizes data into entities, establishes relationships between them, and applies constraints. Database designers use schemas to provide a logical understanding of data to users like programmers and analysts.

Database schemas define the structure of a database and ensure data consistency, unique primary keys, and no important data is omitted. Schemas can be represented visually or using formulas/constraints. Different databases have their ways of defining schemas, but common systems like MySQL, Oracle Database, and Microsoft SQL Server support the CREATE SCHEMA statement. 

For example, a schema for a database may include tables like "Owners" to outline the necessary structure for the data.

<img src="https://i.sstatic.net/3iKAL.png" width="600" height="300">

This single schema contains valuable information such as:

1. The title of each table
2. The fields each table contains
3. The relationships between tables (for example, linking an employee’s overtime pay to their identity via their ID number)

Developers and database administrators can then convert these schema tables into SQL code.


### Best Practices for Database Schema Design

1. **Naming Conventions:**

* Utilize proper naming conventions for database schema designs to enhance their efficiency. 
* Consistency in naming fields is crucial, whether following a specific style or adhering to an ISO standard. 
* Avoid using reserved words to prevent syntax errors. 
* Steer clear of hyphens, quotes, spaces, or special characters, as they can complicate matters or be invalid. 
* Use singular nouns in table names to represent collections, omitting unnecessary verbiage. For instance, use "StudentName" instead of "StudentNames" and "Department" instead of "DepartmentList" or "TableDepartments".

2. **Security:**

Secure data by designing a strong database schema and encrypting confidential information like PII and passwords. Use user authentication for database access, avoiding admin role distribution to users.

3. **Documentation:**

Good documentation for database schemas is essential for future use. Include explicit instructions and comment lines in scripts, triggers, and commands for clear understanding by others.

4. **Normalization:**

Normalization separates entities and relationships in different tables to minimize redundancy and enhance database integrity for optimal performance. Be cautious of over-normalization and under-normalization.

5. **Expertise:**

Analyzing data attributes is crucial for creating an effective schema design to accommodate exponential data growth. Continuously evaluate each field in relation to others in your schema for optimal performance.

### Schema-based Constraints

#### Domain Constraints
* Domain constraints specify that within each tuple, the value of each
attribute A must be an atomic value from the domain dom(A).

* The data types associated with domains typically include standard
numeric data types for integers (such as short integer, integer, and long
integer) and real numbers (float and double-precision float).

* Characters, Booleans, fixed-length strings, and variable-length strings are
also available, as are date, time, timestamp, and other special data types.

 Domains can also be described by a subrange of values from data
type or as an enumerated data type in which all possible values are
explicitly listed.

#### Key Constraints

* Superkey (SK) of Relation: It is a set of attributes as
• No two tuples in any valid relation state r(R) will have the same value for SK

* Key of R:
• A "minimal" superkey
• That is, a key is a superkey K such that the removal of any attribute from K results in
a set of attributes that is not a superkey (does not possess the super key
uniqueness property)

* We call such a key a Primary Key. If a relation has several candidate keys, one is chosen arbitrarily to be the primary key.
• The primary key attributes are underlined. The primary key value is used to uniquely identify each tuple in a relation. It provides the tuple identity.

#### Entity Integrity

• The primary key attributes PK of each relation schema cannot have null values in any tuple.

• This is because primary key values are used to identify the individual tuples.

• If PK has several attributes, null is not allowed in any of these attributes.

• Note: Other attributes of Relation may be constrained to disallow null values, even though they are not members of the primary key.

#### Referential Integrity

• Tuples in the referencing relation R1 have attributes FK (called foreign
key attributes) that reference the primary key attributes PK of the
other referenced relation R2.

• A tuple t1 in Relation 1 is said to reference a tuple t2  in Relation 2 if t1[FK] = t2[PK].
• The value in the foreign key column (or columns) FK of the referencing relation
can be either:

1.  a value of an existing primary key value of a corresponding primary key
PK in the referenced relation R2, or

2. a null.

<!-- ---------------------------------------------------------------------- -->

## Best practices for data storage and retrieval

Efficient data storage and retrieval are paramount for any database-driven application. This section will delve into key best practices to optimize these processes.

### Database Design and Schema Optimization

#### Normalization:

Ensure data integrity and reduce redundancy by adhering to normalization principles. However, consider denormalization for performance-critical scenarios.

#### Data Types

Choose appropriate data types to minimize storage space and improve query performance.

#### Indexing
Create indexes on frequently queried columns to accelerate data retrieval. Avoid over-indexing as it can impact write performance. Understanding indexing options before choosing a strategy can enhance query selection and database performance.

1. **Identify key queries and columns:** Before starting indexing, analyze the types of queries your app frequently runs and the columns involved. This helps prioritize efforts where it matters most. For instance, in an online bookstore app, indexing the "author" column can boost search query performance significantly. Avoid wasting time and energy on indexing columns rarely used.

Data orchestration tools can examine query patterns and usage statistics to pinpoint the most commonly executed queries in your database.

Orchestration in data management involves coordinating tasks such as collecting, processing, and analyzing data from various sources to ensure efficient operations. 

Database administrators can improve efficiency by prioritizing indexing on columns frequently used in queries.

2. **Regularly monitor and tune indexes:** Regularly checking and adjusting indexes is crucial as data and query patterns can change over time. Just like in MLOps, where ongoing monitoring is necessary for model effectiveness, reviewing and fine-tuning indexes is essential for their optimal performance in managing data efficiently.

Neglecting to address this issue can result in a buildup of technical debt, causing a decline in performance and higher maintenance costs. Utilize SQL tools such as MySQL's EXPLAIN or Microsoft SQL Server's Query Execution Plan to gain insight into query execution and index utilization. This will aid in identifying areas for adding new indexes, removing unnecessary ones, and optimizing existing ones to improve query efficiency.

3. **Consider using covering indexes:** A covering index contains all required columns for a query, eliminating the need to access the base table. It is like having the necessary folders in front of you, saving time by avoiding searching through the entire cabinet. Covering indexes speed up search queries by reducing disk I/O operations.

4. **Monitor and manage index fragmentation:**
Index fragmentation happens when the order of index pages doesn't match their physical placement, leading to inefficient data storage and slow search queries. It's similar to a library's card catalog not aligning with book locations. Without addressing this issue, it worsens with additional or updated data. Regularly monitoring and organizing indexes is crucial to maintaining efficiency.

Containerization assists in managing databases effectively by offering a structured environment. Modern systems include tools for identifying and resolving index fragmentation through index rebuilding or reorganization.

**Indexing Strategies**

1. **Single-column indexes** are effective for databases with a large number of rows, where queries often filter or sort data based on a single column, like looking up users by their usernames for faster retrieval.

2. **Composite indexes** are more useful for queries involving multiple columns in a WHERE clause, or operations like ORDER BY and GROUP BY, such as searching for sales by date and location together in a sales database.

3. **Unique indexes** ensure data integrity by enforcing uniqueness on one or more columns, ideal for columns like primary keys or email addresses to avoid duplicate values.

<img src="https://developernation.net/_gatsby/image/c9c3e57e290ffea936757d5d0a58b4e5/acd3a719ebd6ac78cd8be89de96cbe0c/image3.png?u=https%3A%2F%2Fwordpress.developernation.net%2Fwp-content%2Fuploads%2F2024%2F03%2Fimage3.png&a=w%3D661%26h%3D281%26fm%3Dpng%26q%3D90&cd=2024-03-28T11%3A43%3A03" width="600" height="300">

4. **Clustered indexes** physically store rows in order based on the index key, enhancing range queries or sequential scans, like organizing time-series data by date for quicker chronological information retrieval.

5. **Covering indexes** include all necessary information to answer a query without reverting to the original data table, beneficial for SELECT, JOIN, and WHERE clauses to improve query performance, especially for data-driven insights or complex queries involving multiple columns or tables.

6. **Partial indexes** cover only a subset of data that is frequently queried, reducing index size and enhancing query performance, like indexing active users in a user table where only rows with “active = true” are indexed.

7. **Expression indexes** are created based on expressions or functions applied to columns, useful for queries involving computed values or transformations like indexing the result of mathematical operations or string concatenations.

8. **Hash indexes** provide fast access to data with low cardinality columns or when randomly accessing a large number of rows, particularly suitable for scenarios like indexing boolean or enumerated columns.

For organizations managing large-scale data processing tasks, implementing various types of indexes can significantly improve query performance, especially during critical periods like website launches. Utilizing a comprehensive website launch checklist can help ensure that database infrastructure is adequately prepared to handle increased traffic and demands on query performance

**Example**

Scenario: E-commerce Product Catalog
Problem: An online store with a large product catalog experiences slow performance when customers search for products by price range.

Solution: Create an index on the price column of the products table.

Explanation:

Products table:
````
product_id (INT, PRIMARY KEY)
name (VARCHAR(255))
description (TEXT)
price (DECIMAL(10,2))
category_id (INT)
````
... other columns

**Without an index:** When a user searches for products between a specific price range, the database has to scan every row in the products table to find matching products. This can be extremely slow for large catalogs.

**With an index:** An index on the price column creates a sorted structure (usually a B-tree) that points to the rows where each price value exists. When a query for a price range is executed, the database can efficiently use the index to quickly locate the relevant price ranges and access only the corresponding rows.

SQL Example:
````
CREATE INDEX idx_products_price ON products(price);
````

#### Partitioning

Divide large tables into smaller, manageable chunks for better performance and scalability.

The code block shown below describes the process of creating and adding partitions to an SQL table.

<img src="https://nithub.unilag.edu.ng/wp-content/uploads/2024/05/num-1-min.png" width="600" height="300">

This code establishes a new table named “sales” within the database. The table is defined with three columns:

**id:** This column is an integer (INT) and acts as the primary key. Primary keys ensure each row has a unique identifier.

**product_name:** This column stores product names as strings (VARCHAR) with a maximum length of 255 characters.

**sale_date:** This column captures the date of each sale using the DATE data type.

The NOT NULL constraint specified after each column definition enforces that these columns cannot contain missing values. Finally, the ENGINE=InnoDB clause indicates that the InnoDB storage engine, a popular choice for MySQL tables, will be used for this table.

### Query Optimization

**Query Profiling:** Identify slow queries and analyze their execution plans to pinpoint performance bottlenecks.

**Indexing:** Ensure proper indexing for frequently used search criteria.

**Query Structure:** Optimize query structure by avoiding unnecessary subqueries, joins, and function calls.

**Caching:** Implement caching mechanisms to store frequently accessed data in memory for faster retrieval.

Caching can be applied to any type of database including relational databases such as Amazon RDS or NoSQL databases such as Amazon DynamoDB, MongoDB and Apache Cassandra. 

<img src="https://d1.awsstatic.com/product-marketing/caching-database-caching-diagram.70a0c9d62877d7a32bf1024d00561eb5b560a45d.PNG" width="600" height="300">

A database cache reduces strain on primary database by saving frequently accessed read data, stored separately.

### Data Storage and Retrieval Techniques

1. **Compression:** Compress data to reduce storage space and improve I/O performance.

2. **Data Replication:** Create multiple copies of data for high availability and disaster recovery.

3. **Data Sharding:** Distribute data across multiple servers for scalability and performance.

4. **Content Delivery Networks (CDNs):** Offload static content to CDNs to reduce database load and improve response times.

### Database Management and Maintenance

#### Regular Backups: 

Implement a robust backup strategy to protect data from loss or corruption.

#### Performance Monitoring:

Continuously monitor database performance metrics to identify and address issues proactively.

#### Database Tuning:

Database tuning involves adjusting various configuration parameters to align the database system's behavior with the specific demands of its workload. It's a delicate balance between maximizing performance, resource utilization, and ensuring system stability.

##### Understanding Workload Characteristics

Before diving into parameter tuning, it's crucial to analyze the database's workload. Key characteristics to consider include:

**Transaction rate:** Number of transactions per second.

**Query complexity:** Average query execution time.

**Data volume:** Size of the database and growth rate.

**Concurrency level:** Number of concurrent users or sessions.

**I/O patterns:** Read/write ratio, sequential vs. random access.

##### Key Configuration Parameters

Different database systems have varying sets of parameters. However, some common categories include:

**Buffer cache:** 

* Purpose: Stores frequently accessed data blocks in memory for rapid retrieval.

* Impact: Significantly improves query performance by reducing disk I/O operations.

* Example: When a query requests data, the database first checks the buffer cache. If the data is found there (a cache hit), it's retrieved directly from memory, bypassing disk access.

**Shared pool:** 

* Purpose: Stores parsed SQL statements, execution plans, and other shared data structures.

* Impact: Enhances query performance by reusing parsed statements and execution plans, reducing CPU overhead.

* Example: When a SQL statement is executed, the database first checks the shared pool for an existing execution plan. If found, it's reused, avoiding the time-consuming process of parsing and optimizing the SQL again.

##### Tuning Process

**Baseline performance:** Establish a performance baseline to measure improvements.

**Identify bottlenecks:** Use performance monitoring tools to find performance bottlenecks.

**Adjust parameters:** Modify relevant parameters based on workload characteristics and bottleneck analysis.

**Testing and monitoring:** Implement changes in a controlled environment and monitor their impact.

**Iterative refinement:** Continuously analyze and adjust parameters as needed.

**Example:** Tuning Buffer Cache

If a database experiences high read I/O, increasing the buffer cache size can improve performance by reducing disk access. However, excessive buffer cache size can consume memory that might be better used for other purposes.

### Additional Considerations

**Data Governance:** Establish clear data ownership, access controls, and data quality standards.

**Data Retention Policies:** Define data lifecycle management and retention periods to optimize storage usage.

**Data Privacy:** Comply with relevant data privacy regulations (e.g., GDPR, CCPA).

### Case Studies and Examples

To illustrate these concepts, consider real-world examples:

**E-commerce:** Optimize product catalogs, order processing, and customer data for fast search and checkout.

**Social Media:** Handle massive user data, content, and interactions efficiently.
Financial Services: Ensure data integrity, security, and performance for transactions and reporting.

By following these best practices and tailoring them to specific requirements, organizations can significantly enhance database performance, scalability, and reliability.

<!-- ---------------------------------------------------------------------- -->

## References <br />

1. [CISCO](https://www.appdynamics.com/topics/database-management-systems)

2. [BCcampus](https://opentextbc.ca/dbdesign01/chapter/chapter-6-classification-of-database-systems/)

3. [Board](https://www.boardinfinity.com/blog/relational-model-in-dbms/)

4. [prepinsta](https://prepinsta.com/dbms/object-oriented-database-model/)

5. [DataMation](https://www.datamation.com/big-data/what-is-a-hierarchical-data-model-definition-and-examples/)

6. [Integrate](https://www.integrate.io/blog/complete-guide-to-database-schema-design-guide/#:~:text=DB%20schema%20design%20organizes%20data,a%20logical%20understanding%20of%20data.),

7. [ResearchGate](https://www.researchgate.net/publication/234797241_Database_schema_design_An_experimental_comparison_between_normalization_and_information_analysis)

8. [DeveloperNation](https://developernation.net/blog/8-indexing-strategies-to-optimize-database-performance/)

9. [nitHub](https://nithub.unilag.edu.ng/database-partitioning-and-sharding/#:~:text=Partitioning%20breaks%20down%20large%20datasets,distributes%20data%20across%20multiple%20servers.)

10. [Microsoft](https://learn.microsoft.com/en-us/power-platform/well-architected/performance-efficiency/optimize-data-performance)

11. [Amazon](https://aws.amazon.com/caching/database-caching/#:~:text=Overview,to%20reduce%20your%20database%20costs.)

12. [MongoDB](https://www.mongodb.com/resources/basics/databases/what-is-an-object-oriented-database)
