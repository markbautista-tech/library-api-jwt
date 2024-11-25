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

1. `/user/registration`
2. `/user/authentication`
3. `/add-books-author`
4. `/display-books-authors-both`
5. `/update-book`
6. `/update-author`
7. `/delete-book`
8. `/delete-author`

## DESCRIPTION, PAYLOAD, RESPONSE of API Endpoints

1. `/user/registration`

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

2. `/user/authentication`

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
        "data": 
            {
                "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vc2VjdXJpdHkub3JnIiwiYXVkIjoiaHR0cDovL3NlY3VyaXR5LmNvbSIsImlhdCI6MTczMjUyOTI0NCwiZXhwIjoxNzMyNTI5NTQ0LCJkYXRhIjp7InVzZXJfaWQiOjEwfX0.VOao22x81uRKEt5rEwtXSkjuF2o-jDJPMJ9C8DoiWrQ"
            }
    }
    </pre>

3. `/add-books-author`

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
        "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9. eyJpc3MiOiJodHRwOi8vc2VjdXJpdHkub3JnIiwiYXVkIjoiaHR0cDovL3NlY3VyaXR5LmNvbSIsImlhdCI6MTczMjUyOTU3OSwiZXhwIjoxNzMyNTI5ODc5LCJkYXRhIjp7InVzZXJfaWQiOjEwfX0.6TcZJyz8O92UV2sPrTULBBf2tpFdfjtccfNmfLmkjo0"
    }
  </pre>

  This payload is used to add a new author and their associated book to the library system. It includes author information and a JWT for authorization.

- **Response:**
  <pre>
    {
        "status": "success",
        "data": 
            {
                "message": "Successfully add books with authors to records.",
                "new_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vc2VjdXJpdHkub3JnIiwiYXVkIjoiaHR0cDovL3NlY3VyaXR5LmNvbSIsImlhdCI6MTczMjUyOTYyMSwiZXhwIjoxNzMyNTI5OTIxLCJkYXRhIjp7InN0YXR1cyI6ImFjdGl2ZSJ9fQ.045aJ8Rml_URBmikoG4X0AvmEkdyXI48ZpJGtszRi0c"
            }
    }
  </pre>

4. `/display-books-authors-both`

- **Method:** `POST`
- **Description:** Retrieves a comprehensive list of books along with their associated authors, list of authors, and list of books from the library system. This endpoint provides detailed information, allowing users to view all books and their corresponding authors in a single response.
- **Functionality:**
  - **Data Retrieval:** Fetches records from the database, including book details and linked author information.
  - **JWT Authentication:** Verifies the provided JWT token to ensure that only authenticated users can access the data.
- **Payload:**

  - **books**
  <pre>
      {
          "books_or_authors_or_both": "books",
          "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vc2VjdXJpdHkub3JnIiwiYXVkIjoiaHR0cDovL3NlY3VyaXR5LmNvbSIsImlhdCI6MTczMjUzMDQxMSwiZXhwIjoxNzMyNTMwNzExLCJkYXRhIjp7InVzZXJfaWQiOjEwfX0.DKyK1yDzGnnMW8AqmCWJ9-2daSvaTTRZBfb8bPWTFyI"
      }
  </pre>

  - **authors**
  <pre>
      {
          "books_or_authors_or_both": "authors",
          "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vc2VjdXJpdHkub3JnIiwiYXVkIjoiaHR0cDovL3NlY3VyaXR5LmNvbSIsImlhdCI6MTczMjUzMDQxOSwiZXhwIjoxNzMyNTMwNzE5LCJkYXRhIjp7InN0YXR1cyI6ImFjdGl2ZSJ9fQ.oRa9zc58uPI4rsxVmCuUh1N3NBg6VPoem5sYmvyv928"
      }
  </pre>

  - **authors with books**
  <pre>
      {
          "books_or_authors_or_both": "both",
          "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vc2VjdXJpdHkub3JnIiwiYXVkIjoiaHR0cDovL3NlY3VyaXR5LmNvbSIsImlhdCI6MTczMjUzMDU2OSwiZXhwIjoxNzMyNTMwODY5LCJkYXRhIjp7InN0YXR1cyI6ImFjdGl2ZSJ9fQ.HClJOrbmGaxcmZDu8--ZaEJfwD8J-A_cCps0WkAxbqM"
      }
  </pre>

- **Response:**

  - **books**
  <pre>
    {
        "status": "success",
        "data": 
        {
            "books": 
            [
                {
                    "book_id": 34,
                    "book_title": "Boss Naman V1.0"
                },
                {
                    "book_id": 37,
                    "book_title": "Juan Tamad 1.0"
                }
            ],
            "new_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vc2VjdXJpdHkub3JnIiwiYXVkIjoiaHR0cDovL3NlY3VyaXR5LmNvbSIsImlhdCI6MTczMjUzMDQxOSwiZXhwIjoxNzMyNTMwNzE5LCJkYXRhIjp7InN0YXR1cyI6ImFjdGl2ZSJ9fQ.oRa9zc58uPI4rsxVmCuUh1N3NBg6VPoem5sYmvyv928"
        }
    }
  </pre>

  - **authors**
  <pre>
    {
        "status": "success",
        "data": 
        {
            "authors": 
            [
                {
                    "author_id": 11,
                    "author_name": "Paulo L."
                },
                {
                    "author_id": 14,
                    "author_name": "Juan the Author"
                }
            ],
            "new_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vc2VjdXJpdHkub3JnIiwiYXVkIjoiaHR0cDovL3NlY3VyaXR5LmNvbSIsImlhdCI6MTczMjUzMDU2OSwiZXhwIjoxNzMyNTMwODY5LCJkYXRhIjp7InN0YXR1cyI6ImFjdGl2ZSJ9fQ.HClJOrbmGaxcmZDu8--ZaEJfwD8J-A_cCps0WkAxbqM"
        }
    }
  </pre>

  - **authors with books**
  <pre>
    {
        "status": "success",
        "data": 
        {
            "collections": 
            [
                {
                    "collection_id": 22,
                    "book_title": "Boss Naman V1.0",
                    "author_name": "Paulo L."
                },
                {
                    "collection_id": 25,
                    "book_title": "Juan Tamad 1.0",
                    "author_name": "Juan the Author"
                }
            ],
            "new_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vc2VjdXJpdHkub3JnIiwiYXVkIjoiaHR0cDovL3NlY3VyaXR5LmNvbSIsImlhdCI6MTczMjUzMDY3MSwiZXhwIjoxNzMyNTMwOTcxLCJkYXRhIjp7InN0YXR1cyI6ImFjdGl2ZSJ9fQ.oHHzJSONg9gi4p6pxbeMglK-GB28Jexv6JLBhU-wj5c"
        }
    }
  </pre>

5. `/update-book`

- **Method:** `POST`
- **Description:** Updates the details of an existing book in the library system. This endpoint allows authorized users to modify book information such as title of the book.
- **Functionality:**
  - **Data Validation:** Ensures that the required fields (e.g., `bookid`) are provided and correctly formatted.
  - **JWT Authentication:** Verifies the JWT token to ensure the user is authenticated.
- **Payload:**
    <pre>
    {
        "bookid": 34,
        "authorid": 11,
        "new_title": "Bossing 2.0",
        "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vc2VjdXJpdHkub3JnIiwiYXVkIjoiaHR0cDovL3NlY3VyaXR5LmNvbSIsImlhdCI6MTczMjUzNTUwMywiZXhwIjoxNzMyNTM1ODAzLCJkYXRhIjp7InVzZXJfaWQiOjEwfX0.fB5PxFxHGmpXpNgunkVtv57ft2tS4s3HAR9g_nUvhH8"
    }
    </pre>

- **Response:**
    <pre>
    {
        "status": "success",
        "data":
        {
            "message": "Successfully updated the book.",
            "new_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vc2VjdXJpdHkub3JnIiwiYXVkIjoiaHR0cDovL3NlY3VyaXR5LmNvbSIsImlhdCI6MTczMjUzNTUxMSwiZXhwIjoxNzMyNTM1ODExLCJkYXRhIjp7InN0YXR1cyI6ImFjdGl2ZSJ9fQ.zAnjRSPuXa9YOwsiTFtFZba62sTlTtbKZoniAeH1Rw8"
        }
    }
    </pre>

6. `/update-author`

- **Method:** `POST`
- **Description:** Updates the details of an existing author in the library system. This endpoint allows authorized users to modify author information, such as name of the author.
- **Functionality:**
  - **Data Validation:** Ensures required fields (e.g., `authorid`) are provided and correctly formatted.
  - **JWT Authentication:** Verifies the JWT token to ensure the user is authenticated.
  - **Database Update:** Updates the author's details in the database.
- **Payload:**
    <pre>
    {
        "authorid": 11,
        "new_author": "Pedro",
        "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vc2VjdXJpdHkub3JnIiwiYXVkIjoiaHR0cDovL3NlY3VyaXR5LmNvbSIsImlhdCI6MTczMjUzOTMwMiwiZXhwIjoxNzMyNTM5NjAyLCJkYXRhIjp7InVzZXJfaWQiOjEwfX0.9kmbOCH-bnqn27zR47xPHLRXhxUYvRBjm_wbI5xIeng"
    }
    </pre>

- **Response:**
    <pre>
    {
        "status": "success",
        "data": 
        {
            "message": "Successfully updated an author from records.",
            "new_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vc2VjdXJpdHkub3JnIiwiYXVkIjoiaHR0cDovL3NlY3VyaXR5LmNvbSIsImlhdCI6MTczMjUzOTMwOSwiZXhwIjoxNzMyNTM5NjA5LCJkYXRhIjp7InN0YXR1cyI6ImFjdGl2ZSJ9fQ.qAE1mqUnuUzc1wkRhStcCOsNzlAys1CdAMKSHlJn_E8"
        }
    }
    </pre>

7. `/delete-book`

- **Method:** `POST`
- **Description:** Deletes a specific book from the library system. This endpoint ensures only authorized users can perform deletions, protecting the integrity of the library's data.
- **Functionality:**
  - **Data Validation:** Confirms that the `bookid` exists in the database.
  - **JWT Authentication:** Verifies the JWT token to ensure the user is authenticated.
  - **Database Deletion:** Removes the specified book record from the database.
- **Payload:**
    <pre>
    {
        "bookid": 34,
        "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vc2VjdXJpdHkub3JnIiwiYXVkIjoiaHR0cDovL3NlY3VyaXR5LmNvbSIsImlhdCI6MTczMjUzOTMwOSwiZXhwIjoxNzMyNTM5NjA5LCJkYXRhIjp7InN0YXR1cyI6ImFjdGl2ZSJ9fQ.qAE1mqUnuUzc1wkRhStcCOsNzlAys1CdAMKSHlJn_E8"
    }
    </pre>

- **Response:**
    <pre>
    {
        "status": "success",
        "data": 
        {
            "message": "Successfully deleted a book from records.",
            "new_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vc2VjdXJpdHkub3JnIiwiYXVkIjoiaHR0cDovL3NlY3VyaXR5LmNvbSIsImlhdCI6MTczMjUzOTQ5NSwiZXhwIjoxNzMyNTM5Nzk1LCJkYXRhIjp7InN0YXR1cyI6ImFjdGl2ZSJ9fQ.05ZlvQqaCZf0eoEH-vYI3EYSQ8M8VnOm_b9rmhvp12Q"
        }
    }
    </pre>

8. `/delete-author`

- **Method:** `POST`
- **Description:** Deletes a specific author from the library system. This endpoint ensures only authorized users can perform deletions, maintaining the integrity and consistency of the library's data.
- **Functionality:**
  - **Data Validation:** Checks if the `authorid` exists in the database.
  - **JWT Authentication:** Verifies the JWT token to ensure the user is authenticated.
  - **Database Deletion:** Removes the specified author record from the database.
- **Payload:**
    <pre>
    {
        "authorid": 11,
        "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vc2VjdXJpdHkub3JnIiwiYXVkIjoiaHR0cDovL3NlY3VyaXR5LmNvbSIsImlhdCI6MTczMjUzOTQ5NSwiZXhwIjoxNzMyNTM5Nzk1LCJkYXRhIjp7InN0YXR1cyI6ImFjdGl2ZSJ9fQ.05ZlvQqaCZf0eoEH-vYI3EYSQ8M8VnOm_b9rmhvp12Q"
    }
    </pre>

- **Response:**
    <pre>
    {
        "status": "success",
        "data": 
        {
            "message": "Successfully deleted an author from records.",
            "new_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vc2VjdXJpdHkub3JnIiwiYXVkIjoiaHR0cDovL3NlY3VyaXR5LmNvbSIsImlhdCI6MTczMjUzOTU5MCwiZXhwIjoxNzMyNTM5ODkwLCJkYXRhIjp7InN0YXR1cyI6ImFjdGl2ZSJ9fQ.FrMCulToKUq2vsKE9pIR25bNNg8-yBKBqghwAL9eY4Y"
        }
    }
    </pre>
