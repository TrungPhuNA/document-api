[← Back to Home](./index.md)

# Scalef API Documentation

## Tổng Quan
Tổng hợp các API liên quan đến dự án Scalef

- **Base URL:** `https://pub-be-stag.mp.directsale.vn/`
- **Version:** `v2`
---
## Danh sách các API

### Render Token
- **URL:** `/api/v2/gen-token`
- **Method:** `POST`
- **Headers:**
    - `X-Port-Type: PUB`
    - `Content-Type: application/json`
- **Request Body:**
    ```json
    {
        "network_id": 1,
        "type": "PUB",
        "time": "3/5/2025, 11:57:58 PM",
        "token": "x8R09aUanv5peXl98rvrbwX3AKz14E7d"
    }
    ```
- **Parameters:**
    - `network_id`: ID của network (required)
    - `type`: Loại port (required)
    - `time`: Thời gian hết hạn của token (required)
    - `token`: Token cần render (required)

- **Response Success:**
    - **Status Code:** `200`
    - **Content-Type:** `application/json`
    - **Body:**
      ```json
      {
        "status": "success",
        "data": {
            "token": "eyJpdiI6InY2M1..."
        }
      }
      ```

- **Response Error:**
    - **Status Code:** `200`
    - **Content-Type:** `application/json`
    - **Body:**
      ```json
      {
        "status": "fail",
        "data": "Thông tin không hợp lệ"
      }
      ```
- **Response Error:**
    - **Status Code:** `200`
    - **Content-Type:** `application/json`
    - **Body:**
      ```json
      {
            "status": "fail",
            "data": {
                "type": [
                    "The type field is required."
                ]
            }
        }
      ```
    - **Description:** Lỗi này xẩy ra khi truyền vào thiếu các thông tin required 
### Social Signup

- **URL:** `/api/v1/auth/social-signup`
- **Method:** `POST`
- **Headers:**
  - `X-Port-Type: PUB`
  - `Content-Type: application/json`
- **Request Body:**
    ```json
    {
        "_id_token": "123456789",
        "provider": "google",
        "social_data": {
            "email": "phu994_009@gmail.com",
            "username": "phu994_009",
            "given_name": "phu",
            "family_name": "phan",
            "google_id": "google_0986420994_009",
            "avatar": "https://123code.net/images/logo.png"
        }
    }
### QR Code

- **URL:** `/api/v2/qr-code`
- **Method:** `GET`
- **Headers:**
    - `X-Network-Id: 1`
    - `X-Port-Type: PUB`
    - `Content-Type: application/json`
    - `Authorization: Bearer <access_token>`
    - `X-Network-Token: <network_token>`

- **Response Success:**
    - **Status Code:** `200`
    - **Content-Type:** `image/*`
    - **Body:** Binary data của ảnh QR code

- **Response Error:**
    - **Status Code:** `200`
    - **Content-Type:** `application/json`
    - **Body:**
      ```json
      {
        "status": "fail",
        "data": "URL không được để trống"
      }
      ```
    - **Status Code:** `200`
    - **Content-Type:** `application/json`
    - **Body:**
      ```json
      {
        "status": "fail",
        "data": "Không thể tạo mã QR code"
      }
      ```
    - **Status Code:** `200`
    - **Content-Type:** `application/json`
    - **Body:**
      ```json
      {
        "status": "fail",
        "data": "Không thể tạo mã QR code. Vui lòng thử lại sau."
      }
      ```

### Lưu ý:
- Token cần được cung cấp dưới dạng Bearer token trong header Authorization
- X-Network-Token là token bắt buộc để xác thực network
- Response trả về trực tiếp là ảnh QR code nếu thành công