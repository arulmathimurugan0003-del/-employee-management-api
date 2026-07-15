# Employee Management API

A REST API for managing employee records, built with Java and Spring Boot. Supports full CRUD operations (Create, Read, Update, Delete) backed by a MySQL database.

## Tech stack

- **Java** — core language
- **Spring Boot** — application framework, handles configuration and dependency injection
- **Spring Data JPA** — object-relational mapping (maps Java objects to database tables)
- **Hibernate** — JPA implementation, generates and executes SQL
- **MySQL** — relational database
- **Maven** — build and dependency management

## Features

- Create, view, update, and delete employee records
- Each employee has: name, email, department, salary
- Auto-incrementing IDs, no manual ID assignment needed
- Clean layered architecture: Controller → Repository → Database

## Project structure

```
src/main/java/com/example/demo/
├── DemoApplication.java       # application entry point
├── Employee.java              # entity — maps to the employee table
├── EmployeeRepository.java    # data access layer
└── EmployeeController.java    # REST API endpoints
```

## API endpoints

| Method | Endpoint          | Description               |
|--------|-------------------|----------------------------|
| GET    | `/employees`      | Get all employees          |
| GET    | `/employees/{id}` | Get one employee by ID     |
| POST   | `/employees`      | Create a new employee      |
| PUT    | `/employees/{id}` | Update an existing employee|
| DELETE | `/employees/{id}` | Delete an employee         |

### Example request

**POST** `/employees`
```json
{
  "name": "Arun Kumar",
  "email": "arun@example.com",
  "department": "Engineering",
  "salary": 45000
}
```

**Response**
```json
{
  "id": 1,
  "name": "Arun Kumar",
  "email": "arun@example.com",
  "department": "Engineering",
  "salary": 45000.0
}
```

## How to run locally

**Prerequisites:** Java 17+, Maven, MySQL running locally.

1. Clone the repository
   ```
   git clone https://github.com/yourusername/employee-management-api.git
   ```

2. Create a MySQL database
   ```sql
   CREATE DATABASE employee_db;
   ```

3. Set your database password as an environment variable (or it defaults to `root`)
   ```
   set DB_PASSWORD=your_mysql_password
   ```

4. Run the application
   ```
   ./mvnw spring-boot:run
   ```

5. The API will be available at `http://localhost:8080`

## Testing

Tested manually using Postman — all CRUD endpoints verified working against a live MySQL database.

## What I learned

Building this project helped me understand:
- How Spring Boot auto-configures a full backend application
- The role of JPA as a specification and Hibernate as its implementation
- How a Controller, Repository, and Entity work together in a layered architecture
- Debugging real startup errors (misconfigured datasource, misplaced files, missing methods)

## Future improvements

- Add a Department entity with a one-to-many relationship to Employee
- Add input validation and proper error responses
- Add authentication (Spring Security + JWT)
- Add pagination and search/filter endpoints
