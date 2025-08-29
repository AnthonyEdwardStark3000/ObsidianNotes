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
![Description](./Pasted%20image%2020250829232023.png)

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