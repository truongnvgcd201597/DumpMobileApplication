# Toast trong Android Studio:

## 1. Toast là gì?

> Toast là một **cách để hiển thị thông báo ngắn tạm thời trên màn hình thiết bị di động**. Nó thường được sử dụng để thông báo cho người dùng về một hành động đã được thực hiện hoặc một thông tin quan trọng.

Toast hiển thị một hộp thoại nhỏ tạm thời, thường hiển thị dưới dạng một văn bản ngắn và tự động biến mất sau khoảng thời gian ngắn. Nó không yêu cầu sự tương tác từ người dùng và không gây gián đoạn quá nhiều trong quá trình sử dụng ứng dụng.

Bạn có thể tạo một Toast bằng cách sử dụng lớp Toast và phương thức tĩnh makeText() trong Android Studio. Dưới đây là một ví dụ đơn giản:

```java
Toast.makeText(MainActivity.this, "Đây là một thông báo Toast", Toast.LENGTH_SHORT).show();
```

- **MainActivity.this:** Tham chiếu đến hoạt động hiện tại hoặc ngữ cảnh hiện tại.
- **"Đây là một thông báo Toast":** Nội dung văn bản của Toast.
- **Toast.LENGTH_SHORT:** Thời gian hiển thị của Toast (ngắn). Bạn cũng có thể sử dụng Toast.LENGTH_LONG cho thời gian hiển thị lâu hơn.
- **show():** Phương thức cuối cùng để hiển thị Toast lên màn hình.
