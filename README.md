


# Role-Based Access Control (RBAC) in Spring Boot

This project demonstrates how to implement Role-Based Access Control (RBAC) in a Spring Boot application using JWT for authentication and authorization.

## Features
- **User Registration**: Sign up as a new user with specific roles.
- **User Authentication**: Authenticate users and issue JWT tokens.
- **Protected Endpoints**: Access control based on user roles (User, Admin, Super Admin).
- **Role-Based Access Control**: Different roles have access to specific routes.

## API Endpoints

### Public Routes

- **[POST] /auth/signup**  
  Register a new user.

- **[POST] /auth/login**  
  Authenticate a user and obtain a JWT token.

### Protected Routes

These routes require users to be authenticated and have the appropriate roles to access them. Below is a list of the protected routes and the roles required for access.

#### 1. **[GET] /users/me**
- **Roles**: `User`, `Admin`, `Super Admin`
- **Description**: Retrieve the currently authenticated user’s details.

#### 2. **[GET] /users**
- **Roles**: `Admin`, `Super Admin`
- **Description**: Retrieve a list of all registered users.

#### 3. **[POST] /admins**
- **Roles**: `Super Admin`
- **Description**: Create a new administrator.

## Role-Based Access Control Overview

The system is designed to restrict access to specific routes based on user roles. Below are the roles and their respective permissions:

- **User**: Can view their own profile information.
- **Admin**: Can view all users' information.
- **Super Admin**: Has full access to all routes, including creating new administrators.

## Getting Started

### Prerequisites
- Jdk 22
- Maven or Gradle

### Installation


 Install dependencies and run the application:

   ```bash
   mvn spring-boot:run
   ```

### Configuration

- Ensure you configure the JWT secret and other security settings in the `application.properties` or `application.yml` file.
  
```properties
jwt.secret=your_secret_key
jwt.expiration=86400000
```

## Usage

1. **Register a User**:  
   Send a `POST` request to `/auth/signup` with the following payload:
   ```json
   {
     "email": "user@gmail.com",
     "password": "password",
    "fullName":"full name"
   }
   ```

2. **Authenticate a User**:  
   Send a `POST` request to `/auth/login` with the following payload:
   ```json
   {
     "email": "user@gmail.com",
     "password": "password"
   }
   ```

   If successful, a JWT token will be returned, which should be used in subsequent requests to access protected routes.

3. **Access Protected Routes**:  
   For any protected route, include the token in the `Authorization` header of your request:
   ```bash
   Authorization: Bearer your_jwt_token
   ```

