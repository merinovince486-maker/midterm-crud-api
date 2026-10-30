README.md ACTIVITY 7

# Reflection Questions

### 1. What was the most challenging part of building this API?

The most challenging part of building this API was connecting the application to the MySQL database using TypeORM and fixing errors during development. I also had difficulty configuring TypeScript, creating entities, and making sure the CRUD operations worked correctly. I learned that every part of the application must be properly configured for the API to work.

### 2. How does TypeORM make database operations easier compared to raw SQL?

TypeORM makes database operations easier because it allows developers to use TypeScript classes and objects instead of writing SQL queries manually. It provides methods such as `find()`, `findOne()`, `create()`, `save()`, and `remove()` to perform database operations. It also helps manage relationships between tables and makes the code easier to understand and maintain.

### 3. Why is it important to exclude the password field from API responses? How did you implement this?

It is important to exclude passwords from API responses because passwords are confidential user information. Exposing them could create security risks if someone accesses the API response. I implemented this using `select: false` in the password column of the User entity. This prevents TypeORM from including the password in normal database queries by default.

### 4. Describe a scenario where you would need to use database transactions instead of individual operations.

A database transaction is useful when performing multiple related operations that must all succeed together. For example, when placing an order, the system might need to create an order record, save the order details, and update the product stock. If one operation fails, a transaction can roll back the changes to prevent incomplete or inconsistent data.

### 5. What is the difference between `synchronize: true` and migrations? When should you use each?

`synchronize: true` automatically updates the database structure based on the entities in the application. It is useful during development because it saves time when making changes to entities.

Migrations are files that contain specific database structure changes. They allow developers to control, track, and apply database updates safely. I would use `synchronize: true` during development and migrations for production environments because they provide better control over database changes.

### 6. If you had to add a `Product` entity with a relationship to `User` (a user can have many products), how would you modify the code?

I would create a new `Product` entity with fields such as `id`, `name`, `price`, and `quantity`. I would use a `ManyToOne` relationship in the Product entity because many products can belong to one user. In the User entity, I would add a `OneToMany` relationship because one user can have many products.

I would also register the Product entity in the DataSource configuration and create a ProductController and product routes to perform CRUD operations.

### 7. What security improvements would you make before deploying this API to production?

Before deploying the API to production, I would improve its security by adding password hashing using bcrypt so passwords are not stored as plain text. I would also implement authentication and authorization to make sure only authorized users can access protected resources. Additionally, I would add rate limiting to prevent too many requests, validate user inputs, use HTTPS, and protect sensitive information through environment variables. These improvements would make the API more secure and reliable.


ACTIVITY 7..1


# Reflection Questions

### 1. What was the most challenging part of building this API?

The most challenging part of building this API was connecting the application to the MySQL database using TypeORM and fixing errors during development. I also experienced difficulties configuring TypeScript, creating entities, and making sure all CRUD operations worked correctly. Through this activity, I learned how to troubleshoot errors and understand how the different parts of an API work together.

### 2. How does TypeORM make database operations easier compared to raw SQL?

TypeORM makes database operations easier because it allows developers to use TypeScript classes and objects instead of writing SQL queries manually. It provides methods such as `find()`, `findOne()`, `create()`, `save()`, and `remove()` to perform database operations. It also makes managing relationships between tables easier and keeps the code organized.

### 3. Why is it important to exclude the password field from API responses? How did you implement this?

It is important to exclude passwords from API responses because passwords are confidential user information. Exposing them could create security risks if someone accesses the API. I implemented this by using `select: false` in the password column of the User entity. This prevents TypeORM from including the password in normal database queries by default.

### 4. Describe a scenario where you would need to use database transactions instead of individual operations.

A database transaction is useful when multiple related operations must succeed together. For example, when creating a task and adding its comments, both operations may need to be completed successfully. If one operation fails, a transaction can roll back the changes to prevent incomplete or inconsistent data.

### 5. What is the difference between `synchronize: true` and migrations? When should you use each?

`synchronize: true` automatically updates the database structure based on the entities in the application. It is useful during development because it saves time when making changes to entities.

Migrations are files that contain specific database structure changes. They allow developers to track and control database updates. I would use `synchronize: true` during development and migrations in production because migrations provide better control and help prevent unexpected database changes.

### 6. If you had to add a Comment entity (tasks can have many comments), how would you modify the code?

I would create a new Comment entity with properties such as `id`, `content`, `createdAt`, and `taskId`. I would use a `ManyToOne` relationship in the Comment entity because many comments can belong to one task. In the Task entity, I would add a `OneToMany` relationship because one task can have many comments.

I would also register the Comment entity in the DataSource configuration and create a CommentController and comment routes to perform CRUD operations.

### 7. What security improvements would you make before deploying this API to production?

Before deploying the API to production, I would improve its security by adding password hashing using bcrypt so passwords are not stored as plain text. I would also implement authentication and authorization to ensure that only authorized users can access protected resources. Additionally, I would add rate limiting to prevent too many requests, validate user inputs, use HTTPS, and protect sensitive information using environment variables. These improvements would make the API more secure and reliable.

### 8. Why did you need to add the `!` (definite assignment operator) to your entity properties?

I needed to add the `!` operator because TypeScript's strict property initialization checks require class properties to be initialized when they are declared or inside a constructor. In TypeORM, entity properties are usually populated when data is retrieved from the database. The `!` operator tells TypeScript that these properties will be assigned later and should not be treated as uninitialized.

### 9. What are the benefits of explicitly defining column types (e.g., `type: 'varchar'`) in your entities?

Explicitly defining column types helps make the database structure clear and predictable. It tells TypeORM what type of data should be stored in each column, such as `varchar` for text, `int` for numbers, and `boolean` for true or false values. It also allows developers to specify options like column length and whether a field can contain NULL values.

### 10. How do relationships in TypeORM differ from foreign keys in raw SQL? What are the advantages?

In raw SQL, developers manually define foreign keys to connect related tables. In TypeORM, relationships can be defined using decorators such as `OneToMany`, `ManyToOne`, and `OneToOne`. TypeORM uses these relationships to manage the database connections and foreign keys.

The advantage is that developers can work with related data using TypeScript objects instead of writing complex SQL JOIN queries manually. It also makes the code easier to read, organize, and maintain.