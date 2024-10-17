# PassOp - Password Manager Backend

This is the backend for **PassOp**, a secure password manager built using Node.js, Express, and MongoDB. It provides APIs for securely saving, retrieving, and managing encrypted passwords.

## Features

- **User Authentication**: Securely checks for existing passwords associated with a user.
- **Password Encryption**: Passwords are encrypted using AES before being stored.
- **Password Decryption**: Retrieves and decrypts passwords before sending them to the user.
- **CRUD Operations**: Save, fetch, and delete encrypted passwords.
- **CORS Protection**: Restricts access based on allowed origins.

## Technologies Used

- **Node.js**: JavaScript runtime for building the backend server.
- **Express.js**: Framework for handling HTTP requests and routing.
- **MongoDB**: NoSQL database for storing user data and encrypted passwords.
- **dotenv**: For managing environment variables.
- **Crypto**: Native Node.js module for encrypting and decrypting passwords using AES.
- **CORS**: Middleware for controlling access to the API based on allowed origins.
- **body-parser**: Middleware for parsing incoming JSON data.

## Setup and Installation

### Prerequisites

- **Node.js** and **npm** installed.
- **MongoDB** instance or cloud setup.

### Steps

1. **Clone the repository**:
    ```bash
      https://github.com/Sujal-Gupta-SG/password-manager-backend.git
    cd passop-backend
    ```

2. **Install dependencies**:
    ```bash
    npm install
    ```

3. **Create a `.env` file** in the root directory and add the following variables:
    ```bash
    PORT=5000
    MONGO_URI=your_mongodb_uri
    DB_NAME=your_database_name
    COLLECTION_NAME=your_collection_name
    ALLOWEDORIGIN=your_allowed_origin
    ENCRYPTION_KEY=your_32_byte_key
    ALGORITHM=aes-256-cbc
    ```

4. **Run the server**:
    ```bash
    npm start
    ```
    The backend server will start on `http://localhost:5000`.

## API Endpoints

### Get All Passwords

- **GET** `/`
    - Fetch all passwords associated with a user by display name and email.
    - **Query Parameters**:
        - `s`: User's display name
        - `e`: User's email
    - **Response**: Returns all decrypted passwords.

### Check for Password Entry

- **GET** `/check`
    - Check if a password entry exists for a specific site and username.
    - **Query Parameters**:
        - `site`: Site name
        - `username`: Username for the site
        - `userDisplayName`: Display name of the user
        - `userEmail`: Email of the user
    - **Response**: Returns whether the password entry exists and the associated ID.

### Save a Password

- **POST** `/save`
    - Save an encrypted password entry.
    - **Request Body**:
      ```json
      {
        "form": {
          "site": "example.com",
          "username": "user",
          "password": "password123"
        },
        "user": {
          "displayName": "User Name",
          "email": "user@example.com"
        }
      }
      ```
    - **Response**: Returns the inserted document ID.

### Delete a Password

- **DELETE** `/delete/:id`
    - Delete a password entry by its ID.
    - **Params**:
        - `id`: The ObjectId of the document to delete.
    - **Response**: Returns success message if deletion was successful.

## Security

- **Encryption**: Passwords are encrypted using `aes-256-cbc` with a secure encryption key.
- **Decryption**: Passwords are decrypted using the same algorithm when fetched.
- **CORS**: Only allowed origins can access the API.

## Future Improvements

- **User Authentication**: Add authentication and authorization for better security.
- **Password Strength**: Implement a password strength checker.
- **Two-Factor Authentication**: Add support for two-factor authentication (2FA) to increase security.


