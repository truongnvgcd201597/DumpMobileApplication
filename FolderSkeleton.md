# Folder Skeleton

## 1. Project folder structure:

Cấu trúc thư mục trong Android Studio thường được tổ chức như sau:

### 1.1. Manifest folder:

Chứa tệp **AndroidManifest.xml**. Tệp này chứa thông tin cấu hình chung và khai báo các thành phần chính của ứng dụng như **Activities**, **Services**, **Broadcast Receivers** và **Content Providers**.
![](https://media.geeksforgeeks.org/wp-content/uploads/20191003195545/manifolder.jpg)

### 1.2. Java folder:

Thư mục này chứa mã nguồn Java của ứng dụng. Đây là nơi bạn viết mã Java **để xây dựng và thực thi các thành phần của ứng dụng** như `Activities`, `Fragments`, `Adapters` và `Utility classes`.
![](https://media.geeksforgeeks.org/wp-content/uploads/20191003195704/javafolder.jpg)

### 1.3 res (Resources):

Tệp này chứa tài nguyên của ứng dụng như `hình ảnh`, `tệp XML`, `chuỗi`, `màu sắc` và `kiểu chữ`.

- **drawable**: Chứa các tệp hình ảnh và các tệp XML định nghĩa các hình ảnh.
- **layout**: Chứa các tệp XML định nghĩa giao diện người dùng (layout) của ứng dụng.
- **mipmap**: Chứa các biểu tượng ứng dụng với các kích thước khác nhau.
- **values**: Chứa các tệp XML định nghĩa các tài nguyên giá trị như chuỗi, màu sắc, kích thước, v.v.

![](https://media.geeksforgeeks.org/wp-content/uploads/20191003195916/resfolder.jpg)

### 1.4 Gradle Scripts:

Chứa tệp cấu hình Gradle cho dự án và các mô-đun của nó.

- **build.gradle (Project)**: Định nghĩa cấu hình chung cho dự án, bao gồm phiên bản SDK, các thư viện bên thứ ba, và các cài đặt khác liên quan đến dự án.
- **build.gradle (Module)**: Định nghĩa cấu hình cho mỗi mô-đun trong dự án, bao gồm phiên bản SDK, các phụ thuộc và các cài đặt khác của mô-đun.

Đây là cấu trúc thư mục cơ bản trong một dự án Android Studio. Tuy nhiên, có thể có thêm các thư mục và tệp khác tùy thuộc vào tính chất và yêu cầu cụ thể của dự án.

![](https://media.geeksforgeeks.org/wp-content/uploads/20191003200004/gradlefolder.jpg)
