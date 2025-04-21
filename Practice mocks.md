### ❓Q1.

**What is the difference between `IEnumerable` and `IQueryable` in C#? When would you use each?**
- **`IEnumerable<T>`**: This is a more general interface used to represent a collection of objects that can be iterated over. It's in-memory and typically used when you have already retrieved the data from the database. If you're working with an in-memory collection, like a list or an array, you would return `IEnumerable`.
    
- **`IQueryable<T>`**: This is used for queries that are meant to be executed against a database or an external data source. It's designed to represent a query that hasn’t yet been executed. `IQueryable` supports deferred execution, meaning the query doesn’t run until you iterate over it (or call a method like `.ToList()` or `.First()`).
    

### Key Difference:

- **`IEnumerable`**: Works with in-memory data.
    
- **`IQueryable`**: Works with external data sources (like databases), and the query is executed against that source.
    

### When to use each:

- Use **`IQueryable`** when you want to build a query that will be executed by the database. For example, LINQ queries executed against a database will use `IQueryable`.
    
- Use **`IEnumerable`** when you're working with data that is already in memory and don’t need the ability to build queries dynamically.

### **Difference Between `IEnumerable` and `IQueryable` in C#**

- **`IEnumerable<T>`**:
    
    - Represents a collection of objects that can be iterated over.
        
    - It’s used for in-memory collections, like lists, arrays, etc.
        
    - Once you have the data in memory, you use `IEnumerable` to work with it.
        
    - It does not support query construction. The data must already be fetched.
        
- **`IQueryable<T>`**:
    
    - Represents a query that is executed against an external data source, typically a database.
        
    - It supports deferred execution, meaning the query isn't executed until it's enumerated.
        
    - It’s used to build queries that can be translated into a language like SQL, and then executed on the database.
        

### **Key Differences**:

- **`IEnumerable`**: Used for in-memory collections.
    
- **`IQueryable`**: Used for querying external data sources, such as databases.
    

### **When to Use Each**:

- **Use `IQueryable`** when you want to build a query that will be executed against a database. LINQ queries are often executed using `IQueryable`.
    
- **Use `IEnumerable`** when you're working with data that’s already loaded in memory.
### ❓Q2.

**Can you briefly explain how Dapper works under the hood, and why it is considered a micro ORM?**
### **Conceptual Feedback**:

- You correctly mentioned that Dapper is lightweight and flexible, which are key characteristics.
    
- However, it would help to explain a bit more about **how** Dapper works under the hood:
    
    - Dapper is a micro ORM because it doesn't abstract away SQL in the same way larger ORMs like Entity Framework do. Instead, it allows you to write raw SQL queries while still providing some ORM-like capabilities, such as mapping query results to objects.
        
    - Dapper is fast because it avoids the overhead of tracking changes and managing object states, which other ORMs often do.
        
    - It’s not really a full-fledged ORM; instead, it's a "micro ORM" because it focuses only on the basic features needed for data access, without the additional features you might find in larger ORMs like Entity Framework.
      
    ### ❓Q3.

**How do you handle exceptions in a typical .NET Web API project?**
### **Conceptual Feedback**:

- Exceptions are indeed errors, but in .NET, they are objects that provide detailed information about the error (such as the type of error, where it occurred, and the stack trace).
    
- Handling exceptions involves catching them and responding appropriately. In a Web API project, you typically handle exceptions using **try-catch blocks** or **middleware**.
    
    - **Try-catch** blocks are used within methods to catch exceptions as they occur.
        
    - **Global exception handling** in .NET Web API is often done using **middleware** (like custom exception filters or using `UseExceptionHandler` in the `Startup.cs` file) to catch unhandled exceptions globally and return meaningful HTTP responses.
    ### ❓Q4.

**What is a primary key in MySQL, and why is it important?**
### **Conceptual Feedback**:

- You correctly mentioned that a primary key ensures **uniqueness** in a table, which is the most important property of a primary key.
    
- A primary key does **not allow duplication** of its values in the table, which prevents inserting rows with the same primary key value.
    
- You also brought up **foreign keys**, which is a good point. A primary key in one table can be used as a **foreign key** in another table to create relationships between them.
    

However, it’s important to note that the primary key isn’t just about uniqueness. It also implicitly defines the **row identity** and is often used for efficient searching and indexing in the database.

### **Refined Answer**:

_"A primary key in MySQL is a column (or a set of columns) that uniquely identifies each row in a table. It ensures that no two rows can have the same value in the primary key column(s). The primary key also automatically creates an index on that column for fast lookups. Additionally, the primary key can be used in other tables as a foreign key to establish relationships between tables, which helps maintain referential integrity."_

### ❓Q5.

**How would you retrieve the top 5 highest-paid employees from an `Employees` table in MySQL?**
### **Conceptual Feedback**:

- You mentioned using `ORDER BY`, which is correct! To retrieve the top 5 highest-paid employees, you would:
    
    1. **Sort the employees** by salary in descending order using `ORDER BY salary DESC`.
        
    2. **Limit the result** to the top 5 rows using `LIMIT 5`.
        

Here’s a more detailed explanation and example:

sql

CopyEdit

`SELECT * FROM Employees ORDER BY salary DESC LIMIT 5;`

- This query will retrieve the top 5 employees based on their salary, ordered from highest to lowest.### **Conceptual Feedback**:

- You mentioned using `ORDER BY`, which is correct! To retrieve the top 5 highest-paid employees, you would:
    
    1. **Sort the employees** by salary in descending order using `ORDER BY salary DESC`.
        
    2. **Limit the result** to the top 5 rows using `LIMIT 5`.
        

Here’s a more detailed explanation and example:

sql

CopyEdit

`SELECT * FROM Employees ORDER BY salary DESC LIMIT 5;`

- This query will retrieve the top 5 employees based on their salary, ordered from highest to lowest.
