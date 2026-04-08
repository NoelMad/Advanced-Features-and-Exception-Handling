# Creating-My-First-Spring-Boot-API-with-Validation & Adding Database Persistence with Spring Data JPA & Advanced Features and Exception Handling

## Project Description

This project is a Spring Boot REST API that allows users to manage tasks. Users can create, read, update, and delete tasks (CRUD operations). The API also includes input validation to ensure that all data entered meets requirements such as title length and required fields.

This project demonstrates how to build a structured backend using controllers, services, and models in Spring Boot.

The application follows a layered architecture:

* Controller: Handles HTTP requests
* Service: Contains business logic
* Model: Represents task data

---

## How to Run the Application

### Option 1: Using an IDE

1. Open the project in IntelliJ IDEA or VS Code
2. Locate `CampusTaskboardApplication.java`
3. Right-click and click **Run**
4. The server will start at:
   [http://localhost:8080](http://localhost:8080)

---

### Option 2: Using Terminal

1. Open a terminal in the project folder
2. Run:

   ```
   ./mvnw spring-boot:run
   ```
3. Open in browser or Postman:
   [http://localhost:8080/api/tasks](http://localhost:8080/api/tasks)

---

## API Endpoints Documentation

## Testing the API

The API was tested using Postman.

Each endpoint (GET, POST, PUT, DELETE) was tested by sending HTTP requests to:
[http://localhost:8080/api/tasks](http://localhost:8080/api/tasks)

Headers used:
Content-Type: application/json

Screenshots of successful requests and responses are included in the project submission.

---

### GET all tasks

GET /api/tasks
Returns a list of all tasks

---

### GET task by ID

GET /api/tasks/{id}
Returns a single task by ID

---

### POST create task

POST /api/tasks
Creates a new task

Example JSON:

```json
{
   "title": "Complete Homework 5",
   "description": "Finish Spring Boot API assignment",
   "completed": false,
   "priority": "HIGH"
}
```

---

### PUT update task

PUT /api/tasks/{id}
Updates an existing task

Example JSON:

```json
{
   "title": "Updated Task",
   "description": "Updated description",
   "completed": true,
   "priority": "HIGH"
}
```

---

### DELETE task

DELETE /api/tasks/{id}
Deletes a task

---

## Validation

The API validates input using Spring Validation:

* Title must be between 3 and 100 characters
* Title cannot be empty
* Description cannot exceed 500 characters

If invalid data is submitted, the API returns a **400 Bad Request** with error messages.

---

## Video Link

[Watch the demo](https://www.youtube.com/watch?v=mo7y3R6u-RQ)

---

## 🚀 Database Persistence

This project has been extended to use **Spring Data JPA** and an **H2 in-memory database**. Tasks are now stored in a database instead of an in-memory list.

### New Features Added

* Database persistence using JPA
* H2 database integration
* Repository layer for data access
* Search functionality
* Pagination and sorting
* Filtering by completion and priority

---

## Database Configuration

The application uses the H2 in-memory database.

### Access H2 Console

[http://localhost:8080/h2-console](http://localhost:8080/h2-console)

### Connection Settings

* JDBC URL: `jdbc:h2:mem:taskboarddb`
* Username: `sa`
* Password: (leave empty)

---

## JPA & Repository

* `@Entity` is used to map the Task class to the database
* `JpaRepository` handles CRUD operations automatically
* Custom query methods allow filtering and searching

Example:

```java
List<Task> findByCompletedTrue();
List<Task> findByPriority(Task.Priority priority);
```

---

## New API Endpoints (Homework 6)

### Get completed tasks

GET /api/tasks/completed

### Get incomplete tasks

GET /api/tasks/incomplete

### Get tasks by priority

GET /api/tasks/priority/HIGH

---

### Search tasks

GET /api/tasks/search?keyword=homework

---

### Pagination & Sorting

GET /api/tasks/paginated?page=0&size=5&sortBy=title

---

## Database Testing

* Tasks created via POST are saved in the database
* Verified using the H2 Console:

```sql
SELECT * FROM tasks;
```

---
## Video Link

[Watch the demo](https://youtu.be/6tCTppEGuNE)