local_passport_auth_service

Ứng dụng mẫu sử dụng Express + Passport (local strategy) để xác thực người dùng với MongoDB.

## Tổng quan

Project này chứa backend nhỏ dùng để demo xác thực local với Passport.js. Nó dùng:
- Node.js (Express)
- Passport (passport-local)
- Mongoose (MongoDB)
- bcryptjs để băm mật khẩu

## Yêu cầu

- Node.js (khuyến nghị v16+)
- MongoDB (local hoặc URI tới MongoDB Atlas)

## Cài đặt

1. Cài dependencies:

```powershell
npm install
```

2. Cấu hình biến môi trường. Tạo file `.env` (khuyến nghị) hoặc export biến môi trường trước khi chạy app:

Biến phổ biến:
- `MONGO_URI` - connection string tới MongoDB (ví dụ: `mongodb://localhost:27017/mydb`)
- `SESSION_SECRET` - chuỗi bí mật cho express-session
- `PORT` - (tuỳ chọn) port để chạy server (mặc định 3000 nếu không chỉ định)

Ví dụ (PowerShell):

```powershell
$env:MONGO_URI = "mongodb://localhost:27017/mydb"; $env:SESSION_SECRET = "changeme"; $env:PORT = "3000"
node app.js
```

Lưu ý: dự án hiện tại không có package script `start`. Bạn có thể thêm vào `package.json` để dùng `npm start`:

```json
"scripts": {
  "start": "node app.js"
}
```

## Cấu trúc thư mục

- `app.js` - file khởi tạo Express app và cấu hình middleware
- `config/passport.js` - cấu hình Passport local strategy
- `models/User.js` - schema Mongoose cho user
- `routes/auth.js` - route liên quan đến xác thực

## Chạy ứng dụng

1. Đảm bảo MongoDB đang chạy và `MONGO_URI` được cấu hình.
2. Cài dependency `npm install` (xem trên).
3. Chạy server:

```powershell
node app.js
```

Ứng dụng sẽ lắng nghe ở `http://localhost:<PORT>` (mặc định 3000 nếu bạn không đặt `PORT`).

## Lỗi thường gặp

- Kết nối MongoDB thất bại: kiểm tra `MONGO_URI` và đảm bảo MongoDB đang chạy.
- Lỗi session: kiểm tra `SESSION_SECRET` đã được cấu hình.
- Trang đăng nhập/đăng ký trả lỗi 500: kiểm tra log trong console để biết stack trace.

## Mở rộng / Gợi ý

- Thêm `dotenv` để load `.env` tự động (npm i dotenv) và require ở đầu `app.js`.
- Thêm script `start` trong `package.json` để thuận tiện dùng `npm start`.

## License

MIT (tùy chỉnh theo nhu cầu của bạn)
