# Crosscheck API Documentation

## Overview
Tổng hợp các API dành cho crosscheck ADMIN && ADV

---

## ADMIN

### B2B

#### BBDS và DNTT
- **Lấy link BBDS và DNTT**
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
    
