# Creating My First Spring Boot API with Validation, Database Persistence, and Exception Handling

## Project Description

This project is a Spring Boot REST API that allows users to manage tasks. Users can create, read, update, and delete tasks (CRUD operations). The API includes input validation to ensure correct data entry such as title length and required fields.

The application follows a layered architecture:
- Controller: Handles HTTP requests
- Service: Contains business logic
- Model: Represents task data

---

## How to Run the Application

### Option 1: Using an IDE
1. Open the project in IntelliJ IDEA or VS Code
2. Locate `CampusTaskboardApplication.java`
3. Right-click and click Run
4. Open:
http://localhost:8080

---

### Option 2: Using Terminal
1. Open a terminal in the project folder
2. Run:

   ./mvnw spring-boot:run

3. Open in browser or Postman:
http://localhost:8080/api/tasks

---

## API Endpoints

### Get all tasks
   GET /api/tasks

### Get task by ID
   GET /api/tasks/{id}

### Create tas
   POST /api/tasks

Example JSON:
   {
   "title": "Complete Homework 5",
   "description": "Finish Spring Boot API assignment",
   "completed": false,
   "priority": "HIGH"
   }

---

### Update task
   PUT /api/tasks/{id}

Example JSON:
   {
   "title": "Updated Task",
   "description": "Updated description",
   "completed": true,
   "priority": "HIGH"
   }

---

### Delete task
   DELETE /api/tasks/{id}

---

## Validation

- Title must be between 3 and 100 characters
- Title cannot be empty
- Description cannot exceed 500 characters

If invalid data is sent, API returns:
400 Bad Request

---

## Database (H2)

This project uses Spring Data JPA with an H2 in-memory database.

### H2 Console
   http://localhost:8080/h2-console

### Settings
- JDBC URL: jdbc:h2:mem:taskboarddb
- Username: sa
- Password: (empty)

---

## New Features Added

- Database persistence using JPA
- H2 database integration
- Repository layer
- Search functionality
- Pagination and sorting
- Filtering tasks

---

## New API Endpoints

GET /api/tasks/completed  
GET /api/tasks/incomplete  
GET /api/tasks/priority/HIGH  
GET /api/tasks/search?keyword=homework  
GET /api/tasks/paginated?page=0&size=5&sortBy=title  

---

## Exception Handling

Custom exception handling is implemented using:

@RestControllerAdvice

### Custom Exceptions
- TaskNotFoundException
- InvalidTaskDataException

---

## Error Response Example

{
  "timestamp": "...",
  "status": 404,
  "error": "Not Found",
  "message": "Task not found",
  "path": "/api/tasks/1"
}

---

## DTOs

- TaskRequest: Used for incoming data
- TaskResponse: Used for outgoing data

---

## Soft Delete

Instead of deleting permanently:
- Tasks are marked as deleted = true
- Data can be restored later

---

## Logging

Each request is logged:
GET /api/tasks - Status: 200 - Duration: 12ms

---

## Actuator

Health Check:
http://localhost:8080/actuator/health

Response:
   {
   "status": "UP"
   }

---

## Demo Videos

Data Features:
https://www.youtube.com/watch?v=mo7y3R6u-RQ

Advanced Features:
https://youtu.be/6tCTppEGuNE