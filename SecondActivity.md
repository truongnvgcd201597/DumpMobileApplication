# Second Activity

## 1. 2nd Activity là gì?

> 2nd activity đề cập đến một activity thứ hai được tạo ra trong một ứng dụng Android. Activity là một thành phần chính trong phát triển ứng dụng Android và đại diện cho một màn hình hoặc một giao diện người dùng trong ứng dụng.

Thông thường, activity đầu tiên (còn được gọi là MainActivity) được khởi động khi ứng dụng được mở lần đầu tiên. Tuy nhiên, trong một số trường hợp, bạn có thể muốn khởi động một activity thứ hai để hiển thị nội dung hoặc chức năng khác.

Khi bạn muốn chuyển từ activity hiện tại sang activity thứ hai, bạn có thể sử dụng **Intent** và phương thức **startActivity()** để khởi chạy activity thứ hai.

## 2. Các bước khởi tạo 2nd Activity:

- Thiết kế giao diên cho activity thứ hai:

  - Mở file layout activity_second.xml (hoặc tên file layout tương ứng) trong thư mục **res/layout**.
  - Thiết kế giao diện người dùng cho activity thứ hai bằng cách kéo và thả các view từ `Palette` vào `layout`.
  - Tùy chỉnh giao diện bằng cách sửa đổi thuộc tính của các view trong file XML.

- Khởi chạy 2nd activity từ activity chính:

  - Trong activity chính, ví dụ `MainActivity`, tìm phương thức **onCreate()** và tìm dòng **setContentView(R.layout.activity_main)**.
  - Dưới dòng **setContentView()**, thêm đoạn mã sau để tạo một **Intent** và khởi chạy 2nd activity:

  ```java
   // Tạo một Intent để khởi chạy activity thứ hai
    Intent intent = new Intent(MainActivity.this,    SecondActivity. class);
    // Khởi chạy activity thứ hai
   startActivity(intent);
  ```

  `MainActivity.this` **đại diện cho context của activity hiện tại**, và `SecondActivity.class` là lớp của activity thứ hai mà bạn đã tạo.

  Bây giờ, khi activity chính được khởi chạy, nó sẽ tự động khởi chạy activity thứ hai thông qua Intent.

- Tùy chỉnh activity thứ hai:

  - Trong `SecondActivity`, tìm phương thức **onCreate()** và tìm dòng **setContentView(R.layout.activity_second)**.
  - Ta có thể thêm các thành phần như TextView, Button, ImageView, vv. vào layout `activity_second.xml` và thao tác với chúng trong **SecondActivity.java** bằng cách sử dụng phương thức **findViewById()**.

  `Lưu ý: Để quay trở lại activity gốc từ activity thứ hai, bạn có thể sử dụng phương thức finish() trong SecondActivity.`

## 3. Ví dụ:

![](https://github.com/vinhhn3/comp1786-L2-android-basics/raw/add-2nd-activity/img_2.png)
![](https://github.com/vinhhn3/comp1786-L2-android-basics/raw/add-2nd-activity/img_3.png)
![](https://github.com/vinhhn3/comp1786-L2-android-basics/raw/add-2nd-activity/img_4.png)

Thêm activity thứ hai vào ứng dụng Android, `NameDisplay` được thêm:
![](https://github.com/vinhhn3/comp1786-L2-android-basics/raw/add-2nd-activity/img_5.png)

Chúng ta sẽ thêm layout của activity `NameDisplay` vào `activity_name_display.xml`:

```java
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".NameDisplay">

    <TextView
        android:id="@+id/name_display"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Name Display"
        android:textSize="20sp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />
</androidx.constraintlayout.widget.ConstraintLayout>
```

Sau đó, thực hiện chỉnh sửa **MainActivity.java** để có thể gửi giá trị `name` từ **MainActivity** sang **NameDisplay**:

```java
public class MainActivity extends AppCompatActivity {
    TextView nameLabel;
    EditText nameField;
    Button buttonSubmit;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        nameLabel = findViewById(R.id.name_label);
        nameField = findViewById(R.id.name_input);
        buttonSubmit = findViewById(R.id.button_submit);
        Intent i = new Intent(this, NameDisplay.class);

        buttonSubmit.setOnClickListener(new View.OnClickListener() {

            @Override
            public void onClick(View view) {
                String name = nameField.getText().toString();
                // Put the name into the intent as extra
                i.putExtra(NameDisplay.NAME, name);

                startActivity(i);
            }
        });
    }
}
```

Tại `NameDisplay.java`, chúng ta sẽ nhận được giá trị `name` từ `extras` của `Intent` và hiển thị nó lên `TextView`:

```java
public class NameDisplay extends AppCompatActivity {
    public static final String NAME = "name";
    TextView nameDisplay;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_name_display);

        // Reference from the layout
        nameDisplay = findViewById(R.id.name_display);

        // Get the extras of the current activity
        Bundle extras = getIntent().getExtras();

        // If extra is display, display ERROR with color RED
        if (extras == null) {
            nameDisplay.setTextColor(Color.RED);
            nameDisplay.setText("ERROR ...");
            return;
        }

        // Get the value from extras
        String name = extras.getString(NAME);

        // If name is empty, display Error with color RED
        if (name.trim().isEmpty()) {
            nameDisplay.setTextColor(Color.RED);
            nameDisplay.setText("Name should not be empty");
            return;
        }

        // Display name with color BLUE
        nameDisplay.setTextColor(Color.BLUE);
        nameDisplay.setText("Hello " + name);
    }
}
```
