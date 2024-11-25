# Simple Library System API with JWT Authentication

### Developed by: markbautista-tech (Bautista, Ray Mark R.)

## Features

- **User Authentication:** Secure login and registration with JWT.
- **Book Management:** CRUD operations for managing books.
- **User Management:** Handle library users and their permissions.
- **Protected Routes:** Access controlled using JWT tokens.
- **Error Handling:** Custom error messages for better user experience.

## API DESCRIPTION

This API provides functionality to manage a library system, ensuring secure access to resources through JWT (JSON Web Token) authentication.

## API Endpoints

1. /user/registration
2. /user/authentication
3. /add-books-author
4. /display-books-authors-both
5. /update-book
6. /update-author
7. /delete-book
8. /delete-author

## DESCRIPTION, PAYLOAD, RESPONSE of API Endpoints

1. /user/registration

- **Method:** `POST`
- **Description:** This endpoint registers a new user in the library system by creating an account with their provided credentials. Upon successful registration, the system stores the user's information securely and returns a confirmation response.
- **Functionality:**
  - **Validation:** Ensures that all required fields (such as username and password) are provided.
  - **Password Hashing:** The user's password is hashed using a secure hashing algorithm before being stored in the database to protect sensitive information.
- **Payload:**
    <pre>
    {
    "username": "admin",
    "password": "admin"
    }
    </pre>

  This payload provides a simple example of user credentials that can be used for registration or authentication.

- **Response:**
    <pre>
    {
    "status": "success",
    "data": null
    }
    </pre>

2. /user/authentication

- **Method:** `POST`
- **Description:** Authenticates a user by validating their credentials (username and password). Upon successful authentication, the system generates and returns a JWT (JSON Web Token) that can be used to access protected routes within the library system.
- **Functionality:**
  - **Validation:** Compares the provided username and password with stored user data. Ensures that both fields match an existing account.
  - **Token Generation:** Creates a JWT token containing user-specific information (e.g., user ID, role). This token is required for accessing secure endpoints.
- **Payload:**
    <pre>
    {
    "username": "admin",
    "password": "admin"
    }
    </pre>

  This payload provides a simple example of user credentials that can be used for authentication to access the library system.

- **Response:**
    <pre>
    {
    "status": "success",
    "data": {
        "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vc2VjdXJpdHkub3JnIiwiYXVkIjoiaHR0cDovL3NlY3VyaXR5LmNvbSIsImlhdCI6MTczMjUyOTI0NCwiZXhwIjoxNzMyNTI5NTQ0LCJkYXRhIjp7InVzZXJfaWQiOjEwfX0.VOao22x81uRKEt5rEwtXSkjuF2o-jDJPMJ9C8DoiWrQ"
    }
    }
    </pre>

3. /add-books-author

- **Method:** `POST`
- **Description:** Adds a new author and their associated book to the library system. This endpoint ensures that only authorized users can add authors, maintaining the integrity and security of the library database.
- **Functionality:**
  - **Validation:** Ensures both `author_name` and `book_title` fields are provided.
  - **JWT Authentication:** Decodes and verifies the provided token.
- **Payload:**
  <pre>
  {
  "author_name": "Juan the Author",
  "book_title": "Juan Tamad 1.0",
  "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vc2VjdXJpdHkub3JnIiwiYXVkIjoiaHR0cDovL3NlY3VyaXR5LmNvbSIsImlhdCI6MTczMjUyOTU3OSwiZXhwIjoxNzMyNTI5ODc5LCJkYXRhIjp7InVzZXJfaWQiOjEwfX0.6TcZJyz8O92UV2sPrTULBBf2tpFdfjtccfNmfLmkjo0"
  }
  </pre>

  This payload is used to add a new author and their associated book to the library system. It includes author information and a JWT for authorization.

- **Response:**
  <pre>
  {
  "status": "success",
  "data": {
  "message": "Successfully add books with authors to records.",
  "new_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vc2VjdXJpdHkub3JnIiwiYXVkIjoiaHR0cDovL3NlY3VyaXR5LmNvbSIsImlhdCI6MTczMjUyOTYyMSwiZXhwIjoxNzMyNTI5OTIxLCJkYXRhIjp7InN0YXR1cyI6ImFjdGl2ZSJ9fQ.045aJ8Rml_URBmikoG4X0AvmEkdyXI48ZpJGtszRi0c"
  }
  }
  </pre>
