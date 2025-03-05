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
    - **Status Code:** `401`
    - **Content-Type:** `application/json`
    - **Body:**
      ```json
      {
        "status": "error",
        "message": "Unauthorized"
      }
      ```
    - **Mô tả lỗi:**
        - `401`: Token không hợp lệ hoặc đã hết hạn
        - `403`: Không có quyền truy cập
        - `500`: Lỗi server

#### Lưu ý:
- Token cần được cung cấp dưới dạng Bearer token trong header Authorization
- X-Network-Token là token bắt buộc để xác thực network
- Response trả về trực tiếp là ảnh QR code nếu thành công
