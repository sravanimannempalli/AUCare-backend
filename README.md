# AUCare – Backend

The backend of **AUCare – Smart Campus Maintenance and Complaint Management System** provides REST APIs for user authentication, complaint submission, complaint retrieval, and complaint status management.

It is developed using Java and Spring Boot, with MySQL as the database.

## Features

- **User Registration** – Registers new student accounts.
- **User Authentication** – Supports login and logout.
- **Session Management** – Maintains authenticated user sessions.
- **Complaint Management** – Creates and retrieves maintenance complaints.
- **Status Updates** – Allows authorized administrators to update complaint statuses.
- **Role-Based Access Control** – Restricts operations based on user roles.
- **Password Encryption** – Uses BCrypt to store passwords securely.

## Technology Stack

- Java
- Spring Boot
- Spring Security
- Spring Data JPA
- Hibernate
- MySQL
- Maven
- REST APIs

## Project Structure

```text
campus-maintenance/
├── src/
│   ├── main/
│   │   ├── java/com/campus/campus_maintenance/
│   │   │   ├── config/
│   │   │   ├── entity/
│   │   │   ├── repository/
│   │   │   ├── controller/
│   │   │   └── CampusMaintenanceApplication.java
│   │   └── resources/
│   │       └── application.properties
│   └── test/
├── .mvn/
├── mvnw
├── mvnw.cmd
└── pom.xml
```

## Prerequisites

Install the following:

- Java 21
- MySQL 8 or a compatible MySQL version
- Git (optional)

Maven is provided through the included Maven Wrapper.

## Database Configuration

1. Start MySQL.
2. Create the database:

   ```sql
   CREATE DATABASE campus_maintenance;
   ```

3. Configure the database URL, username, and password locally.

   Example environment-variable configuration:

   ```properties
   spring.datasource.url=${DB_URL:jdbc:mysql://localhost:3306/campus_maintenance}
   spring.datasource.username=${DB_USERNAME:root}
   spring.datasource.password=${DB_PASSWORD}
   ```

4. Set `DB_PASSWORD` to your local MySQL password before starting the backend.

**Security:** Never commit actual database passwords or other secrets to GitHub.

## Running the Backend

Open PowerShell in the backend directory:

```powershell
.\mvnw.cmd spring-boot:run
```

The backend normally runs at:

```text
http://localhost:8080
```

To compile and test the project, run:

```powershell
.\mvnw.cmd clean install
```

## API Endpoints

Base URL: `http://localhost:8080`

| Method | Endpoint | Purpose |
|---|---|---|
| POST | `/api/auth/register` | Register a student |
| POST | `/api/auth/login` | Log in |
| GET | `/api/auth/me` | Get the current user's details |
| POST | `/api/auth/logout` | Log out |
| GET | `/api/complaints` | Retrieve complaints |
| POST | `/api/complaints` | Submit a complaint |
| PUT | `/api/complaints/{id}/status` | Update complaint status (admin only) |

Authenticated requests use the session maintained by the backend. The frontend must send credentials with requests.

## Complaint Status

A complaint is initially assigned the **Pending** status. Authorized administrators can update the status as the complaint progresses.

## Frontend Integration

The React frontend communicates with this backend through REST APIs. Ensure the frontend origin is permitted by the backend CORS configuration and that MySQL is running.

## Project

**AUCare – Smart Campus Maintenance and Complaint Management System**

Developed as an academic full-stack project using React, Spring Boot, Spring Security, and MySQL.

