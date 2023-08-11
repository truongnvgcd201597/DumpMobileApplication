```java
CheckBox checkbox = findViewById(R.id.checkbox_id);
checkbox.setOnCheckedChangeListener(new CompoundButton.OnCheckedChangeListener() {
    @Override
    public void onCheckedChanged(CompoundButton buttonView, boolean isChecked) {
        // Xử lý sự kiện khi checkbox được thay đổi trạng thái
        if (isChecked) {
            // Checkbox được chọn
        } else {
            // Checkbox không được chọn
        }
    }
});
```

Trong ví dụ này, khi người dùng nhấn vào nút "Kiểm tra", chúng ta kiểm tra trạng thái của checkbox và hiển thị một thông báo Toast tương ứng.

```java
CheckBox checkbox = findViewById(R.id.checkbox_id);
Button button = findViewById(R.id.button_id);

button.setOnClickListener(new View.OnClickListener() {
    @Override
    public void onClick(View v) {
        if (checkbox.isChecked()) {
            // Checkbox được chọn
            Toast.makeText(MainActivity.this, "Checkbox được chọn", Toast.LENGTH_SHORT).show();
        } else {
            // Checkbox không được chọn
            Toast.makeText(MainActivity.this, "Checkbox không được chọn", Toast.LENGTH_SHORT).show();
        }
    }
});
```
