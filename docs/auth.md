![Logo](https://123code.net/images/logo.png)

# Lưu tài liệu dưới dạng file Markdown
**Tài liệu API - [Tên dự án của bạn]**

## Tổng Quan

API của chúng tôi cung cấp các dịch vụ để quản lý [miêu tả ngắn về API của bạn].

- **Base URL:** `https://api.example.com`

---

## Endpoint

### Auth

#### Đăng nhập

- **URL:** `/auth/login`
- **Method:** `POST`
- **Headers:**
    - `Content-Type: application/json`
- **Request Body:**
  ```json
  {
    "username": "your_username",
    "password": "your_password"
  }
