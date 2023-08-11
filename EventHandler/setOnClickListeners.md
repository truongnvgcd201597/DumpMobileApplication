# setOnClickListeners

## 1. setOnClickListener là gì?

> **setOnClickListener** là một phương thức được sử dụng để **gắn một sự kiện listener tới một View** cụ thể. Nghe sự kiện này có nghĩa là khi người dùng tương tác với View đó, chẳng hạn như nhấn vào nút (Button), sự kiện được gọi và mã được thực thi.

**OnClickListener** cung cấp một đoạn mã (lambda expression hoặc anonymous inner class) để xử lý sự kiện khi nó xảy ra.

```java
Button myButton = findViewById(R.id.my_button);
myButton.setOnClickListener(new View.OnClickListener() {
    @Override
    public void onClick(View v) {
        // Thực thi mã khi người dùng nhấn vào nút
        // Xử lý sự kiện ở đây
    }
});
```

- `new View.OnClickListener()` tạo một object `View.OnClickListener` mới, sử dụng anonymous inner class để triển khai giao diện `View.OnClickListener` và định nghĩa phương thức onClick(View v) bên trong.

Khi người dùng nhấn vào nút `myButton`, phương thức `onClick(View v)` sẽ được gọi tự động và mã xử lý sự kiện bên trong nó sẽ được thực thi. Bạn có thể thay đổi và tuỳ chỉnh mã xử lý sự kiện trong đoạn mã bên trong phương thức `onClick()` để đáp ứng theo yêu cầu của ứng dụng của bạn.
