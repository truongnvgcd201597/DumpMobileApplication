# Alert Dialog

## 1. Định nghĩa:

> AlertDialog trong Android Studio là một thành phần giao diện người dùng (UI) được sử dụng để hiển thị một hộp thoại thông báo cho người dùng. Nó giúp bạn thông báo cho người dùng về các sự kiện, cảnh báo, hoặc yêu cầu thông tin bổ sung.

AlertDialog có thể chứa tiêu đề, nội dung và các nút (button) để người dùng tương tác. Bạn có thể tạo các loại AlertDialog khác nhau, bao gồm:

- Alert Dialog Notification: Hiển thị một thông báo cho người dùng mà không yêu cầu hành động từ phía người dùng.
- Alert Dialog Prompt: Yêu cầu người dùng nhập một số liệu hoặc thực hiện một hành động nào đó. Thường có một hoặc hai nút, ví dụ: "Đồng ý" và "Hủy".
- Alert Dialog Input: Yêu cầu người dùng nhập thông tin hoặc dữ liệu bổ sung. Thường có các trường nhập liệu (EditText) và các nút như "Lưu" và "Hủy".

Bạn có thể tạo AlertDialog trong Android Studio bằng cách sử dụng lớp AlertDialog.Builder. Đầu tiên, bạn cần tạo một đối tượng AlertDialog.Builder và cấu hình nó bằng cách thiết lập tiêu đề, nội dung, các nút và các thuộc tính khác. Sau đó, bạn có thể gọi phương thức .create() để tạo đối tượng AlertDialog từ AlertDialog.Builder và gọi phương thức .show() để hiển thị nó.

## 2. Các phương thức của AlertDialog:

- Tiêu đề (Title): **setTitle()** Thiết lập tiêu đề của AlertDialog.
- Nội dung (Message): **setMessage()**: Thiết lập nội dung của AlertDialog.
- Nút tích cực (Positive Button): **setPositiveButton()** Thiết lập nút tích cực và xử lý sự kiện khi người dùng nhấn vào nút này.

- Nút tiêu cực (Negative Button): **setNegativeButton()** Thiết lập nút tiêu cực và xử lý sự kiện khi người dùng nhấn vào nút này.

- Nút trung tính (Neutral Button): **setNeutralButton()** Thiết lập nút trung tính và xử lý sự kiện khi người dùng nhấn vào nút này.

- Hủy bỏ khi chạm ngoài (Cancelable): **setCancelable()** Thiết lập trạng thái cho phép hủy bỏ AlertDialog bằng cách chạm vào bên ngoài của nó.

- Giao diện tùy chỉnh (Custom Interface): **setView()** Thiết lập một giao diện tùy chỉnh cho AlertDialog, cho phép bạn tạo giao diện theo ý muốn.

- Định dạng màu sắc (Color Formatting): Các phương thức như setTitleColor(), setMessageColor(), setButtonColor(), vv., cho phép bạn thiết lập màu sắc cho các phần khác nhau của AlertDialog.

- Hình ảnh (Icon): **setIcon()** Thiết lập biểu tượng (icon) cho AlertDialog.

## 3. Ví dụ:

Dưới đây là một ví dụ về cách tạo và hiển thị AlertDialog đơn giản trong Android Studio:

```java
AlertDialog.Builder builder = new AlertDialog.Builder(this);
builder.setTitle("Thông báo");
builder.setMessage("Đây là nội dung thông báo.");

builder.setPositiveButton("Đồng ý", new DialogInterface.OnClickListener() {
    @Override
    public void onClick(DialogInterface dialogInterface, int i) {
        // Xử lý sự kiện khi người dùng nhấn nút "Đồng ý"
    }
});

builder.setNegativeButton("Hủy", new DialogInterface.OnClickListener() {
    @Override
    public void onClick(DialogInterface dialogInterface, int i) {
        // Xử lý sự kiện khi người dùng nhấn nút "Hủy"
    }
});

builder.setNeutralButton("Bỏ qua", new DialogInterface.OnClickListener() {
    @Override
    public void onClick(DialogInterface dialogInterface, int i) {
        // Xử lý sự kiện khi người dùng nhấn nút "Bỏ qua"
    }
});

AlertDialog alertDialog = builder.create();
alertDialog.show();
```

```java
public class MainActivity extends AppCompatActivity {

    // DatePicker Fragment inside MainActivity
    public static class DatePickerFragment extends DialogFragment implements
    {
        // ...
    }


    public  void updateDOB(LocalDate dob){
        // ...
    }
    // Define variables to reference the layout
    EditText nameInput;
    EditText emailInput;
    EditText phoneInput;
    Spinner sp;
    String workStatus;
    Button submitBtn;

    // Define function getInputs() to get values from inputs
    private void getInputs(){
        nameInput = findViewById(R.id.name_input);
        emailInput = findViewById(R.id.email_input);
        phoneInput = findViewById(R.id.phone_input);

        String name = nameInput.getText().toString();
        String email = emailInput.getText().toString();
        String phone = phoneInput.getText().toString();
        workStatus = sp.getSelectedItem().toString();

        // Use function displayNextAlert to display an AlertDialog
        displayNextAlert(name, phone, email, workStatus);
    }

    public void displayNextAlert(String name, String phone, String email, String workStatus){
        new AlertDialog.Builder(this)
                .setTitle("Details Entered")
                .setMessage(
                        "Details: \n" +
                                name + "\n" +
                                phone + "\n" +
                                email + "\n" +
                                workStatus
                        )
                .setNeutralButton("Back", new DialogInterface.OnClickListener() {
                    @Override
                    public void onClick(DialogInterface dialogInterface, int i) {

                    }
                })
                .show();
    }
    TextView dobControl;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        // ...

        // Refer the Spinner from the layout
        sp = findViewById(R.id.spinner);

        // Refer the button from the layout
        submitBtn = findViewById(R.id.submit_btn);

        // Adding behavior to the button
        submitBtn.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                getInputs();
            }
        });
    }
}
```
