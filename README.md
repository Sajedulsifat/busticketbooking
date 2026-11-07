Bus Ticket Booking System
A web-based bus ticket booking application built with ASP.NET Core MVC (.NET 8) and Microsoft SQL Server. The system provides separate passenger and administrator workflows for searching buses, selecting seats, managing bookings, and maintaining bus operations.
Features
Passenger
- Passenger registration and login
- Passenger dashboard and profile management
- Search buses and available schedules
- View available seats and select seats
- Book tickets
- Make and view payment records
- View booked tickets
- Cancel tickets
Administrator
- Administrator login and profile
- Admin dashboard
- Manage buses (create, view, edit, and delete)
- Manage routes
- Manage schedules
- Manage seats
- Manage passenger bookings
- Monitor transactions
- Generate reports
- Process refunds
- Handle seat-management operations
General
- ASP.NET Core MVC architecture
- Entity Framework Core for database access
- SQL Server database
- Cookie-based authentication
- Session support
- Bootstrap, jQuery, and client-side validation assets
Feature availability and behavior depend on the current implementation and configuration. Payment processing should be connected to a real payment gateway before accepting real payments.
Technology Stack
Area	Technology
Backend	ASP.NET Core MVC
Framework	.NET 8
Language	C#
ORM	Entity Framework Core 9
Database	Microsoft SQL Server
Frontend	Razor Views, HTML, CSS, JavaScript
UI library	Bootstrap
Client-side libraries	jQuery, jQuery Validation
Authentication	ASP.NET Core Cookie Authentication
Development IDE	Visual Studio
Project Structure
busticketbooking/
├── busticketbooking.sln
└── busticketbooking/
    ├── Controllers/
    │   ├── AdminController.cs
    │   ├── HomeController.cs
    │   └── PassengerController.cs
    ├── Data/
    │   └── AppDbContext.cs
    ├── Migrations/
    ├── Models/
    ├── Views/
    │   ├── Admin/
    │   ├── Home/
    │   ├── Passenger/
    │   └── Shared/
    ├── wwwroot/
    │   ├── css/
    │   ├── js/
    │   └── lib/
    ├── appsettings.json
    ├── Program.cs
    └── busticketbooking.csproj
  Prerequisites
Install the following before running the application:
- .NET 8 SDK
- Visual Studio 2022  with the ASP.NET and web development workload, or Visual Studio Code
- Microsoft SQL Server (SQL Server Express or Developer Edition is suitable for local development)
- SQL Server Management Studio (SSMS), recommended for database administration
Getting Started
1. Clone the repository
git clone https://github.com/Sajedulsifat/busticketbooking.git
cd busticketbooking
2. Open the solution
Open busticketbooking.sln in Visual Studio, or open the repository folder in VS Code.
3. Configure the database connection
The application reads the connection string named DefaultConnection from appsettings.json.

Update the ConnectionStrings section to match your local SQL Server instance and database:
{
  "ConnectionStrings": {
    "DefaultConnection": "Server=YOUR_SERVER_NAME;Database=BusTicketBookingDb;Trusted_Connection=True;MultipleActiveResultSets=true;TrustServerCertificate=True"
  }
}
For SQL Server Express, your server name may look like YOUR_COMPUTER_NAME\\SQLEXPRESS. Use the server/instance name configured on your machine.

For SQL Server authentication, use the username and password supplied for your local database. Do not commit real credentials to GitHub. For shared or production environments, store secrets in User Secrets or environment variables rather than in a committed configuration file.
4. Restore dependencies
From the directory containing busticketbooking.csproj, run:
dotnet restore
5. Apply Entity Framework Core migrations
The repository includes Entity Framework Core migrations. Install the EF Core command-line tool if it is not already installed:
dotnet tool install --global dotnet-ef
If it is already installed, update it if needed:
dotnet tool update --global dotnet-ef
Apply the existing migrations:
dotnet ef database update
Run this command from the project directory containing busticketbooking.csproj. Make sure the SQL Server instance is running and the connection string is correct.
6. Run the application
dotnet run
Database Overview
The AppDbContext defines the following main entity sets:
- Admins
- Passengers
- Buses
- Routes
- Schedules
- Bookings
- Seats
- Payments
Entity relationships and seed data are configured in Data/AppDbContext.cs, while schema changes are tracked in the Migrations directory.
Security Notes
- Never publish database passwords, API keys, or production connection strings.
- The current source includes a seeded administrator record with a hard-coded password in AppDbContext.cs. Change or remove this default credential and use secure password hashing before deploying publicly.
- Do not use plain-text password storage. Store password hashes generated with a modern password-hashing approach.
- Review authorization on all administrator and passenger actions before production deployment.
- Configure HTTPS and production-safe error handling.
- Use a payment provider's secure integration; do not store raw card details.
- Remove development-only settings and diagnostic endpoints before public deployment.
Deployment
This application targets ASP.NET Core on .NET 8, not the older ASP.NET MVC 5 / .NET Framework runtime.

Deploy it to a hosting provider that explicitly supports:
- ASP.NET Core .NET 8 (or a compatible supported runtime)
- SQL Server connectivity
- Configuration of production connection strings
Before deployment, publish the application in Release configuration and configure the hosted SQL Server connection string through the hosting provider's secure configuration settings. Do not upload local database credentials or publish profiles to the repository.
Future Improvements
Potential enhancements include:
- Integration with a production payment gateway
- Email/SMS booking confirmations
- Password reset and email verification
- Improved role-based authorization
- Booking history filters and downloadable tickets
- Automated tests and CI/CD deployment
- More comprehensive validation and audit logging
Author
Sajedul Sifat
- GitHub: @Sajedulsifat
