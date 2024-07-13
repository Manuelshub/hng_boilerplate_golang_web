# HNG Stage Three Task

## Overview
This Project contains database design and API documentation for a HNG task

## API Documentation

### Authentication
#### Create User
- **URL**: `/users`
- **Method**: `POST`
- **Request**:
    ```json
    {
        "firstName": "string",
        "lastName": "string",
        "email": "string",
        "password": "string"
    }
    ```
- **Responses**:
- **Status Code**: 200
- **Description**: `User successfully created`
    ```json
    {
        "status": "success",
        "data": {
            "id": 1,
            "firstName": "Mark",
            "lastName": "Okonkwo",
            "email": "Mark.okonkwo@example.com",
            "createdAt": "2024-07-13T20:25:09.697Z",
            "updatedAt": "2024-07-13T20:25:09.697Z"
        }
    }
    ```

- **Status code**: 400
- **Description**: `Failed to create user`
    ```json
    {
        "status": "error",
        "message": "Failed to create user",
        "errors": [
            {
                "field": "email",
                "message": "Email is invalid"
            }
        ]
    }
    ```

#### Change User Details
- **URL**: `/users/{userId}`
- **Method**: `PUT`
- **Request**:
    ```json
    {
        "firstName": "string",
        "lastName": "string",
        "email": "string"
    }
    ```
- **Responses**:
- **Status code**: 201
- **Description**: The ID of the user
    ```json
    {
        "status": "success",
        "data": {
            "id": 1,
            "firstName": "Mark",
            "lastName": "okonkwo",
            "email": "Mark.okonkwo@email.com",
            "updatedAt": "2024-07-13T20:36:16.135Z" 
        }
    }
    ```

- **Status code**: 400
- **Description**: `Failed to update user details`
    ```json
    {
        "status": "error",
        "message": "Failed to update user",
        "errors": [
            {
                "field": "email",
                "message": "Email is invalid"
            }
        ]
    }
    ```


#### Email Verification
- **URL**: `/users/verify-email`
- **Method**: `POST`
- **Request**:
    ```json
    {
        "email": "string",
        "verificationCode": "string"
    }
    ```
- **Responses**:
- **Status code**: 200
- **Description**: `Email successfully verified`
    ```json
    {
        "status": "success",
        "message": "Email verified successfully"
    }
    ```
- **Status Code**: 400
- **Description**: `Failed to verify email`
    ```json
    {
        "status": "error",
        "message": "Invalid verification code"
    }
    ```

#### Request Password Reset
- **URL**: `/users/password-reset-request`
- **Method**: `POST`
- **Request**:
    ```json
    {
        "email": "string"
    }
    ```
- **Responses**:
- **Status code**: 200
- **Description**: `Password reset email sent`
    ```json
    {
        "status": "success",
        "message": "Password reset email sent successfully"
    }
    ```
- **Status code**: 400
- **Description**: `Failed to send password reset email`
    ```json
    {
        "status": "error",
        "message": "Email not found"
    }
    ```

#### Reset Password
- **URL**: `/users/password-reset`
- **Method**: `POST`
- **Request**:
    ```json
    {
        "email": "string",
        "resetCode": "string",
        "newPassword": "string"
    }
    ```
- **Responses**:
- **Status code**: 200
- **Description**: `Password reset successfully`
    ```json
    {
        "status": "success",
        "message": "Password reset successfully"
    }
    ```

- **Status code**: 400
- **Description**: `Failed to reset password`
    ```json
    {
        "status": "error",
        "message": "Invalid reset code or email"
    }
    ```

#### Create Organisation
- **URL**: `/organisations`
- **Method**: `POST`
- **Request**:
    ```json
    {
        "name": "string",
        "description": "string"
    }
    ```
- **Responses**:
- **Status code**: 200
- **Description**: `Oranisation created successfully`
    ```json
    {
        "status": "success",
        "data": {
            "id": 1,
            "name": "Kingsley's Organisation",
            "description": "An organisation for Kingsley",
            "createdAt": "2024-07-13T21:24:14.911Z",
            "updatedAt": "2024-07-13T21:24:14.911Z"
        }
    }
    ```
- **Status Code**: 400
- **Description**: `Failed to create organisation`
    ```json
    {
        "status": "error",
        "message": "Failed to create organisation",
        "errors": [
            {
                "field": "name",
                "message": "Organisation name is required"
            }
        ]
    }
    ```

#### Add Member to Organisation
- **URL**: `/organisations/{organisationId}/members`
- **Method**: `POST`
- **Request**:
    ```json
    {
        "userId": 0
    }
    ```

- **Responses**:
- **Status code**: 200
- **Description**: `Member added successfully`
    ```json
    {
        "status": "success",
        "data": {
            "id": 1,
            "organisationId": 1,
            "userId": 2,
            "createdAt": "2024-07-13T21:28:50.903Z",
            "updatedAt": "2024-07-13T21:28:50.903Z"
        }
    }
    ```
- **Status code**: 400
- **Description**: `Failed to add member`
    ```json
    {
        "status": "error",
        "message": "Failed to add member",
        "errors": [
            {
                "field": "userId",
                "message": "User ID is invalid"
            }
        ]
    }
    ```
#### Create Transaction
- **URL**: `/transactions`
- **Method**: `POST`
- **Request**:
    ```json
    {
        "amount": 0,
        "description": "string",
        "userId": 0
    }
    ```
- **Responses**:
- **Status code**: 200
- **Description**: `Transaction created successfully`
    ```json
    {
        "status": "success",
        "data": {
            "id": 1,
            "amount": 100,
            "description": "Payment for services",
            "userId": 1,
            "createdAt": "2024-07-13T21:33:56.465Z",
            "updatedAt": "2024-07-13T21:33:56.465Z"
        }
    }
    ```
- **Status code**: 400
- **Description**: `Failed to create transaction`
    ```json
    {
        "status": "error",
        "message": "Failed to create transaction",
        "errors": [
            {
                "field": "amount",
                "message": "Amount is required"
            }
        ]
    }
    ```

#### Create Notification
- **URL**: `/notifications`
- **Method**: `POST`
- **Request**:
    ```json
    {
        "type": "string",
        "message": "string",
        "userId": 0
    }
    ```
- **Responses**:
- **Status code**: 200
- **Description**: `Notification created successfully`
    ```json
    {
        "status": "success",
        "data": {
            "id": 1,
            "type": "email",
            "message": "Your account has been created.",
            "userId": 1,
            "createdAt": "2024-07-13T21:40:12.895Z",
            "updatedAt": "2024-07-13T21:40:12.895Z"
        }
    }
    ```
- **Status code**: 400
- **Description**: `Failed to create notification`
    ```json
    {
        "status": "error",
        "message": "Failed to create notification",
        "errors": [
            {
                "field": "type",
                "message": "Type is required"
            }
        ]
    }
    ```

#### Send Message
- **URL**: `/messages`
- **Method**: `POST`
- **Request**:
    ```json
    {
        "content": "string",
        "senderId": 0,
        "receiverId": 0
    }
    ```
- **Responses**:
- **Status code**: 200
- **Description**: `Message sent successfully`
    ```json
    {
        "status": "success",
        "data": {
            "id": 1,
            "content": "Hello, how are you?",
            "senderId": 1,
            "receiverId": 2,
            "createdAt": "2024-07-13T21:50:42.890Z",
            "updatedAt": "2024-07-13T21:50:42.890Z"
        }
    }
    ```
- **Status code**: 400
- **Description**: `Failed to send message`
    ```json
    {
        "status": "error",
        "message": "Failed to send message",
        "errors": [
            {
                "field": "content",
                "message": "Content is required"
            }
        ]
    }
    ```

#### Create Blog
- **URL**: `/blogs`
- **Method**: `POST`
- **Request**:
    ```json
    {
        "title": "string",
        "content": "string",
        "authorId": 0
    }
    ```

- **Responses**:
- **Status code**: 200
- **Description**: `Blog created successfully`
    ```json
    {
        "status": "success",
        "data": {
            "id": 1,
            "title": "My First Blog",
            "content": "This is the content of my first blog.",
            "authorId": 1,
            "createdAt": "2024-07-13T21:55:23.423Z",
            "updatedAt": "2024-07-13T21:55:23.423Z"
        }
    }
    ```
- **Status code**: 400
- **Description**: `Failed to create blog`
    ```json
    {
        "status": "error",
        "message": "Failed to create blog",
        "errors": [
            {
                "field": "title",
                "message": "Title is required"
            }
        ]
    }
    ```

#### Get User Transactions
- **URL**: `/users/{usersId}/transactions`
- **Method**: `GET`
- **Request**:
- UserId required
-
- **Responses**:
- **Status code**: 200
- **Description**: `List of user transactions`
    ```json
    {
        "status": "success",
        "data": [
            {
                "id": 1,
                "amount": 100,
                "description": "Payment for services",
                "userId": 1,
                "createdAt": "2024-07-13T21:59:43.945Z",
                "updatedAt": "2024-07-13T21:59:43.945Z"
            }
        ]
    }
    ```
- **Status code**: 400
- **Description**:`Failed to get user transactions`
    ```json
    {
        "status": "error",
        "message": "Failed to get user transactions"
    }
    ```

#### Get User Notifications
- **URL**: `/users/{usersId}/Notifications`
- **Method**: `GET`
- **Request**:
- UserId required
-
- **Responses**:
- **Status code**: 200
- **Description**: `List of user notifications`
    ```json
    {
        "status": "success",
        "data": [
            {
                "id": 1,
                "type": "email",
                "message": "Your account has been created.",
                "userId": 2,
                "createdAt": "2024-07-13T21:59:43.945Z",
                "updatedAt": "2024-07-13T21:59:43.945Z"
            }
        ]
    }
    ```
- **Status code**: 400
- **Description**:`Failed to get user notifications`
    ```json
    {
        "status": "error",
        "message": "Failed to get user notifications"
    }
    ```


## Database Design

### Entities

1. Users

- `id`: Interger Primary key
- `first_name`: varchar
- `last_name`: varchar
- `email`: varchar
- `email_verified`: boolean
- `phone`: varchar
- `phone_verified`: boolean
- `password`: varchar
- `created_at`: timestamp
- `updated_at`: timestamp

2. Organisations

- `id`: integer Primary key
- `name`: varchar(255)
- `description`: text
- `created_at`: timestamp
- `updated_at`: timestamp

3. Organisation_members

- `user_id`: Integer Foreign key(users.id)
- `organisation`: Integer Foreign key(Organisations.id)
- `is_owner`: boolean
- `created_at`: timestamp
- `updated_at`: timestamp

4. Blogs

- `id`: Integer
- `author_id`: integer foreign key(Users.id)
- `title`: varchar
- `content`: text
- `created_at`: timestamp
- `updated_at`: timestamp
