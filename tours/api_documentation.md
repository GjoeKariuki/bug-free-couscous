# API Documentation for Tours and Travel Application

## Overview
This document provides an overview of the API design for the tours and travel application, focusing on security, reliability, and scalability.

### Security Features
1. **Authentication**:
   - Use JWT (JSON Web Tokens) for secure user authentication.
   - Implement token expiration and refresh mechanisms.

2. **Authorization**:
   - Role-based access control (RBAC) to restrict access to certain endpoints based on user roles (e.g., admin, user).

3. **Input Validation**:
   - Validate all incoming data to prevent SQL injection and other attacks.
   - Use Django's built-in validation features.

4. **HTTPS**:
   - Ensure that the API is served over HTTPS to encrypt data in transit.

5. **Rate Limiting**:
   - Implement rate limiting to prevent abuse and denial-of-service attacks.
   - Use tools like Django Ratelimit to limit the number of requests a user can make to the API within a specified time frame.

### API Endpoints

#### 1. Authentication Endpoints

- **POST /api/auth/login**
  - **Request**: 
    - Body: `{ "username": "string", "password": "string" }`
  - **Response**: 
    - Success: `{ "token": "string" }`
    - Error: `{ "error": "string" }`
  - **Status Codes**:
    - 200 OK: Successful login
    - 401 Unauthorized: Invalid credentials

- **POST /api/auth/register**
  - **Request**: 
    - Body: `{ "username": "string", "password": "string", "email": "string" }`
  - **Response**: 
    - Success: `{ "message": "User registered successfully." }`
    - Error: `{ "error": "string" }`
  - **Status Codes**:
    - 201 Created: User registered successfully
    - 400 Bad Request: Validation errors

#### 2. Tours Endpoints

- **GET /api/tours/**
  - **Response**: 
    - Success: `[ { "id": "integer", "name": "string", "description": "string", "price": "decimal", "image": "string" }, ... ]`
  - **Status Codes**:
    - 200 OK: Successful retrieval of tours

- **GET /api/tours/{id}**
  - **Response**: 
    - Success: `{ "id": "integer", "name": "string", "description": "string", "price": "decimal", "image": "string" }`
    - Error: `{ "error": "Tour not found." }`
  - **Status Codes**:
    - 200 OK: Tour found
    - 404 Not Found: Tour does not exist

- **POST /api/tours/**
  - **Request**: 
    - Body: `{ "name": "string", "description": "string", "price": "decimal", "image": "file" }`
  - **Response**: 
    - Success: `{ "message": "Tour created successfully." }`
    - Error: `{ "error": "string" }`
  - **Status Codes**:
    - 201 Created: Tour created successfully
    - 400 Bad Request: Validation errors

- **PUT /api/tours/{id}**
  - **Request**: 
    - Body: `{ "name": "string", "description": "string", "price": "decimal", "image": "file" }`
  - **Response**: 
    - Success: `{ "message": "Tour updated successfully." }`
    - Error: `{ "error": "Tour not found." }`
  - **Status Codes**:
    - 200 OK: Tour updated successfully
    - 404 Not Found: Tour does not exist

- **DELETE /api/tours/{id}**
  - **Response**: 
    - Success: `{ "message": "Tour deleted successfully." }`
    - Error: `{ "error": "Tour not found." }`
  - **Status Codes**:
    - 200 OK: Tour deleted successfully
    - 404 Not Found: Tour does not exist

### Conclusion
This API documentation outlines the endpoints, request methods, expected responses, and security considerations for the tours and travel application. It emphasizes security, reliability, and scalability to ensure a robust application.
