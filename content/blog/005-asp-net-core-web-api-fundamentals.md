---
title: "ASP.NET Core 6 Web API Fundamentals"
author: "@christo"
dates:
  published: "2023-08-06"
description: Covering the fundamentals of creating a Web API using ASP.NET Core and EF Core
---

# ASP.NET Core 6 Web API Fundamentals

## TL;DR
You know the drill by now...

- The source code for this app can be found on my <a href="https://github.com/christo-froneman/AspNetCore6WebAPIFundamentals" target="_blank">Github Repository</a>.
- This app was built by following along with Kevin Dockx's Pluralsight course with the same name: ASP.NET Core 6 Web API Fundamentals.

## Fundamentals
Each of the following sections can be expanded / collapsed.

<details>
<summary><b>Getting Acquainted with ASP.NET Core</b></summary>

- ASP.NET Core is a cross‑platform, high performance, open source framework for building modern cloud‑enabled internet connected apps. 
- The Program class is the starting point of our application, or to be more exact, the main method of that class. We don't see that method, but the compiler generates it behind the scenes. 
- It's that generated main method that's responsible for configuring and running the application. In our case, we'll be running a web application, our API, and that needs to be hosted. For that, a web application builder can be used. 
- The services collection on that builder is what we can add services to while configuring them. This is the built‑in dependency injection container at work. So by adding services to it, you can inject them wherever we need them in our code. 

</details>

<br />

<details>
<summary><b>Creating the API and Returning Resources</b></summary>

- MVC pattern = model‑view‑controller. 
- The model handles the logic for our application data. 
- The view represents the parts that display data. In the case of an API, that's the data, typically in JSON format, returned from API calls. 
- And the controller handles the interaction between view and model. 
- This pattern leads to more reuse and better testability. 
- We worked with the GET method to return data from our API. It's routing that takes care of mapping a request URI to a method on our controller. 
- Next to GET, there is also POST for creating, PUT for updates, PATCH for partial updates, and DELETE for the deleting resources. 
- For APIs, attribute‑based routing is advised over convention‑based routing. 

</details>

<br />

<details>
<summary><b>Manipulating Resources and Validating Input</b></summary>

- Use POST to create a resource. 
- When the resource has successfully been created, 201 status code response is what we should return. 
- Submit a request body to our API. The format of it is designated by the Content‑Type header. 
- When talking about input, we're also talking about validation. 
  - Use data annotations on our DTO classes.
  - Check for these using the ModelState. That's a dictionary containing both the state of the model and model binding validation. 
  - Whenever the request comes in, the annotations applied to the model are checked. 
  - If one of them doesn't check out, the ModelState's IsValid property will be false. 
  - Thanks to the ApiController attribute, a Bad Request will automatically be returned in such a case. 
- Updating a resource: PUT is for full updates, while PATCH is for partial updates. 
- Partial updates are often preferred, but they require a way to send through a list of changes. 
  - That's where the JSON Patch standard comes into play. 
  - It's essentially a set of rules for expressing a sequence of operations to apply to the JSON representation of the resource we want to update. 
- After a successful update, a NoContent status code or, as an alternative, a 200 OK status code should be sent back with a response. 
- DELETE is for deleting resources, and that warrants a 204 status code in the response. 

</details>

<br />

<details>
<summary><b>Working with Services and Dependency Injection</b></summary>

- ASP.NET Core has its own built‑in dependency injection system. 
  - This is a specialization of the inversion of control pattern. 
  - It uses an object, the container, to initialize objects and provide required dependencies to the object. 
  - This principle has looser coupling as an advantage, which leads to less possible required code changes and better testability. 
- We learned how to use this by implementing logging functionality. The logger is a built‑in service, but we also created a custom service. 
- These are registered on the service collection, which is our container, in the Program class. 
- There are three different lifetimes for services. 
  - Transient lifetime services are created each time they are requested. This lifetime works best for lightweight, stateless services. 
  - Scoped lifetime services are created once per request. 
  - And singleton lifetime services are created the first time they are requested. Every subsequent request will use the same instance. 
- After having registered the service, we can use dependency injection to inject it into the class requiring an instance of it, and that led us to working with configuration files to store the mail addresses in. 
- We can inject an IConfiguration object anywhere we need access to configuration values.
- We can scope configuration files to environments by adding the environment name as part of the file name. 

</details>

<br />

<details>
<summary><b>Getting Acquainted with Entity Framework Core</b></summary>

- Entity Framework Core is ORM, or object‑relational mapper. 
- Object‑relational mapping is a technique that lets you query and manipulate data from a database using an object‑oriented paradigm. 
- EF Core is the preferred ORM to use for .NET. 
- We created entity classes first. As we learned, the DTOs or the outer‑facing model is different from the entities or the entity model. Not all fields, like computed fields, are stored in the database, and the data we want to offer through an API is often shaped differently than how it's stored in the underlying data store, so it's important to make that distinction. 
- We can rely on conventions or use annotations on those to define things like primary and foreign keys, required fields, and so on. 
  - Personally, I prefer being explicit because I believe it makes the code more readable, so I tend not to rely too much on the conventions. 
- These are then registered as DbSets, on the DbContext. That context represents a session with the database, and it can be used to query and save instances of our entities. 
- From that moment on, we could access our entities through LINQ. 
- Another important concept is migrations. Just as our code evolves, so does the database. New tables might be added after a while, existing tables might be dropped or altered. Migrations allow us to provide code to change the database from one version to another. 
- Then we looked into an option to seed the database, which means providing it with data to start with. We can do that through the HasData method when configuring the model. 
  - Don't forget to add a migration afterward. 
- And lastly, we got rid of our hard‑coded connection string. We learned how to store it in the appsettings file for the development environment, but used a safer storage option for the production environment, an environment variable. 

</details>

<br />

<details>
<summary><b>Using Entity Framework Core in Your Controllers</b></summary>

- The repository pattern is an abstraction that reduces complexity and aims to make the code, save for the repository implementation, persistence‑ignorant. 
- In fact, the best illustration of this was that we would have had a lot less work in switching out the in-memory store for our database if we had used the repository in the beginning of the course. 
- For I/O operations, writing async code ensures threads can be freed up faster, resulting in improved scalability for our API. 
- One part of the code that was quite error‑prone was the mapping code between DTOs and entities. We improved our code base by using AutoMapper for this. 

</details>

<br />

<details>
<summary><b>Searching, Filtering, and Paging Resources</b></summary>

- Filtering allows you to be precise by adding filters until you get exactly the result you want. 
- Searching allows you to go wider. It's used when you don't exactly know which items will be in the collection. 
  - We don't pass in a field name that should match. We pass in a value to search for, and it's up to the API to decide which fields shall be searched for that value. 
  - Often, that's done with full‑text search, but the implementation is up to the API. 
- We implemented both, and along the way, we learned about deferred execution with LINQ 
  - The principle that allows query execution to occur sometime after the query is constructed. 
  - It's thanks to that principle that we could build our Entity Framework Core query, taking filter and search parameters into account without it hitting the database before the query was fully constructed. 
- Paging can be very good for performance if done correctly. We should pass the page size and page number via the query string. 
  - Think about limiting the page size that's passed in to avoid consumers requesting 1 page with 100,000 records. In other words, make sure to provide default values for page size and page number. 
  - When paging, it's important to send page size and page number all the way through to the underlying data store. Like that, only the requested page is returned from the store. 
  - Thanks to deferred execution, we can use Skip and Take statements for that. 
  - Page by default to avoid performance issues when the collection grows. 
  - And lastly, it's important to return pagination metadata so the consumer knows how many pages are left, for example. That metadata belongs in a custom header, for example an X‑Pagination header.

</details>

<br />

<details>
<summary><b>Securing Your API</b></summary>

- There are different ways to secure you API. 
  - An example of a bad implementation would be sending over a username and password on each request.
  - A better approach would be to use token‑based security.
  - Best practice is token‑based security implemented by following the OAuth2 and OpenID Connect standards. 
- We implemented token‑based security. A typical approach is to create an endpoint at level of your API for that that accepts your username and password. 
  - If those check out, a token can be returned from that call. 
  - That token is requested by and returned to a client app. It is then sent as a bearer token on each request to the API, and at that level, it's validated. If that checks out, access is granted. 
  - From that moment on, we also get access to the claims from the token via the user object. 
  - We can use those in a controller action. 
  - Authorization policies improve on that. They allow us to check whether a request will be allowed before even entering a controller action, thus allowing us to create a full‑fledged authorization layer. 
  - We learned how to implement a basic policy. 
- Lastly, we learned that what we just did is just the tip of the iceberg. Security is a huge topic that evolves fast. You can improve on the token‑based security approach by implementing it using standards like OAuth2 and OpenID Connect.

</details>

<br />

<details>
<summary><b>Versioning and Documenting your API</b></summary>

- As APIs evolve over time, different versions of that API start to coexist because you don't want to break existing consumers that might use an older version. 
- That leads to versioning strategies for APIs. Commonly used are URI versioning via URI segments or query string, custom headers, or version media types. 
- We learned how to implement it using Microsoft's default approach via the Microsoft.AspNetCore.Mvc.Versioning package. 
- Documenting your API is important, not only for public APIs, but also for internal APIs as other teams in your company will want to know how to integrate with your API. 
- It all starts from an OpenAPI specification. That's a standardized description of your API. From that specification, documentation UI, a web app, for example, can be generated. 
- That's what Swagger UI does, and that's what we see when we navigate to the Swagger endpoint. 
- In the default ASP.NET Core API template, this is implemented via Swashbuckle.AspNetCore. 
- We learned how to improve the default documentation and that data annotations are taken into account, how to incorporate XML comments and how to improve the documentation with information regarding the returned status codes and authentication. 
- The more specific you can be, the better. After all, this documentation is the first thing people who want to integrate with your API will see.

</details>