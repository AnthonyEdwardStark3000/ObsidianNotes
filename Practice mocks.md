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
### ❓Q6.

**In Angular, what are lifecycle hooks? Can you name a few and explain their purpose?**
- **Lifecycle hooks** in Angular are methods that are invoked at specific stages of a component’s lifecycle. They give developers control over the initialization, update, and destruction of components.
    
- You mentioned `ngOnInit()` and `ngOnDestroy()`, which are two common lifecycle hooks.
    
- However, the distinction you made between a component and a service needs clarification:
    
    - A **component** has lifecycle hooks because it’s tied to the view and its lifecycle events (like initialization and destruction).
        
    - A **service**, on the other hand, doesn’t have lifecycle hooks because it typically exists for the lifetime of the application (or until it’s explicitly destroyed via dependency injection).
        

You could mention other common lifecycle hooks like `ngOnChanges()` and `ngAfterViewInit()` as well.

### **Full Explanation**:

Here’s an improved and more detailed answer:

- **Lifecycle hooks** are methods that Angular calls at various points during the life of a component. They allow you to tap into specific stages of the component's lifecycle to perform actions.
    
- **Common lifecycle hooks include**:
    
    1. **`ngOnInit()`**: Called once after the component’s input properties are set. It’s used for component initialization.
        
    2. **`ngOnChanges()`**: Called when input properties change. It’s useful for reacting to changes in input data.
        
    3. **`ngAfterViewInit()`**: Called after the component’s view has been initialized. It’s often used to interact with the component’s view elements.
        
    4. **`ngOnDestroy()`**: Called just before Angular destroys the component. It’s useful for cleanup, like unsubscribing from observables or cleaning up timers.
       
    "Lifecycle hooks in Angular are methods that occur at specific points during a component's life. For example, `ngOnInit()` is called when a component is initialized, and `ngOnDestroy()` is called when a component is destroyed. These hooks help manage actions related to the component's lifecycle, such as initialization, property changes, and cleanup. Services don’t have lifecycle hooks because they aren’t tied to the lifecycle of the view like components are."
    - **Components**: Have lifecycle hooks because they are tied to the view (UI).
    
- **Services**: Are typically singleton objects that exist for the lifetime of the application, so they don’t have lifecycle hooks like components.
  ### ❓Q7.

**What is dependency injection in .NET, and why is it important in modern application development?**
- **Dependency Injection (DI)** is an **Inversion of Control** (IoC) pattern. The core idea is that instead of manually creating objects (like a service or a repository), we rely on an external container to manage the instantiation and lifecycle of these objects.
    
- You correctly mentioned that DI is related to **constructor injection** — this is a common form of DI in .NET, where dependencies are provided through a class constructor rather than the class creating them directly.
    
- The three **lifetime types** for DI in .NET are:
    
    1. **Singleton**: A single instance is created and shared throughout the application’s lifetime.
        
    2. **Scoped**: A new instance is created per scope, often tied to a single request (in web applications).
        
    3. **Transient**: A new instance is created each time it is requested.
        

These lifetimes determine how and when the objects are created and disposed of.
### **Improved Answer**:

_"Dependency Injection (DI) is an Inversion of Control (IoC) pattern where the creation of an object is delegated to a container or framework, rather than the class itself. In .NET, DI helps improve **decoupling** between components, making code more testable and maintainable. The main methods of dependency injection in .NET are:_

- **Singleton**: The same instance is shared throughout the application’s lifetime.
    
- **Scoped**: A new instance is created for each request or scope (usually within the context of a web request).
    
- **Transient**: A new instance is created each time it’s requested.
    

Using DI promotes **loose coupling** and makes the application easier to manage, test, and extend."_
_"Dependency Injection is an Inversion of Control (IoC) pattern that allows objects to be created by a container rather than the class itself. This helps decouple components, making the application easier to manage and test. There are three main lifetimes in DI: Singleton, Scoped, and Transient. These lifetimes determine how often instances of a service are created."_
- **Inversion of Control (IoC)**: This principle means that the flow of control is inverted. Instead of a class controlling its own dependencies, an external container (like the built-in DI container in .NET) provides the necessary objects.
    
- DI in .NET helps in building **testable**, **maintainable**, and **flexible applications**. It allows you to easily swap out implementations (e.g., for testing) without modifying the dependent class.
### ❓Q8.

**In Angular, what are Observables and how do they differ from Promises?**
Both **Observables** and **Promises** deal with **asynchronous operations**, but there are some key differences:

1. **Promises**:
    
    - A **Promise** represents a single value that will be resolved in the future. It either resolves with a value or rejects with an error, and you can only handle it once.
        
    - Promises are **eager** — they start executing as soon as they are created, and you can only use `.then()` or `.catch()` to handle their results.
        
2. **Observables**:
    
    - **Observables** are more powerful because they allow **multiple asynchronous events** over time (not just one like Promises). They can emit multiple values (or none), and you can listen for updates continuously.
        
    - They are **lazy** — they don't start executing until you subscribe to them.
        
    - Observables are often used in Angular for handling things like HTTP requests, event listeners, etc. You can use `.subscribe()` to get the emitted values.
    **Observables** are commonly used for **data sharing** between components, especially in Angular. For example, a parent component can emit data to a child component through an **Observable**, and the child can subscribe to that data.
    "In Angular, **Observables** and **Promises** both handle asynchronous operations, but they differ in important ways. A **Promise** is used for a single asynchronous value that resolves once, whereas an **Observable** can emit multiple values over time. Promises are **eager** — they execute immediately when created, and you handle them with `.then()` or `.catch()`. On the other hand, Observables are **lazy** — they don’t start executing until you **subscribe** to them, and they allow you to receive multiple values over time. This makes Observables useful for handling things like HTTP responses, events, or data sharing between components in Angular."
    - **Observables** are part of the **ReactiveX (RxJS)** library, which is a set of tools for working with asynchronous data streams.
    
- **Use cases for Observables in Angular** include:
    
    - **HTTP requests**: Angular’s HTTP client returns an Observable, which you can subscribe to.
        
    - **Event handling**: Like mouse clicks or keyboard events.
        
    - **Component communication**: Sharing data between parent and child components using Observables allows for more flexible and dynamic data flows.
### ❓Q9.

**Can you explain the SOLID principles? Please pick any two principles and describe them with examples.**
The **SOLID** principles are five key design guidelines in object-oriented programming that help make code more maintainable, extensible, and robust. The acronym stands for:

1. **S**ingle Responsibility Principle
    
2. **O**pen/Closed Principle
    
3. **L**iskov Substitution Principle
    
4. **I**nterface Segregation Principle
    
5. **D**ependency Inversion Principle
#### 1. Single Responsibility Principle (SRP)

- **Definition**: A class should have only one reason to change, meaning it should have only one job or responsibility.
    
- **Example**:
    
    - **Bad**: A `ReportManager` class that handles both generating report data _and_ formatting that report for display.
        
    - **Good**:
        
        - `ReportGenerator` class that only collects and processes the data.
            
        - `ReportFormatter` class that only handles converting that data into PDF, HTML, or other formats.
            

**Why it matters**: When responsibilities are separated, changes in one area (e.g., formatting) don’t affect unrelated parts (e.g., data generation).

#### 2. Dependency Inversion Principle (DIP)

- **Definition**:
    
    - High-level modules should not depend on low-level modules; both should depend on abstractions.
        
    - Abstractions should not depend on details; details should depend on abstractions.
        
- **Example**:
    
    - **Bad**: A `UserService` class directly instantiates a concrete `EmailSender` class to send emails:
    ```
    public class UserService {
  private EmailSender _emailSender = new EmailSender();
  // ...
}
        **Good**:
```
    public interface IEmailSender {
  void Send(string to, string subject, string body);
}

public class SmtpEmailSender : IEmailSender {
  public void Send(...) { /* SMTP logic */ }
}

public class UserService {
  private readonly IEmailSender _emailSender;
  public UserService(IEmailSender emailSender) {
    _emailSender = emailSender;
  }
  // ...
}
```
### ❓Q10.

**How do you ensure your application is secure against SQL Injection, especially when using Dapper?**

- **SQL Injection** is an attack where a malicious user can manipulate SQL queries by injecting harmful SQL code through user inputs.
    
- **Dapper** helps prevent SQL injection by using parameterized queries. In a parameterized query, placeholders (e.g., `@param`) are used in the SQL query instead of directly concatenating user input into the query string. This way, user input is treated as a value and not as executable SQL code.

### **Clarified Explanation**:

- When you use **query parameters** with Dapper, you’re essentially preventing SQL injection because Dapper will automatically handle sanitizing the user input.
    
- Instead of concatenating raw user input directly into your SQL query string, you pass the input as parameters, like `@Username`, `@Password`, and so on.
    
- This ensures that the values are treated safely, and the query structure (i.e., the SQL command itself) remains fixed, with values being passed as separate parameters.

### **Improved Answer**:

_"To prevent SQL injection when using Dapper, I use **parameterized queries**. Instead of concatenating raw user input directly into SQL queries, I pass the input as parameters. For example, in a query like `SELECT * FROM Users WHERE Username = @Username`, I use placeholders (like `@Username`) in the SQL query, and Dapper automatically replaces them with the actual values from the parameters during execution. This ensures that the input is treated as data, not executable SQL, which prevents malicious injection."_

### **Best Practices**:

- **Always use parameters**: Never concatenate user inputs directly into SQL queries.
    
- **Use parameterized methods in Dapper** like `Query`, `Execute`, and `QueryFirstOrDefault`, passing parameters as an anonymous object or a dictionary.
    
- **Avoid dynamic SQL**: If possible, avoid building SQL queries dynamically from user input.

### ❓Q11.

**Explain how you would implement transaction management in a .NET application using Dapper, and why transactions are important.**

- **Transaction management** is essential in database operations to ensure data consistency, especially when multiple operations need to be performed atomically (i.e., either all succeed or all fail).
    
- In .NET, with **Dapper**, you can manage transactions by starting a transaction, committing it if everything goes well, or rolling it back if something goes wrong.

### **Improved Answer**:

_"To implement transaction management in a .NET application using Dapper, I first establish a connection to the database. Then, I begin a transaction using the `BeginTransaction()` method. Inside the transaction, I perform the necessary database operations, passing the transaction object to each query. Once all queries are executed successfully, I commit the transaction using `commit()`. If any error occurs during the process, I catch the exception and roll back the transaction using `rollback()`. This ensures that either all changes are applied, or none are, maintaining the integrity of the database."_

```
using (var connection = new SqlConnection(connectionString))
{
    connection.Open();
    var transaction = connection.BeginTransaction();

    try
    {
        var query1 = "UPDATE Users SET Name = @Name WHERE Id = @Id";
        connection.Execute(query1, new { Name = "John", Id = 1 }, transaction: transaction);

        var query2 = "UPDATE Orders SET Status = @Status WHERE OrderId = @OrderId";
        connection.Execute(query2, new { Status = "Shipped", OrderId = 101 }, transaction: transaction);

        transaction.Commit();  // Commit the transaction if everything is successful
    }
    catch (Exception ex)
    {
        transaction.Rollback();  // Rollback if an error occurs
        Console.WriteLine("Transaction failed: " + ex.Message);
    }
}

```

### **Why Transactions Are Important**:

- **Atomicity**: All the operations within a transaction are treated as a single unit of work. Either all succeed, or none are applied.
    
- **Consistency**: The database will remain in a valid state, even if there’s a failure during an operation.
    
- **Isolation**: Ensures that intermediate changes within the transaction are not visible to other transactions, preventing inconsistencies.
    
- **Durability**: Once committed, the changes are permanent and will not be lost.

### ❓Q12.

**Explain how data binding works in Angular. What are the different types of data binding available?**

- **Data Binding in Angular** is a mechanism that allows you to synchronize the model (the data in your component) with the view (the UI). It’s used to connect your component's class properties with the DOM (Document Object Model).
    
- **Types of Data Binding** in Angular:
    
    - **One-Way Data Binding**: The data flows in one direction — either from the component to the view, or from the view to the component.
        
    - **Two-Way Data Binding**: This is more interactive. The data flows both ways — from the component to the view, and vice versa.
      
 - **One-Way Data Binding**:
    
    1. **String Interpolation**: This is used for binding data from the component to the view. The value from the component is inserted into the HTML.
        
        - Syntax: `{{ variable }}`
            
        - Example: `<h1>{{ title }}</h1>` will display the value of the `title` variable in the component.
            
    2. **Property Binding**: This binds a property in the component to a property in the DOM.
        
        - Syntax: `[property]="expression"`
            
        - Example: `<img [src]="imageUrl">` will set the `src` attribute of the `img` tag to the value of `imageUrl` in the component.
            
    3. **Event Binding**: This allows you to handle events in the view and send them to the component.
        
        - Syntax: `(event)="expression"`
            
        - Example: `<button (click)="onClick()">Click Me</button>` will call `onClick()` in the component when the button is clicked.
            
- **Two-Way Data Binding**:
    
    - Achieved with the `[(ngModel)]` directive, which allows synchronization between the view and the component. Changes in the view are automatically reflected in the component and vice versa.
        
    - Syntax: `[(ngModel)]="variable"`
        
    - Example: `<input [(ngModel)]="name">` binds the `name` property to the input field, so if the user types in the field, it updates the component’s `name` variable, and vice versa.
      
      