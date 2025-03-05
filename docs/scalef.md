# Scalef API Documentation

## Tổng Quan
API cung cấp các dịch vụ liên quan đến việc tạo và quản lý QR Code.

- **Base URL:** `https://pub-be-stag.mp.directsale.vn/`
- **Version:** `v2`

---

## Endpoints

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
