[← Back to Home](./index.md)

# 📘 Scalef API Documentation

## 🏗 Tổng Quan
Tổng hợp các API liên quan đến dự án Scalef.

- **🌐 Base URL:** `https://pub-be-stag.mp.directsale.vn/`
- **📌 Version:** `v2`

---

## 🚀 Danh sách các API

### 🔑 Render Token
- **🛣 URL:** `/api/v2/gen-token`
- **📝 Method:** `POST`
- **📩 Headers:**
    - `X-Port-Type: PUB`
    - `Content-Type: application/json`
- **📥 Request Body:**
    ```json
    {
        "network_id": 1,
        "type": "PUB",
        "time": "3/5/2025, 11:57:58 PM",
        "token": "x8R09aUanv5peXl98rvrbwX3AKz14E7d"
    }
    ```
- **🔢 Parameters:**
    - `network_id` *(required)*: ID của network
    - `type` *(required)*: Loại port
    - `time` *(required)*: Thời gian hết hạn của token
    - `token` *(required)*: Token cần render

#### ✅ Response Success:
- **🆗 Status Code:** `200`
- **📄 Content-Type:** `application/json`
- **📤 Body:**
    ```json
    {
        "status": "success",
        "data": {
            "token": "eyJpdiI6InY2M1..."
        }
    }
    ```

#### ❌ Response Error:
1. **Trường hợp thông tin không hợp lệ**
    - **🆗 Status Code:** `200`
    - **📄 Content-Type:** `application/json`
    - **📤 Body:**
      ```json
      {
         "status": "fail",
         "data": "Thông tin không hợp lệ"
      }
      ```

2. **Trường hợp thiếu thông tin required**
    - **🆗 Status Code:** `200`
    - **📄 Content-Type:** `application/json`
    - **📤 Body:**
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
    - **📝 Description:** Lỗi này xảy ra khi thiếu thông tin bắt buộc.

---

### 🔗 Social Signup
- **🛣 URL:** `/api/v1/auth/social-signup`
- **📝 Method:** `POST`
- **📩 Headers:**
    - `X-Port-Type: PUB`
    - `Content-Type: application/json`
- **📥 Request Body:**
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
    ```

---

### 📌 QR Code
- **🛣 URL:** `/api/v2/qr-code`
- **📝 Method:** `GET`
- **📩 Headers:**
    - `X-Network-Id: 1`
    - `X-Port-Type: PUB`
    - `Content-Type: application/json`
    - `Authorization: Bearer <access_token>`
    - `X-Network-Token: <network_token>`

#### ✅ Response Success:
- **🆗 Status Code:** `200`
- **📄 Content-Type:** `image/*`
- **📤 Body:** Binary data của ảnh QR code

#### ❌ Response Error:
1. **Trường hợp URL bị thiếu**
    - **🆗 Status Code:** `200`
    - **📄 Content-Type:** `application/json`
    - **📤 Body:**
      ```json
      {
         "status": "fail",
         "data": "URL không được để trống"
      }
      ```

2. **Trường hợp không thể tạo mã QR**
    - **🆗 Status Code:** `200`
    - **📄 Content-Type:** `application/json`
    - **📤 Body:**
      ```json
      {
         "status": "fail",
         "data": "Không thể tạo mã QR code"
      }
      ```

3. **Trường hợp lỗi hệ thống**
    - **🆗 Status Code:** `200`
    - **📄 Content-Type:** `application/json`
    - **📤 Body:**
      ```json
      {
         "status": "fail",
         "data": "Không thể tạo mã QR code. Vui lòng thử lại sau."
      }
      ```

---

## 📌 Lưu ý:
- **Authorization:** Token cần được cung cấp dưới dạng Bearer token trong header `Authorization`.
- **X-Network-Token:** Là token bắt buộc để xác thực network.
- **Response:** Nếu thành công, API sẽ trả về ảnh QR code trực tiếp.

---

📌 **Cập nhật lần cuối:** *06/03/2025*
