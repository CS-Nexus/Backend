﻿# Nexus Backend (.NET 8)

## Overview

This is a backend API for the Nexus application, built with ASP.NET Core (.NET 8). It provides authentication, payment processing (via Stripe), user management, and real-time features using SignalR.

---

## Features

- **JWT Authentication**: Secure login and registration with JWT tokens.
- **User Management**: Signup, signin, and profile management.
- **Payment Integration**: Stripe-based payment method management and payment processing.
- **Real-time Communication**: SignalR hub for leaderboard updates.
- **Swagger UI**: Interactive API documentation and testing.
- **Custom Middleware**: For authentication and request handling.
- **Logging**: Console logging for diagnostics.

---

## Folder Structure
```
├── auth/
│   ├── Controllers/         # API controllers (e.g., PaymentController)
│   ├── Models/              # Data models (e.g., User, PaymentMethod, AuthModels)
│   ├── Services/            # Business logic (e.g., PaymentService)
│   ├── Hubs/                # SignalR hubs (e.g., LeaderboardHub)
│   └── Middlewares/         # Custom middleware (e.g., AuthMiddleware)
├── myapp/
│   ├── Data/                # Entity Framework DbContext and migrations
│   ├── DataAccess/          # Data access logic (e.g., UserDataAccess)
│   └── Services/            # Additional services (e.g., TokenService)
├── appsettings.json         # Configuration (connection strings, JWT, Stripe)
├── Program.cs               # Application entry point and DI setup
└── README.md                # Project documentation
```

## How to Run

1. **Prerequisites**
   - [.NET 8 SDK](https://dotnet.microsoft.com/download)
   - SQL Server (local or remote)
   - Stripe account (for payment integration)

2. **Configuration**
   - Update `appsettings.json` with your database connection string, JWT settings, and Stripe secret key.

3. **Database**
   - Ensure the `Your Project DB` database exists and is accessible.
   - Run EF Core migrations if needed.

4. **Run the Application**
	```
	dotnet run
	```
The API will be available at `http://localhost:8080` (or as configured).

5. **API Documentation**
   - Open [http://localhost:8080](http://localhost:8080) in your browser for Swagger UI.

---

## API Endpoints

| Method | Route                                 | Description                        | Auth Required |
|--------|---------------------------------------|------------------------------------|--------------|
| POST   | `/api/payment/add`                    | Add a payment method (Stripe)      | Yes          |
| GET    | `/api/payment` (example)              | List payment methods (if exists)   | Yes          |
| ...    | ...                                   | ...                                | ...          |
| GET    | `/leaderboardHub` (SignalR endpoint)  | Real-time leaderboard updates      | Yes          |

> **Note:** For a full list, see Swagger UI or the Controllers folder.

---

## Configuration Example (`appsettings.json`)
	{ 
		"Jwt": { 
			"Key": "...", 
			"Issuer": "...", 
			"Audience": "..." 
		}, 
		"ConnectionStrings": { 
			"DefaultConnection": "Server=...;Database=...;integrated security=true;" 
		}, 
		"Stripe": { 
			"SecretKey": "sk_test_..." 
		} 
	}
	
---

## Contributing

1. Fork the repository.
2. Create a feature branch.
3. Commit your changes.
4. Open a pull request.

---

## License

This project is licensed under the MIT License.

---

**Tip:**  
For a complete and up-to-date list of endpoints, always refer to the Swagger UI generated by the application.
