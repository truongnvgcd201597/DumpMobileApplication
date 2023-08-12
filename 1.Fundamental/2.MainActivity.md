# MainActivity

## onCreate()

> onCreate() là một phương thức quan trọng trong lớp Activity của ứng dụng Android. Nó **được gọi khi một Activity được tạo ra hoặc khôi phục sau khi bị hủy**. Hàm onCreate() có chức năng chính để khởi tạo giao diện người dùng và thực hiện các tác vụ khởi đầu liên quan đến Activity.

```java
 @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }
```
