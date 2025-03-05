# Scalef API Documentation

## Tổng Quan
Tổng hợp các API liên quan đến dự án Scalef, bao gồm các chức năng xác thực token và tạo QR code.

- **Base URL:** `https://pub-be-stag.mp.directsale.vn/`
- **Version:** `v2`

---

## Endpoints

### Render Token

#### Tạo Token

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

### QR Code

#### Tạo QR Code

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

#### Lưu ý:
- Token cần được cung cấp dưới dạng Bearer token trong header Authorization
- X-Network-Token là token bắt buộc để xác thực network
- Response trả về trực tiếp là ảnh QR code nếu thành công