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

| Tham số      | Bắt buộc | Kiểu dữ liệu | Mô tả |
|-------------|---------|------------|------|
| `network_id` | ✅ | `integer` | ID của network |
| `type` | ✅ | `string` | Loại port (ví dụ: `"PUB"`) |
| `time` | ✅ | `string` | Thời gian hết hạn của token, định dạng `MM/DD/YYYY, HH:MM:SS AM/PM` |
| `token` | ✅ | `string` | Token cần render |

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

#### ❌ Response Error || Fail:
1. **Trường hợp thông tin không hợp lệ**
    - **🆗 Status Code:** `200`
    - **📤 Body:**
      ```json
      {
         "status": "fail",
         "data": "Thông tin không hợp lệ"
      }
      ```
      ```json
      {
          "status": "error",
          "message": "The only supported ciphers are AES-128-CBC and AES-256-CBC with the correct key lengths.",
          "errorCode": ""
      }
      ```


2. **Trường hợp thiếu thông tin required**
    - **🆗 Status Code:** `200`
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

- **🔢 Parameters:**
    - **Chỉ được chọn một trong hai trường hợp:**
        1. Truyền `id_token`, **không cần** `social_data`
        2. Truyền `social_data`, **không cần** `id_token`

| Tham số        | Bắt buộc | Kiểu dữ liệu | Mô tả |
|---------------|--------|------------|------|
| `provider` | ✅ | `string` | Loại tài khoản (`google`, `facebook`, v.v.) |
| `id_token` | ❌ (Bắt buộc nếu không có `social_data`) | `string` | Token ID của user từ provider |
| `social_data` | ❌ (Bắt buộc nếu không có `id_token`) | `object` | Thông tin user từ provider |
| `social_data.email` | ✅ (nếu có `social_data`) | `string` | Email của user |
| `social_data.username` | ✅ (nếu có `social_data`) | `string` | Tên đăng nhập |
| `social_data.given_name` | ❌ | `string` | Tên của user |
| `social_data.family_name` | ❌ | `string` | Họ của user |
| `social_data.google_id` | ✅ | `string` | ID Google của user |
| `social_data.avatar` | ❌ | `string` | Link avatar của user |

#### ✅ Trường hợp 1: Sử dụng `id_token`
- **📥 Request Body:**
    ```json
    {
        "id_token": "token.......................",
        "provider": "google"
    }
    ```

#### ✅ Trường hợp 2: Sử dụng `social_data`
- **📥 Request Body:**
    ```json
    {
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

#### ❌ Response Error:
- **📄 Lỗi khi thiếu `id_token` hoặc `social_data`**
    ```json
    {
        "status": "fail",
        "data": {
            "id_token": [
                "The id token field is required when social data is not present."
            ],
            "social_data": [
                "The social data field is required when id token is not present."
            ]
        }
    }
    ```

#### ✅ Response Success:
- **📄 Body:**
    ```json
    {
        "status": "success",
        "data": {
            "user": {
                "sso_id": 505419,
                "level_id": 1,
                "username": "phu994_010",
                "email": "phu994_010@gmail.com",
                "avatar": null,
                "facebook_id": null,
                "google_id": "google_0986420994_010",
                "identifier_id": null,
                "created_at": "2025-03-06 22:30:45",
                "id": 228989,
                "roles": [
                    {
                        "id": 3,
                        "name": "PUB_PUBLISHER",
                        "guard_name": "api",
                        "created_at": "2019-08-15 04:28:52",
                        "updated_at": "2019-08-15 04:28:52",
                        "pivot": {
                            "model_id": 228989,
                            "role_id": 3,
                            "model_type": "Isvn\\User\\Entities\\User"
                        }
                    }
                ],
                "profile": {
                    "first_name": "phu994_010",
                    "last_name": "N/A",
                    "gender": 2,
                    "phone_number": "0000000000",
                    "status": 1,
                    "position": null,
                    "address": null,
                    "date_of_birth": "1990-01-01",
                    "utm_source": "",
                    "aff_sid": "",
                    "description": null,
                    "model": null,
                    "utm_medium": "",
                    "utm_campaign": "",
                    "sub1": "",
                    "sub4": ""
                },
                "user_types": [
                    {
                        "id": 3,
                        "name": "PUBLISHER"
                    }
                ],
                "permissions": []
            },
            "access_token": "62b697d9-11a9-48f9-b4f6-a8c8f1419b47",
            "token_type": "bearer",
            "refresh_token": "becfcffd-2d7b-4504-977b-24f6589d6717",
            "expires_in": 35999,
            "scope": "user_info read write",
            "refresh_token_expires_in": 14399,
            "refresh_token_expires_at": "2025-03-06T19:30:49+0000",
            "is_active": true,
            "expires_at": "2025-03-07T01:30:49+0000",
            "user_id": 505419,
            "phone": "0000000000",
            "user_name": "phu994_010",
            "refresh_token_value": "becfcffd-2d7b-4504-977b-24f6589d6717",
            "email": "phu994_010@gmail.com"
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

- **🔢 Parameters:**

| Tham số | Bắt buộc | Kiểu dữ liệu | Mô tả |
|---------|---------|------------|------|
| `X-Network-Id` | ✅ | `integer` | ID của network |
| `X-Port-Type` | ✅ | `string` | Loại port (`PUB`) |
| `Authorization` | ✅ | `string` | Bearer token để xác thực user |
| `X-Network-Token` | ✅ | `string` | Token xác thực network |

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
