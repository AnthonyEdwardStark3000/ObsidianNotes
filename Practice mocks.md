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
