# Adapter

## 1. Adapter là gì trong Android Studio?

> Adapter là một thành phần quan trọng trong việc **hiển thị dữ liệu lên các thành phần giao diện người dùng** như ListView, RecyclerView hoặc Spinner. Adapter chịu trách nhiệm liên kết dữ liệu từ nguồn dữ liệu (như một mảng, danh sách, cơ sở dữ liệu, ...) với UI.

Nó đóng vai trò **trung gian giữa dữ liệu và UI**. Cung cấp phương thức để lấy dữ liệu từ nguồn dữ liệu và chuyển đổi nó thành các thành phần giao diện tương ứng. Adapter cũng quản lý việc tái sử dụng các thành phần giao diện để tối ưu hiệu suất và tiết kiệm tài nguyên.

Trong Android, có một số Adapter được cung cấp sẵn như **ArrayAdapter**, **RecyclerView.Adapter** hoặc **BaseAdapter**. Tuy nhiên, bạn cũng có thể tạo Adapter tùy chỉnh của riêng mình bằng cách kế thừa từ các **Adapter class** có sẵn hoặc triển khai các giao diện tương ứng.

## 2. Các loại Adapter trong Android:

- **ArrayAdapter:** Đây là một Adapter sử dụng để liên kết dữ liệu từ một mảng hoặc danh sách với ListView hoặc Spinner. ArrayAdapter chịu trách nhiệm tạo các View cho mỗi item trong danh sách dựa trên một layout đơn giản.
- **RecyclerView.Adapter:** RecyclerView.Adapter cung cấp các phương thức để tạo và tái sử dụng các ViewHolder cho các item trong danh sách.
- **BaseAdapter:** Đây là một lớp cơ sở trừu tượng cho việc tạo Adapter tùy chỉnh. BaseAdapter cung cấp các phương thức cơ bản để liên kết dữ liệu và tạo giao diện cho các item trong danh sách. Bằng cách inherit từ BaseAdapter, bạn có thể tạo một Adapter tùy chỉnh và triển khai các phương thức cần thiết.
- **ListAdapter:** Đây là một Adapter được sử dụng cùng với RecyclerView trong Jetpack's Paging Library. ListAdapter cung cấp tích hợp sẵn để xử lý cập nhật dữ liệu và hiệu suất tốt hơn khi làm việc với danh sách có thay đổi.

## 3. Các bước để tạo Adapter:

### 3.1. Adapter tuỳ chỉnh:

- **Bước 1:** **Tạo một class mới trong dự án Android Studio**. và đặt tên cho nó (ví dụ: CustomAdapter). Class này sẽ inherit từ một class Adapter có sẵn như ArrayAdapter hoặc RecyclerView.Adapter, hoặc triển khai các giao diện tương ứng như ListAdapter hoặc SpinnerAdapter.

```java
public class CustomAdapter extends ArrayAdapter<String> {
    // Các thuộc tính và phương thức tùy chỉnh của Adapter

    public CustomAdapter(Context context, List<String> data) {
        super(context, 0, data);
        // Khởi tạo Adapter với Context và dữ liệu
    }

    @Override
    public View getView(int position, View convertView, ViewGroup parent) {
        // Triển khai phương thức getView để tạo và trả về View cho mỗi item trong danh sách
        // Các xử lý hiển thị dữ liệu và giao diện người dùng
        // convertView là View đã được tạo trước đó có thể được tái sử dụng
        // parent là ViewGroup chứa danh sách các item
        // position là vị trí của item hiện tại trong danh sách
        // ...
        return convertView;
    }
}
```

- **Bước 2:** **Triển khai phương thức getView()** Phương thức getView() là nơi triển khai xử lý hiển thị dữ liệu và tạo giao diện cho mỗi item trong danh sách. Chúng ta có thể sử dụng **LayoutInflater** để tạo View từ một layout XML hoặc tạo View bằng code trong phương thức này. Sau đó, bạn có thể gán dữ liệu từ nguồn dữ liệu vào các thành phần giao diện trong item.
- **Bước 3:** **Sử dụng Adapter** Sau khi tạo Adapter tùy chỉnh, bạn có thể sử dụng nó để liên kết dữ liệu với thành phần giao diện như `ListView` hoặc `RecyclerView`. Đầu tiên, khởi tạo một đối tượng của Adapter và truyền Context và dữ liệu vào constructor. Tiếp theo, gán Adapter cho thành phần giao diện và cập nhật dữ liệu khi cần thiết.

```java
List<String> data = new ArrayList<>();
// Khởi tạo và thêm dữ liệu vào danh sách data

CustomAdapter adapter = new CustomAdapter(context, data);

ListView listView = findViewById(R.id.list_view);
listView.setAdapter(adapter);
```

### 3.2. ArrayAdapter:

- **Bước 1:** **Chuẩn bị dữ liệu** Tạo một danh sách dữ liệu mà bạn muốn hiển thị trong ListView hoặc Spinner. Ví dụ, tạo một danh sách chuỗi:

```java
List<String> data = new ArrayList<>();
data.add("Item 1");
data.add("Item 2");
data.add("Item 3");
// or
String[] data = new String[] {"Item 1", "Item 2", "Item 3"};
```

- **Bước 2:** **Khởi tạo ArrayAdapter** Tạo một object ArrayAdapter, có params là: **Context**, **một layout cho mỗi item trong danh sách** (có thể sử dụng layout có sẵn như android.R.layout.simple_list_item_1), và list hoặc mảng dữ liệu.

```java
ArrayAdapter<String> adapter = new ArrayAdapter<>(context, android.R.layout.simple_list_item_1, data);
```

- **Bước 3:** **Liên kết ArrayAdapter với ListView hoặc Spinner** Tìm và liên kết `ArrayAdapter` với thành phần giao diện `ListView` hoặc `Spinner` trong XML hoặc trong mã Java.

```java
<ListView
    android:id="@+id/list_view"
    android:layout_width="match_parent"
    android:layout_height="match_parent" />
```

Trong mã Java:

```java
ListView listView = findViewById(R.id.list_view);
listView.setAdapter(adapter);
```

- **Bước 4: (Optional)** **Tùy chỉnh hiển thị**: Nếu bạn muốn tùy chỉnh cách hiển thị của mỗi item trong danh sách, bạn có thể tạo một layout tùy chỉnh cho từng item và ghi đè phương thức `getView()` của ArrayAdapter. Trong phương thức getView(), bạn có thể `inflate layout` tùy chỉnh và gán dữ liệu cho các thành phần giao diện.

```java
ArrayAdapter<String> adapter = new ArrayAdapter<String>(context, 0, data) {
    @Override
    public View getView(int position, View convertView, ViewGroup parent) {
        if (convertView == null) {
            convertView = LayoutInflater.from(getContext()).inflate(R.layout.custom_item_layout, parent, false);
        }

        // Gán dữ liệu cho các thành phần giao diện trong convertView

        return convertView;
    }
};
```
