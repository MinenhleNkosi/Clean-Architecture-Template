 # ASP.NET Core WebApi - Clean Architecture 🚀

 [![Visual Studio](https://custom-icon-badges.demolab.com/badge/Visual%20Studio-5C2D91.svg?&logo=visual-studio&logoColor=white)](#)
[![.NET](https://img.shields.io/badge/.NET-512BD4?logo=dotnet&logoColor=fff)](#)
![.NET Core](https://img.shields.io/badge/.NET%209-8A2BE2)
[![NuGet](https://img.shields.io/badge/NuGet-004880?logo=nuget&logoColor=fff)](#)
[![C#](https://custom-icon-badges.demolab.com/badge/C%23-%23239120.svg?logo=cshrp&logoColor=white)](#)
[![Markdown](https://img.shields.io/badge/Markdown-%23000000.svg?logo=markdown&logoColor=white)](#)
[![Gmail](https://img.shields.io/badge/Gmail-D14836?logo=gmail&logoColor=white)](#)
[![Git](https://img.shields.io/badge/Git-F05032?logo=git&logoColor=fff)](#)
![GitHub stars](https://img.shields.io/github/stars/MinenhleNkosi/Clean-Architecture-Template)
[![LinkedIn](https://custom-icon-badges.demolab.com/badge/LinkedIn-0A66C2?logo=linkedin-white&logoColor=fff)](https://www.linkedin.com/in/mxolisi-nkosi-b47b57117/)

<br/>

An Implementation of Clean Architecture with ASP.NET Core 9.0 WebApi. With this Open-Source BoilerPlate Template, you will get access to the world of Loosely-Coupled and Inverted-Dependency Architecture in ASP.NET Core 9.0 WebApi with a lot of best practices.

Read the [Changelog file](https://github.com/MinenhleNkosi/Clean-Architecture-Template/blob/main/CHANGELOG.md) to see the new changes.


### 0.0.1 RC is available now!

This is the first pre-release version of the `fullstackmastery .NET WebAPI Boilerplate` package. Newer versions will be available on a weekly basis with newer updates and patches.

### Clone the Repository.

1. Clone this Repository and Extract it to a Folder.
3. Change the Connection Strings for the Application and Identity in the WebApi/appsettings.json - (WebApi Project)
2. Run the following commands on Powershell in the WebApi Projecct's Directory.
- dotnet restore
- dotnet ef database update -Context ApplicationDbContext
- dotnet ef database update -Context IdentityContext
- dotnet run (OR) Run the Solution using Visual Studio 2019

Say [Hi on LinkedIn!](https://www.linkedin.com/in/mxolisi-nkosi-b47b57117/)

### How to use SQL Server or PostgreSQL as your Data Provider
The Project currently uses MSSQL as the default Data Provider. If you are more comfortable with MySQL or PostgreSQL, here is how to migrate to them easily.


1. delete all existing file inside migrations folder on both project
   - {YourProjectName}.Infrastructure.Identity
   - {YourProjectName}.Infrastructure.Persistence

2. In `ServiceExtensions.cs` and `ServiceRegistration.cs` change from `options.UseSqlServer` to:
#### For MySql
`options.UseMySql`
#### For PostgreSQL
`options.UseNpgsql`

3. Add NuGet packages to both projects (Infrastructure.Identity and Infrastructure.Persistence):
#### For MySql:
run `dotnet add package Pomelo.EntityFrameworkCore.MySql --version 3.1.2` (remember to do this on both projects)
#### For PostgreSQL:
run 
```cli
dotnet add package Npgsql.EntityFrameworkCore.PostgreSQL
dotnet add package Npgsql.EntityFrameworkCore.PostgreSQL.Design
```
(remember to do this on both projects)

4. on `IdentityContext.cs` comment `builder.HasDefaultSchema("Identity");` because ef doesn't support that on mysql

5. cd to `{YourProjectName}.Infrastructure.Identity` and run
   - `dotnet ef database update --startup-project ../{YourProjectName}.WebApi/{YourProjectName}.WebApi.csproj -c "IdentityContext"`
   - `dotnet ef migrations add Initial --startup-project ../{YourProjectName}.WebApi/{YourProjectName}.WebApi.csproj -c "IdentityContext"`

6. cd to `{YourProjectName}.Infrastructure.Persistence` and run
   - `dotnet ef database update --startup-project ../{YourProjectName}.WebApi/{YourProjectName}.WebApi.csproj -c "ApplicationDbContext"`
   - `dotnet ef migrations add Initial --startup-project ../{YourProjectName}.WebApi/{YourProjectName}.WebApi.csproj -c "ApplicationDbContext"`
   
The above guide (To use MySQL) was contributed by [geekz-reno](https://github.com/geekz-reno).

### Default Roles & Credentials 🔐
As soon you build and run your application, default users and roles get added to the database.

Default Roles are as follows.
- SuperAdmin
- Admin
- Moderator
- Basic

Here are the credentials for the default users.
- Email: superadmin@gmail.com  / Password: 123Pa$$word!
- Email: basic@gmail.com  / Password: 123Pa$$word!

You can use these default credentials to generate valid JWTokens at the ../api/account/authenticate endpoint.

## Purpose of this Project ✔️

Does it really make sense to Setup your ASP.NET Core Solution everytime you start a new WebApi Project ? Aren't we wasting quite a lot of time in doing this over and over gain?

This is the exact Problem that I intend to solve with this Full-Fledged ASP.NET Core 3.1 WebApi Solution Template, that also follows various principles of Clean Architecture.

The primary goal is to create a Full-Fledged implementation, that is well documented along with the steps taken to build this Solution from Scratch. This Solution Template will also be available within Visual Studio 2019 (by installing the required Nuget Package / Extension).
- Demonstrate Clean Monolith Architecture in ASP.NET Core 3.1 
- This is not a Proof of Concept
- Implementation that is ready for Production
- Integrate the most essential libraries and packages

## Give a Star ⭐️
If you found this Implementation helpful or used it in your Projects, do give it a star. Thanks!
Or, If you are feeling really generous, [Support the Project with a small contribution!](https://www.buymeacoffee.com/codewithmukesh)

## Technologies 👩🏿‍💻💻🧑🏿‍💻
- ASP.NET Core 9.0 WebApi
- REST Standards
- .NET Core 9.0

## Features
- [x] Onion Architecture
- [x] CQRS with MediatR Library
- [x] Entity Framework Core - Code First
- [x] Repository Pattern - Generic
- [x] MediatR Pipeline Logging & Validation
- [x] Serilog
- [x] Swagger UI
- [x] Response Wrappers
- [x] Healthchecks
- [x] Pagination
- [ ] In-Memory Caching
- [ ] Redis Caching
- [x] In-Memory Database
- [x] Microsoft Identity with JWT Authentication
- [x] Role based Authorization
- [x] Identity Seeding
- [x] Database Seeding
- [x] Custom Exception Handling Middlewares
- [x] API Versioning
- [x] Fluent Validation
- [x] Automapper
- [x] SMTP / Mailkit / Sendgrid Email Service
- [x] Complete User Management Module (Register / Generate Token / Forgot Password / Confirmation Mail)
- [x] User Auditing

## Prerequisites
- Visual Studio 2019 Community and above
- .NET Core 8.0 SDK and above
- Basic Understanding of Architectures and Clean Code Principles
- I Recommend that you read [Onion Architecture In ASP.NET Core With CQRS – Detailed](https://www.codewithmukesh.com/blog/onion-architecture-in-aspnet-core/) article to understand this implementation much better. This project is just an Advanced Version of the mentioned article.

## Getting Started

## Changelog
Every changes / additions / deletions will be recorded in the [Changelog file](https://github.com/MinenhleNkosi/Clean-Architecture-Template/blob/main/CHANGELOG.md).

## Questions? Bugs? Suggestions for Improvement?
[Raise a Bug or Feature Request](https://github.com/MinenhleNkosi/Clean-Architecture-Template/issues/new/choose). Always happy to help.

## Share it!
I have personally not come across a clean implementation on a WebAPI, which is the reason that I started building this up. There are quite a lot of improvements and fixes along the way from the day I started out. Thanks to the community for the support and suggestions.
Please share this Repository within your developer community, if you think that this would a difference! Thanks.

## About the Author
### Minenhle Nkosi
- Linkedin - [Minenhle Nkosi](https://www.linkedin.com/in/mxolisi-nkosi-b47b57117/)

## Licensing
This Project is licensed with the [MIT License](https://github.com/MinenhleNkosi/Clean-Architecture-Template/blob/main/LICENSE).
