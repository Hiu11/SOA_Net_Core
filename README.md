

# Dự Án API Quản Lý Sách và Dữ Liệu với MongoDB

## Tổng Quan Dự Án

Dự án này xây dựng một dịch vụ web RESTful sử dụng **ASP.NET Core** kết nối với cơ sở dữ liệu **MongoDB** để quản lý các cuốn sách. API cung cấp các chức năng CRUD (Create, Read, Update, Delete) cho phép người dùng thực hiện các thao tác trên dữ liệu sách. Mô hình này dễ dàng mở rộng và bảo trì, phù hợp cho các ứng dụng nhỏ và vừa, cũng như các microservices.

Dự án này cũng ứng dụng **Swagger** để tự động tạo tài liệu API và hỗ trợ kiểm thử trực tiếp trên trình duyệt, tạo điều kiện thuận lợi cho quá trình phát triển và kiểm tra API.

## Các Thành Phần Chính

### 1. **Model**

- **Book**: Mô hình đại diện cho cuốn sách, bao gồm các thuộc tính:
  - `Id`: ID duy nhất của cuốn sách, được sử dụng kiểu **ObjectId** của MongoDB.
  - `BookName`: Tên cuốn sách.
  - `Price`: Giá của cuốn sách.
  - `Category`: Thể loại của cuốn sách.
  - `Author`: Tác giả của cuốn sách.
  
- **BookStoreDatabaseSettings**: Cấu hình kết nối MongoDB, bao gồm các trường:
  - `ConnectionString`: Chuỗi kết nối MongoDB.
  - `DatabaseName`: Tên cơ sở dữ liệu MongoDB.
  - `BooksCollectionName`: Tên bộ sưu tập sách trong cơ sở dữ liệu.

### 2. **Controller**

- **BooksController** cung cấp các API để thao tác với sách:
  - **GET /items**: Lấy danh sách tất cả các sách từ cơ sở dữ liệu.
  - **GET /items/{id}**: Lấy thông tin chi tiết một cuốn sách theo ID.
  - **POST /items**: Thêm một cuốn sách mới vào cơ sở dữ liệu.
  - **PUT /items/{id}**: Cập nhật thông tin một cuốn sách theo ID.
  - **DELETE /items/{id}**: Xóa một cuốn sách theo ID.

### 3. **Service**

- **BooksService** chứa các phương thức thao tác với cơ sở dữ liệu MongoDB, bao gồm:
  - `GetAsync`: Lấy tất cả các sách hoặc một cuốn sách theo ID.
  - `CreateAsync`: Tạo một cuốn sách mới.
  - `UpdateAsync`: Cập nhật thông tin cuốn sách theo ID.
  - `RemoveAsync`: Xóa cuốn sách khỏi cơ sở dữ liệu.

### 4. **Cấu Hình MongoDB**

Cấu hình kết nối MongoDB được lưu trong tệp `appsettings.json`:
```json
"BookStoreDatabase": {
  "ConnectionString": "mongodb://localhost:27017",
  "DatabaseName": "BookStore",
  "BooksCollectionName": "Books"
}
```

Đảm bảo MongoDB đã được cài đặt và đang chạy trên máy chủ của bạn. Cấu hình này sẽ giúp ứng dụng kết nối và thao tác với cơ sở dữ liệu MongoDB để lưu trữ dữ liệu sách.

## Các Tính Năng API

Dưới đây là các endpoint API được triển khai:

| HTTP Method | Endpoint            | Mô tả                              |
|-------------|---------------------|-------------------------------------|
| GET         | `/items`            | Lấy danh sách tất cả các sách       |
| GET         | `/items/{id}`       | Lấy thông tin chi tiết theo ID     |
| POST        | `/items`            | Tạo một cuốn sách mới              |
| PUT         | `/items/{id}`       | Cập nhật thông tin cuốn sách theo ID|
| DELETE      | `/items/{id}`       | Xóa một cuốn sách theo ID          |

## 🚀 Hướng Dẫn Cài Đặt và Chạy

### 1. **Clone repository**:

   ```bash
[
](https://github.com/Hiu11/SOA_Net_Core)   ```

### 2. **Cài đặt các thư viện cần thiết**:

Điều hướng vào thư mục dự án và chạy lệnh sau để cài đặt các gói NuGet:

```bash
dotnet restore
```

### 3. **Cấu hình MongoDB**:

Mở tệp `appsettings.json` và chỉnh sửa thông tin kết nối MongoDB:

```json
{
  "MongoDB": {
    "ConnectionString": "mongodb://localhost:27017",
    "DatabaseName": "YourDatabaseName"
  }
}
```

Đảm bảo rằng MongoDB đã được cài đặt và đang chạy trên máy chủ của bạn.

### 4. **Chạy ứng dụng**:

```bash
dotnet run
```

### 5. **Kiểm tra API**:

Mở trình duyệt và truy cập tài liệu Swagger tại:

```
http://localhost:<port>/swagger
```

Swagger cho phép bạn dễ dàng kiểm tra và tương tác trực tiếp với API, giúp việc phát triển và kiểm thử trở nên thuận tiện hơn.

## 🛠️ Công Nghệ Sử Dụng

- **ASP.NET Core**: Framework chính để xây dựng dịch vụ web.
- **MongoDB.Driver**: Thư viện giúp kết nối và thao tác với MongoDB.
- **Swagger**: Công cụ tự động tạo tài liệu API và kiểm thử các endpoint.
  
## 🛡️ Bảo Mật

Đảm bảo sử dụng kết nối an toàn với MongoDB khi triển khai trên môi trường sản xuất. Cấu hình tường lửa và các biện pháp bảo mật khác để bảo vệ cơ sở dữ liệu khỏi các truy cập trái phép.

## Kết Quả Đạt Được

- **API Hoạt Động**: Tất cả các endpoint API hoạt động như mong đợi, cho phép quản lý sách từ cơ sở dữ liệu MongoDB thông qua các phương thức GET, POST, PUT, DELETE.
  
- **Tương Tác Cơ Sở Dữ Liệu**: Kết nối thành công với MongoDB để thực hiện các thao tác CRUD.

- **Swagger**: Tạo tài liệu API tự động và cho phép thử nghiệm các API trực tiếp trên trình duyệt, giúp việc kiểm tra và phát triển thuận tiện hơn.

