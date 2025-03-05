<img src="https://123code.net/images/logo.png" width="130px" alt="Logo">

# 123Code API Documentation

## Overview
This file contains API documentation for the 123Code project, covering admin management and category CRUD operations.

---

## Endpoints

### Admin

#### CRUD Category
- **Create Category**
    - **URL:** `/admin/category`
    - **Method:** `POST`
    - **Headers:**
        - `Authorization: Bearer admin_access_token`
        - `Content-Type: application/json`
    - **Request Body:**
      ```json
      {
        "name": "New Category",
        "description": "Category description"
      }
      ```
    - **Response:**
      ```json
      {
        "id": 1,
        "name": "New Category",
        "description": "Category description"
      }
      ```

- **Get Categories**
    - **URL:** `/admin/category`
    - **Method:** `GET`
    - **Headers:**
        - `Authorization: Bearer admin_access_token`
    - **Response:**
      ```json
      [
        {
          "id": 1,
          "name": "Category 1",
          "description": "Description 1"
        },
        {
          "id": 2,
          "name": "Category 2",
          "description": "Description 2"
        }
      ]
      ```

#### CRUD User
- **Create User**
    - **URL:** `/admin/users`
    - **Method:** `POST`
    - **Headers:**
        - `Authorization: Bearer admin_access_token`
        - `Content-Type: application/json`
    - **Request Body:**
      ```json
      {
        "username": "new_user",
        "email": "user@example.com",
        "role": "admin"
      }
      ```
    - **Response:**
      ```json
      {
        "id": 1,
        "username": "new_user",
        "email": "user@example.com",
        "role": "admin"
      }
    
