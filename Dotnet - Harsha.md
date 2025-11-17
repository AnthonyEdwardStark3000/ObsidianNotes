
# ASP.NET Core — Deep Explanation (Obsidian Friendly)

---

## What ASP.NET Core Really Is

ASP.NET Core is not just a web framework.  
It’s a **modern, high-performance request-processing engine** built on top of .NET, designed to let you assemble exactly the kind of web application you need using a flexible middleware pipeline.

Microsoft rebuilt it from scratch with priorities like:

- High performance
    
- Cross-platform execution
    
- Modular design
    
- Testability
    
- Cloud-native support
    
- Full developer control
    

ASP.NET Core is essentially a set of building blocks for creating:

- MVC apps
    
- REST APIs
    
- Razor apps
    
- Blazor apps
    
- Microservices
    
- Real-time apps (SignalR)
    

---

## Why ASP.NET Core Is So Fast

### 1. **Kestrel Web Server**

- Cross-platform, written in C#.
    
- Fully asynchronous, minimal allocations.
    
- Designed to handle millions of requests efficiently.
    
- Often outperforms Node.js, Java Spring, and even Go in benchmarks.
    

### 2. **Middleware Pipeline**

- Replaces old HttpModules/HttpHandlers.
    
- A simple, linear, customizable pipeline:
    

`Request → Middleware 1 → Middleware 2 → Routing → MVC → Response`

- Developers have full control:  
    add, remove, reorder, or replace pipeline components.
    

---

## Cross-Platform Advantages

Running on Windows, Linux, and macOS is not just a feature — it changes deployment strategy.

### Hosting Options

- IIS (Windows)
    
- Nginx/Apache (Linux)
    
- Docker containers
    
- Kubernetes
    
- Azure App Service
    
- AWS ECS/EKS
    
- Even Raspberry Pi
    

This brings:

- Lower hosting costs
    
- Flexible infrastructure
    
- Easier scaling
    

---

## Designed for Cloud From Day 1

### 1. **Flexible Configuration System**

Supports loading config from:

- JSON
    
- Environment variables
    
- Azure Key Vault
    
- Secret managers
    
- Command-line arguments
    

Different configs for:

- Development
    
- Staging
    
- Production
    

### 2. **Logging Providers**

Built-in support for:

- Console
    
- Debug
    
- File
    
- Azure Application Insights
    
- Elastic Stack
    
- Seq
    

Essential for distributed cloud applications.

---

## Built-in Dependency Injection (DI)

ASP.NET Core includes DI at the framework level:

- Controllers, services, middleware, DbContexts — all use DI.
    
- No need for third-party DI containers (though you can add one).
    
- Improves testability and separation of concerns.
    

DI is central to how ASP.NET Core apps are structured.

---

## The Four Development Models in ASP.NET Core

### 1. **ASP.NET Core MVC**

- Suitable for server-rendered web apps.
    
- Uses controllers, views (Razor), models, filters.
    
- Strong separation of concerns.
    

### 2. **ASP.NET Core Web API**

- For building REST APIs.
    
- Most modern applications rely on this.
    
- Supports:
    
    - Attribute routing
        
    - Model binding
        
    - Model validation (DataAnnotations)
        
    - Filters (Auth, Logging, Exception handling)
        

### 3. **Razor Pages**

- A page-focused approach.
    
- Ideal for CRUD dashboards or small applications.
    
- Less boilerplate compared to MVC.
    

### 4. **Blazor**

Build UI using C# instead of JavaScript.

Two hosting models:

- **Blazor Server:**  
    UI runs on server, updates via SignalR.
    
- **Blazor WebAssembly:**  
    Runs .NET in the browser using WebAssembly.
    

Useful for C#-focused teams.

---

## Prerequisites for Learning ASP.NET Core

- Solid understanding of C# (OOP, async/await, LINQ)
    
- Basic understanding of HTML & CSS
    
- Basic JavaScript knowledge
    
- Knowledge of REST, HTTP methods, status codes
    
- Familiarity with SQL or a database
    

---

## Real-World Summary

ASP.NET Core is:

> “A fast, modular, cloud-ready, cross-platform web framework where developers fully control how requests are processed. It supports multiple development models and runs efficiently on any modern infrastructure.”

# ASP.NET Web Forms vs ASP.NET MVC vs ASP.NET Core

---

## Summary

ASP.NET Core offers better performance, cloud-friendliness, and cross-platform support compared to ASP.NET Web Forms and ASP.NET MVC.

---

## Detailed Comparison

### ⚡️ ASP.NET Web Forms

**Strengths:**

- Rapid development using drag‑and‑drop controls.
    
- Event-driven model felt familiar to Windows Forms developers.
    
- ViewState simplified state management (for older era requirements).
    

**Major Drawbacks (Practical & Technical):**

- **Very poor performance** due to heavy ViewState and server controls.
    
- **Bloated page life cycle** making debugging and customization difficult.
    
- **Tightly coupled UI + logic**, which makes testability extremely low.
    
- **Not suitable for modern web standards** (SPA, APIs, microservices).
    
- **Requires Windows + IIS only**, no cross-platform hosting.
    
- Essentially **deprecated** for modern development.
    

---

### 💡 ASP.NET MVC

**Strengths:**

- Excellent **separation of concerns** (Model–View–Controller).
    
- Much **cleaner, lighter, and more testable** than Web Forms.
    
- Great for server-rendered applications.
    
- Supported Razor, routing, filters, strongly typed views.
    

**Drawbacks / Limitations:**

- **Not cross-platform** — works only on .NET Framework.
    
- Still tied to **Windows + IIS** deployment.
    
- No built-in dependency injection (added manually).
    
- Slower improvement lifecycle because .NET Framework is frozen.
    
- Lacks modern performance optimizations introduced in .NET Core.
    
- Being replaced by **ASP.NET Core MVC**, which is the evolved version.
    

---

### 🌐 ASP.NET Core

**Strengths:**

- **Cross-platform** — works on Windows, Linux, macOS.
    
- **Extremely high performance** using Kestrel and minimal overhead.
    
- **Cloud-ready**: configuration system, logging, DI, microservice support.
    
- **Open-source & actively developed** by Microsoft + community.
    
- **First-class Azure integration**.
    
- Built-in **Dependency Injection**.
    
- Unified framework for MVC, API, Razor Pages, Blazor.
    
- Ideal for modern architectures: microservices, containers, Kubernetes.
    

**Drawbacks (Minor but real-world):**

- Learning curve for those coming from Web Forms.
    
- Must understand DI, middleware, and modern patterns.
    
- Migration from .NET Framework apps is not always straightforward.
    

---

# 🔥 Additional Deep-Dive: Real-World Explanations, Scenarios, and Examples

Below is a **much more detailed, practical, Obsidian-quality expansion** of ASP.NET Web Forms vs MVC vs Core — written like someone who deeply understands the evolution of .NET, not surface definitions.

---

## 🧠 1. The Philosophical Difference Between the Three

### **ASP.NET Web Forms — "Old Web in a Windows Desktop Mindset"**

Web Forms tried to bring **WinForms-style development** to the web.

- Drag-and-drop controls.
    
- Events like `Button.Click` handled on server.
    
- ViewState pretending the web is stateful.
    

➡️ This was great for beginners in the early 2000s, but fundamentally **opposed how the web actually works** (stateless, request/response, lightweight).

---

### **ASP.NET MVC — "Clean, HTTP-focused Web Development"**

MVC embraced **the real nature of the web**:

- HTTP verbs
    
- URLs & routing
    
- Clean separation (Model, View, Controller)
    
- No ViewState
    
- Razor pages instead of server controls
    

➡️ This was the first time .NET developers could build modern, lightweight, testable web apps.

But it still had a major problem:

- It ran only on the old .NET Framework → Windows-only.
    

---

### **ASP.NET Core — "Rewritten, Modern, Cloud-Ready, Cross-Platform .NET"**

ASP.NET Core was a complete reboot:

- New runtime (.NET Core → now .NET 8+)
    
- New server (Kestrel)
    
- New modular pipeline (Middleware)
    
- Cross-platform
    
- High performance
    
- Dependency Injection built-in
    

➡️ This wasn’t an evolution — it was a **restart**, built for the next 20+ years.

---

## 🏗 2. Real-World Architecture Comparison

### **Web Forms Architecture**

```
Browser → IIS → Web Forms Page (.aspx) → Page Life Cycle → ViewState → Response
```

- Very heavy.
    
- No clear separation.
    
- Hard to test.
    

**Example problem:**  
If you drag a GridView with AutoPostBack, a simple row click sends a full form with huge ViewState → **slow page**.

---

### **ASP.NET MVC Architecture**

```
Browser → Routing → Controller → Model → View (Razor)
```

- Lightweight.
    
- No ViewState.
    
- Highly testable.
    

**Example:**  
A REST API hitting `/products/23` goes straight to a controller action → predictable, testable.

---

### **ASP.NET Core Architecture**

```
Browser → Kestrel → Middleware Pipeline → Endpoint Routing → Controller / Razor / Minimal API
```

- Very fast.
    
- Modular.
    
- Cloud friendly.
    

**What makes it powerful?**  
You can **insert middleware** anywhere:

- Authentication
    
- Logging
    
- Exception handling
    
- Custom logic
    
- Caching
    

This is impossible in Web Forms and limited in old MVC.

---

## ⚙️ 3. Request Lifecycle Differences (Very Important for Interviews)

### **Web Forms (Page Life Cycle)**

Too many stages:

```
Init → Load → Validation → PostBack → Rendering → Unload
```

Hard to debug. Hard to reason about.

---

### **MVC (Execution Pipeline)**

```
Routing → Controller → Action → Result (View/JSON/etc)
```

Simple, predictable.

---

### **Core (Middleware Pipeline)**

```
UseMiddleware() → MapControllers() → Execute Action
```

You can even build an entire app **without controllers** using Minimal APIs.

---

## 🚀 4. Realistic Modern Use-Cases

### ❌ **Where Web Forms completely fails**

- High-traffic websites
    
- Lightweight REST APIs
    
- Mobile-ready backends
    
- Docker/Kubernetes
    
- Cross-platform hosting
    
- Microservices
    
- Modern frontend like Angular/React
    

Basically **anything beyond 2010-style development**.

---

### ⚠️ **Where MVC still works, but is outdated**

Great for:

- Legacy apps still on .NET Framework
    
- Large Razor-based portals
    

Weak because:

- Not cross-platform
    
- No future updates
    
- Dependent on old IIS pipeline
    

---

### ✔️ **Where ASP.NET Core shines**

- Enterprise-scale APIs
    
- Microservices with Dapper/EF Core
    
- High-performance backend (millions of requests)
    
- Dockerized deployments
    
- Clean Architecture designs
    
- Cross-platform dev teams
    
- Cloud-native apps on Azure, AWS, GCP
    

It fits **every modern development style**, from monoliths to microservices.

---

## 📉 5. Deeper Drawbacks (the real ones, not the generic ones)

### **Web Forms — Deeper Issues**

- Fake statefulness → unnecessary bloat
    
- Hidden magic behind PostBack → debugging nightmare
    
- No real control of HTML output → bad for SEO & performance
    
- ViewState increases page size drastically
    
- Not mobile-friendly
    
- Hard to version control due to designer files
    

---

### **MVC — Deeper Issues**

- Still tied to System.Web — the biggest bottleneck
    
- IIS dependency → limited DevOps
    
- Steep learning curve without Core-level DI/middleware
    
- No first-class SPA or real-time support
    
- Razor was tightly tied to old runtime
    

---

### **Core — Real Drawbacks**

(Core has few, but honest ones.)

- More concepts to learn (DI, middleware, configuration)
    
- Migration from .NET Framework is not simple
    
- Frequent changes require continuous learning
    
- Self-hosted Kestrel requires ops knowledge
    

But these are not true _limitations_—just modern requirements.

---

## 🏁 6. The Ultimate Summary

### **Web Forms → Past**

Based on an incorrect assumption: "Web should work like Windows Forms".

### **MVC → Transition**

A correction to Web Forms, aligned with the real web.

### **ASP.NET Core → Future**

A from-scratch, high-performance, cross-platform, cloud-ready framework designed for modern development.

---














	ASP .NET Core | Asp.Net Core Projects | Bootcamp | Advanced | Interview Questions | Web API | MVC | SOLID Principles
	
**Custom Model Binder**

![Custom Model binder](./images/Pasted%20image%2020250829000130.png)

### 🔹 What is a Custom Model Binder in .NET?

A **Model Binder** in ASP.NET Core (or older ASP.NET MVC) is responsible for **mapping HTTP request data (query string, form data, route values, headers, body, etc.) to action method parameters or model objects**.

A **Custom Model Binder** is when you **create your own binding logic** instead of using the default binder.  
It allows you to control **how data is read, transformed, and populated** into your model or action parameter.

---

### 🔹 Why is it used?

You use a custom model binder when:

1. **Custom Input Format**
    
    - Request data isn’t in a standard format (like JSON, form-data).
        
    - Example: A comma-separated string `"1,2,3"` in the query should be bound to a `List<int>`.
        
2. **Complex Object Mapping**
    
    - If a model requires extra logic to build, e.g., combining values from **headers + query + body**.
        
3. **Data Transformation / Preprocessing**
    
    - Example: Automatically converting Unix timestamps to `DateTime`.
        
    - Or trimming/normalizing strings before binding them.
        
4. **Security / Validation**
    
    - Example: Automatically decrypting an encrypted ID passed in query parameters.

![project structure](./images/Pasted%20image%2020250829000249.png)

```
using CustomModelBinders.CustomModelBinders;
using CustomModelBinders.Models;
using Microsoft.AspNetCore.Mvc;


public class Home : Controller

{
    [HttpPost("register")]
    public IActionResult Index([ModelBinder(BinderType = typeof(PersonModelBinder))]Person person)
    {
        if (!ModelState.IsValid)
        {
            // Get error messages from Model state and return as response
            string errors = string.Join("\n", ModelState.Values.SelectMany(
                value => value.Errors
            ).Select(
                err => err.ErrorMessage
            ));
            return BadRequest(errors);
        }
        return Content($"{person}");
    }
}

HomeController.cs
```

```
using CustomModelBinders.Models;

using Microsoft.AspNetCore.Mvc.ModelBinding;

namespace CustomModelBinders.CustomModelBinders{

    public class PersonModelBinder : IModelBinder
    {
        public Task BindModelAsync(ModelBindingContext bindingContext)
        {
            // FirstName and LastName property from the request body

            var FNameBody = bindingContext.ValueProvider.GetValue("FirstName");

            var LNameBody = bindingContext.ValueProvider.GetValue("LastName");

            var EmailBody = bindingContext.ValueProvider.GetValue("Email");

            var PhoneBody = bindingContext.ValueProvider.GetValue("Phone");

            var PasswordBody = bindingContext.ValueProvider.GetValue("Password");

            var ConfirmPasswordBody = bindingContext.ValueProvider.GetValue("ConfirmPassword");

            var PriceBody = bindingContext.ValueProvider.GetValue("Price");

  

            Person person = new Person();

            if (FNameBody.Length > 0)
            {

                person.PersonName = FNameBody.FirstValue;

                if (LNameBody.Length > 0)
                {
                    person.PersonName += " " + LNameBody.FirstValue;
                }

            }

            if (EmailBody.Length > 0)
            {
                person.Email = EmailBody.FirstValue;
            }

            if (PhoneBody.Length > 0)
            {
                person.Phone = PhoneBody.FirstValue;
            }

            if (PasswordBody.Length > 0)
            {
                person.Password = PasswordBody.FirstValue;
            }

            if (ConfirmPasswordBody.Length > 0)
            {
                person.ConfirmPassword = ConfirmPasswordBody.FirstValue;
            }

            if (PriceBody.Length > 0 && double.TryParse(PriceBody.FirstValue, out var price))
            {
                person.Price = price;
            }

            bindingContext.Result = ModelBindingResult.Success(person);
            return Task.CompletedTask;
        }
    }
}

PersonModelBinder.cs
```

```
using System.ComponentModel.DataAnnotations;

namespace CustomModelBinders.Models
{
    public class Person

    {
        // [Required(ErrorMessage = "Please provide this field to continue")] // Attribute and all the attributes are classes

            public string? PersonName { get; set; }

            [EmailAddress]

            public string? Email { get; set; }

            public string? Phone { get; set; }

            public string? Password { get; set; }

            public string? ConfirmPassword { get; set; }

            public double? Price { get; set; }

            public string? FirstName { get; set; }

            public string? LastName { get; set; }

        public override string ToString()

        {
            return $"PersonName : {PersonName} , Email : {Email} , Phone :{Phone} , Password : {Password} , ConfirmPassword : {ConfirmPassword} , Price : {Price}";

        }
    }
}

Person.cs
```

```
var builder = WebApplication.CreateBuilder(args);

// Add services to the container.

// Learn more about configuring OpenAPI at https://aka.ms/aspnet/openapi

builder.Services.AddOpenApi();

builder.Services.AddControllers();

builder.Services.AddSwaggerGen();  

var app = builder.Build();

// Configure the HTTP request pipeline.

if (app.Environment.IsDevelopment())

{
    app.UseSwagger();
    app.UseSwaggerUI();      
}

app.MapControllers();
app.Run();

Program.cs
```

**Model Binder Providers**

 **1. What is a Model Binder Provider?**

   A **model binder provider** tells ASP.NET Core **which binder to use for a specific type**.

- If you want your custom binder to be applied **automatically everywhere** a certain model type is used, you register it globally via a **custom model binder provider**.

![custom model binder provider](./images/Pasted%20image%2020250829002853.png)
![Description](./images/Pasted%20image%2020250829232023.png)

```
using CustomModelBinders.CustomModelBinders;

using CustomModelBinders.Models;

using Microsoft.AspNetCore.Mvc.ModelBinding;

using Microsoft.AspNetCore.Mvc.ModelBinding.Binders;

  

public class PersonModelBinderProvider : IModelBinderProvider

{

    public IModelBinder? GetBinder(ModelBinderProviderContext context)

    {

        if (context.Metadata.ModelType == typeof(Person))

        {

            return new BinderTypeModelBinder(typeof(PersonModelBinder));

        }

        return null;

    }

}

CustomModelBinders / PersonModelBinderProvider.cs
```

```
using CustomModelBinders.Models;

using Microsoft.AspNetCore.Mvc.ModelBinding;

  

namespace CustomModelBinders.CustomModelBinders{

    public class PersonModelBinder : IModelBinder

    {

        public Task BindModelAsync(ModelBindingContext bindingContext)

        {

            // FirstName and LastName property from the request body

            var FNameBody = bindingContext.ValueProvider.GetValue("FirstName");

            var LNameBody = bindingContext.ValueProvider.GetValue("LastName");

            var EmailBody = bindingContext.ValueProvider.GetValue("Email");

            var PhoneBody = bindingContext.ValueProvider.GetValue("Phone");

            var PasswordBody = bindingContext.ValueProvider.GetValue("Password");

            var ConfirmPasswordBody = bindingContext.ValueProvider.GetValue("ConfirmPassword");

            var PriceBody = bindingContext.ValueProvider.GetValue("Price");

  

            Person person = new Person();

            if (FNameBody.Length > 0)

            {

                person.PersonName = FNameBody.FirstValue;

                if (LNameBody.Length > 0)

                {

                    person.PersonName += " " + LNameBody.FirstValue;

                }

            }

            if (EmailBody.Length > 0)

            {

                person.Email = EmailBody.FirstValue;

            }

            if (PhoneBody.Length > 0)

            {

                person.Phone = PhoneBody.FirstValue;

            }

            if (PasswordBody.Length > 0)

            {

                person.Password = PasswordBody.FirstValue;

            }

            if (ConfirmPasswordBody.Length > 0)

            {

                person.ConfirmPassword = ConfirmPasswordBody.FirstValue;

            }

            if (PriceBody.Length > 0 && double.TryParse(PriceBody.FirstValue, out var price))

            {

                person.Price = price;

            }

            bindingContext.Result = ModelBindingResult.Success(person);

            return Task.CompletedTask;

        }

    }

}

CustomModelBinders / PersonModelBinder.cs
```

```
public class Home : Controller

{

    [HttpPost("register")]

    // public IActionResult Index([ModelBinder(BinderType = typeof(PersonModelBinder))]Person person)  
    // Instead of this , the following way should be used

    public IActionResult Index(Person person)

    {

        if (!ModelState.IsValid)

        {

            // Get error messages from Model state and return as response

            string errors = string.Join("\n", ModelState.Values.SelectMany(

                value => value.Errors

            ).Select(

                err => err.ErrorMessage

            ));

            return BadRequest(errors);

        }

        return Content($"{person}");

    }

}

Controllers/ HomeController.cs
```

```
var builder = WebApplication.CreateBuilder(args);
// Add services to the container.
// Learn more about configuring OpenAPI at https://aka.ms/aspnet/openapi

builder.Services.AddOpenApi();

builder.Services.AddControllers(

    options => {
        options.ModelBinderProviders.Insert(0, new PersonModelBinderProvider());
        }
);

builder.Services.AddSwaggerGen();  

var app = builder.Build();

// Configure the HTTP request pipeline.

if (app.Environment.IsDevelopment())

{
    app.UseSwagger();
    app.UseSwaggerUI();      
}

app.MapControllers();
app.Run();


Program.cs
```
### 🔹 What is this?

The code you shared defines a **Custom Model Binder Provider** in ASP.NET Core.

- **Model Binding** in ASP.NET Core = process of taking HTTP request data (route values, query string, form values, JSON body, etc.) and mapping it to your action method parameters or models.
    
- By default, ASP.NET Core has built-in binders (for primitive types, complex types, collections, etc.).
    
- Sometimes, the default binders are **not enough** (e.g., you want to combine two request fields into one property, parse custom formats, etc.).
    
- That’s when you create a **Custom Model Binder** (your `PersonModelBinder`) and a **Model Binder Provider** (this class).
    

---

### 🔹 What does `PersonModelBinderProvider` do?

- The framework doesn’t know about your custom binder automatically.
    
- `PersonModelBinderProvider` **registers** your custom binder in the ASP.NET Core model binding pipeline.
    
- It checks:
    
    `if (context.Metadata.ModelType == typeof(Person))`
    
    → If the action parameter type is `Person`, then it tells ASP.NET Core:  
    **“Hey, use my custom `PersonModelBinder` for this type instead of the default binder.”**
    

---

### 🔹 Why is this important?

Without this provider:

- You would have to decorate your model or action parameter with `[ModelBinder(typeof(PersonModelBinder))]` **everywhere** you use it.
    
- With this provider:
    
    - It’s **global** → whenever a controller action expects a `Person`, ASP.NET Core will automatically use your custom binder.
        
    - This reduces repetition and enforces consistency.

**Collection Binding**

-  In **ASP.NET Core MVC / Web API**, **collection binding** means that the model binder can automatically bind a collection type (like `List<T>`, `IEnumerable<T>`, `T[]`, `Dictionary<K,V>`) from the **incoming request data** (query string, form data, route values, or JSON body) to your controller action parameters or model properties.

![Collection Binding](./images/Pasted%20image%2020250901234327.png)
```
using Microsoft.AspNetCore.Mvc;

  

public class Home : Controller

{

    [HttpPost("register")]

    public async Task<IActionResult> Register(Person person)

    {

        return Ok("Received person Details");

    }

}

Controllers / HomeController.cs

```

```
public class Person

{

    public string Name { get; set; }

    public int Age { get; set; }

    public List<string?> Skills { get; set; } = new List<string>();

}

Models / Person.cs
```

```
var builder = WebApplication.CreateBuilder(args);

  

builder.Services.AddOpenApi();

builder.Services.AddControllers();

builder.Services.AddSwaggerGen();

var app = builder.Build();

  

if (app.Environment.IsDevelopment())

{

    app.UseSwagger();

    app.UseSwaggerUI();

}

app.MapControllers();

app.Run();


Program.cs
```


**FromHeader**

![FromHeader](./images/Pasted%20image%2020250901235407.png)
```
using Microsoft.AspNetCore.Mvc;

  

public class Home : Controller

{

    [HttpPost("register")]

    public async Task<IActionResult> Register(Person person,[FromHeader(Name="Name")]string UserName)

    {

        return Ok($"Received person Details of {UserName}");

    }

}

Controllers/ HomeController.cs
```

```
public class Person

{

    public string Name { get; set; }

    public int Age { get; set; }

    public List<string?> Skills { get; set; } = new List<string>();

}

Models/ Person.cs
```

```
var builder = WebApplication.CreateBuilder(args);

  

builder.Services.AddOpenApi();

builder.Services.AddControllers();

builder.Services.AddSwaggerGen();

var app = builder.Build();

  

if (app.Environment.IsDevelopment())

{

    app.UseSwagger();

    app.UseSwaggerUI();

}

app.MapControllers();

app.Run();

Program.cs
```

FromBody 

![FromBody](./images/Pasted%20image%2020250908231041.png)
```
using FromBody.Models;

using Microsoft.AspNetCore.Mvc;

  

public class HomeController : Controller

{

    [HttpPost("register")]

    public async Task<IActionResult> RegisterUser(Person person)

    {

        return Ok("Success");

    }

}

Controllers / HomeController.cs
```

```
using System.ComponentModel.DataAnnotations;

  

namespace FromBody.Models

{

    public class Person

    {

        [Required(ErrorMessage = "Please provide this field to continue")] // Attribute and all the attributes are classes

        public string? PersonName { get; set; }

        [EmailAddress]

        public string? Email { get; set; }

        public string? Phone { get; set; }

        public string? Password { get; set; }

        public string? ConfirmPassword { get; set; }

        public double? Price { get; set; }

  

        public override string ToString()

        {

            return $"PersonName : {PersonName} , Email : {Email} , Phone :{Phone} , Password : {Password} , ConfirmPassword : {ConfirmPassword} , Price : {Price}";

        }

    }

}

Models / Person.cs
```

```
var builder = WebApplication.CreateBuilder(args);

  

builder.Services.AddControllers();

  

builder.Services.AddEndpointsApiExplorer();

builder.Services.AddSwaggerGen();

var app = builder.Build();

  

if (app.Environment.IsDevelopment())

{

    app.UseSwagger();

    app.UseSwaggerUI();

}

  

app.MapControllers();

app.Run();


Program.cs
```
![FromBody](./images/Pasted%20image%2020250908232015.png)
```
using FromBody.Models;

using Microsoft.AspNetCore.Mvc;

  

public class HomeController : Controller

{

    [HttpPost("register")]

    public async Task<IActionResult> RegisterUser([FromBody]Person person)

    {

        return Ok("Success");

    }
}

Contollers / HomeController.cs
```

 **`[FromBody]` tells ASP.NET Core “deserialize the JSON request body into this parameter.” Without it, ASP.NET Core looks in query string/route values, leaving body values as null.**

**Input formatters**
  Internal classes in Asp.Net core used to transform the request body into model object . 
  ![Input formatters](./images/Pasted%20image%2020250910222813.png)
  If the input contains XML then XMLserializerInputFormatter will be enabled automatically  , reads the XML data and converts it into model object automatically. 

```
var builder = WebApplication.CreateBuilder(args);

builder.Services.AddControllers().AddXmlSerializerFormatters();

Program.cs
```

  ![XML](./images/Pasted%20image%2020250915223052.png)

**MVC**
 ![Overview](./images/Pasted%20image%2020250916230307.png)
 Here the controller can invoke anything , 
 1. Controller can invoke the model, Controller can invoke the view 
 2.  The view can invoke the model . 
 ![Overview](./images/Pasted%20image%2020250916230630.png)
 