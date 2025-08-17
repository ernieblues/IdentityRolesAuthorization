# Identity Roles Authorization  
This repository demonstrates how to add **custom roles** to ASP.NET Core Identity in an **MVC application**, with each stage captured in a **clearly defined commit**.
The progression can be followed step by step, without having to wade through the **extensive Microsoft Learn documentation**.  

This project uses a **schedule model**, which demonstrates more than the basic *Contacts Example* in Microsoft Learn.
The schedule model demonstrates the implementation of **roles authorization within the MVC design pattern**, with its own **controller** and full set of scaffolded CRUD views.  

---

## Built With
- .NET 9.0
- ASP.NET Core MVC
- ASP.NET Core Identity
- Microsoft SQL Server Developer Edition

---

## Roadmap
This repository demonstrates Identity Authentication and custom Authorization Roles in five stages:

- **Commit 1 — ASP.NET Core MVC**
  - Visual Studio ASP.NET Core MVC project template
  - No Identity Authorization, no database, no roles

- **Commit 2 — Add Authorization - Individual Accounts**
  - Visual Studio ASP.NET Core MVC with Authorization project template
  - Includes registration, login, and logout pages
  - Authorization was added by recreating the project with the ‘Individual Accounts’ option enabled.  
  - Identity Authorization can be added to an existing project by following the steps in Microsoft Learn: 
    [Scaffold Identity in ASP.NET Core projects](https://learn.microsoft.com/en-us/aspnet/core/security/authentication/scaffold-identity?view=aspnetcore-8.0&tabs=visual-studio)
  - Comparing this commit to the previous one clearly shows the difference between creating a project with and without Identity Authorization.

- **Commit 3 — Identity Roles Authorization**
  - Identity Roles Authorization are added by implementing classes that inherit from the IdentityRole class.
  - Roles are not included in the project template, they must be added manually.
  - Microsoft Learn reference: [Identity model customization in ASP.NET Core](
    https://learn.microsoft.com/en-us/aspnet/core/security/authentication/customize-identity-model?view=aspnetcore-9.0)
  - Role types include:
    - Registered Users — Regular user with limited access to the application.
    - Managers — Can manage content, but not users or roles.
    - Administrators — Full access to the application, can manage users and roles.

- **Commit 4 — Authorization Handlers, Schedule Model, Seed Data**
  - Custom Authorization Handlers enforce business rules for role- and resource-based access.
  - A Schedule (employee work schedule) model is added to demonstrate role restrictions in practice.
  - Seed data initializes roles and default accounts (e.g., Registered Users, Managers, Administrators) to make testing easier.
  - Demonstrates the difference between role-based checks (User.IsInRole) and policy-based checks (Authorization Handlers).
  - Microsoft Learn reference: [Create an ASP.NET Core web app with user data protected by authorization](
    https://learn.microsoft.com/en-us/aspnet/core/security/authorization/secure-data?view=aspnetcore-9.0)

- **Commit 5 – Add scaffolded Schedule controller and CRUD views**  
  - Right-click the *Controllers* folder → **Add** → **New Scaffolded Item...**  
  - Choose *MVC Controller with views, using Entity Framework*.  
  - Select the `Schedule` model and `ApplicationDbContext`.  
  - Name the controller **SchedulesController**.  

  This generates the template controller and views (*Create, Index, Details, Edit, Delete*).  

- **Commit 6 — Custom Controller and CRUD with Authorization Roles**
  - Customized `SchedulesController.cs` to implement authorization roles.
  - Modified the *Create, Index, Details, Edit, and Delete* views (CRUD) for the Schedule model.
  - Added a **Calendar** view to display schedules.
  - User actions are restricted by role and by ownership of the resource.
  - Registered users can only manage their own schedules.
  - Managers and administrators can review and approve/reject schedules.
  - Demonstrates the complete flow of Identity + Roles + Authorization in a working ASP.NET Core MVC app.

---

## Getting Started
- Install **Visual Studio**
- Install **SQL Server Developer Edition**
- Install **SQL Server Management Studio (SSMS)**
- Rename `AspNetCoreMVC/appsettings.Development.json.example` to `appsettings.Development.json`
- Update the connection string in `appsettings.Development.json` to point to your SQL Server instance
- The application will automatically apply migrations at startup  
  - Alternatively, run `Update-Database` from the Package Manager Console to apply migrations manually
- Build and run

---

## Credits
- [Scaffold Identity in ASP.NET Core projects](
  https://learn.microsoft.com/en-us/aspnet/core/security/authentication/scaffold-identity?view=aspnetcore-8.0&tabs=visual-studio) — Microsoft Learn  
- [Identity model customization in ASP.NET Core](
  https://learn.microsoft.com/en-us/aspnet/core/security/authentication/customize-identity-model?view=aspnetcore-9.0) — Microsoft Learn  
- [Create an ASP.NET Core web app with user data protected by authorization](
  https://learn.microsoft.com/en-us/aspnet/core/security/authorization/secure-data?view=aspnetcore-9.0) — Microsoft Learn
- [Secure Data Samples Repository](
  https://github.com/dotnet/AspNetCore.Docs/tree/main/aspnetcore/security/authorization/secure-data/samples) — Microsoft dotnet/AspNetCore.Docs GitHub repository

---

## License
This repository includes:

- Files generated by the ASP.NET Core MVC “Individual Accounts” project template from Microsoft Visual Studio.
- Code samples adapted from Microsoft Learn tutorials:
  - Identity model customization in ASP.NET Core
  - Create an ASP.NET Core web app with user data protected by authorization
- Modifications and additional code written for this project.

Microsoft documentation sample code is distributed under the Microsoft Limited Public License, which permits reuse, modification, and redistribution with attribution.
All other source code in this repository retains the license of its original author. Project-specific code is provided as-is for educational purposes.
