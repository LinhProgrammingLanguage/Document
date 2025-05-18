# Ngôn Ngữ Lập Trình Linh (Tinh Linh Lang)
https://Linh.kesug.com
## Giới Thiệu

**Linh (Tinh Linh Lang)** là một ngôn ngữ lập trình mới, được thiết kế với mục tiêu kết hợp sự linh hoạt của các ngôn ngữ kịch bản động với sự an toàn và rõ ràng của các gợi ý kiểu tùy chọn từ ngôn ngữ tĩnh. Linh hướng đến cú pháp quen thuộc, dễ học và dễ sử dụng, lấy cảm hứng từ các ngôn ngữ phổ biến như C, Java, JavaScript và Python.

Tên "Tinh Linh Lang" gợi ý sự nhẹ nhàng, uyển chuyển và thông minh trong thiết kế của ngôn ngữ.

## Đặc Điểm Chính

*   **Kiểu Dữ Liệu Giả Tĩnh + Động:** Linh hoạt trong việc xử lý kiểu dữ liệu, cho phép khai báo biến động hoàn toàn (`var`) hoặc biến có kiểu cố định sau khi khởi tạo (`let`, `const`) với gợi ý kiểu tùy chọn.
*   **Không `null` hay `undefined`:** Để tăng cường độ an toàn và giảm lỗi, Linh loại bỏ khái niệm `null` và `undefined`. Thay vào đó, các biến chưa được gán giá trị tường minh (nhưng có khai báo kiểu) sẽ nhận "giá trị zero" của kiểu đó.
*   **Cơ Chế Hoạt Động:** Mã nguồn Linh được biên dịch thành bytecode bởi trình biên dịch LinhC và chạy trên Máy Ảo Linh (LiVM). Điều này mang lại khả năng di động và hiệu suất tốt hơn so với thông dịch thuần túy, trong khi vẫn giữ được cảm giác của một ngôn ngữ thông dịch cho người dùng cuối.
*   **Cú Pháp Quen Thuộc:** Ngữ pháp và cấu trúc lệnh thuộc nhóm C (C/C++, Java, JavaScript), giúp việc học và chuyển đổi từ các ngôn ngữ khác trở nên dễ dàng hơn.
*   **Từ Khóa Tiếng Anh Ngắn Gọn:** Các từ khóa được chuẩn hóa bằng tiếng Anh và có độ dài tối đa 6 ký tự.
*   **Nhập/Xuất Tích Hợp:** Các hàm `print()` và `input()` được tích hợp sẵn mà không cần import thư viện.

## Cài Đặt
vui lòng chờ chúng tôi hoàn thành

## Bắt Đầu

### Hello, Linh!

Tạo một tệp tin có tên `hello.li` (hoặc `hello.linh`):

```linh
// file: hello.ln
print("Hello, Tinh Linh Lang!");
```

Chạy từ dòng lệnh (giả sử đã cài đặt `linh`):

```bash
linh hello.li
```

Kết quả:
```
Hello, Tinh Linh Lang!
```

## Cú Pháp Cơ Bản

### 1. Khai Báo Biến

Linh sử dụng ba từ khóa để khai báo biến: `var`, `let`, và `const`. Tất cả đều tuân theo phạm vi khối (block scope `{...}`).

| Từ khóa | Thay đổi Giá Trị | Thay đổi Kiểu Dữ Liệu | Mô tả                                                                 |
| :------- | :--------------- | :-------------------- | :-------------------------------------------------------------------- |
| `var`    | Có               | Có                    | Biến động hoàn toàn. Có thể thay đổi cả giá trị và kiểu sau khi khai báo. |
| `let`    | Có               | Không                 | Biến giả tĩnh. Giá trị có thể thay đổi, nhưng kiểu phải giữ nguyên.    |
| `const`  | Không            | Không                 | Hằng số. Giá trị và kiểu không thể thay đổi sau khi khởi tạo.          |

**Ví dụ:**

```linh
var score = 90;
score = 95;      // OK
score = "Excellent";  // OK, 'var' cho phép thay đổi kiểu

let retry_count = 3;
retry_count = 4; // OK
// retry_count = "Four"; // LỖI! 'let' không cho thay đổi kiểu

const PI_VALUE = 3.14159;
// PI_VALUE = 3.14; // LỖI! 'const' không cho thay đổi giá trị
```

**Suy luận kiểu:** Nếu không chỉ định kiểu, Linh sẽ tự suy luận từ giá trị khởi tạo.

```linh
let user_name = "Alice"; // Suy luận là str
var current_age = 30;     // Suy luận là int (ban đầu)
```

**Khai báo với kiểu và Giá trị Zero:** Nếu chỉ định kiểu mà không có giá trị khởi tạo, biến sẽ nhận "giá trị zero" của kiểu đó.

```linh
let quantity: int;     // quantity = 0
var message_text: str;    // message_text = ""
const IS_ACTIVATED: bool; // IS_ACTIVATED = false
```

**Lưu ý:** Khai báo biến chỉ với tên mà không có kiểu hoặc giá trị khởi tạo sẽ gây lỗi.
```linh
// var some_error_var; // LỖI!
```

**Kiểu Kết Hợp (Union Types):** Cho phép biến hoặc hàm có thể thuộc một trong nhiều kiểu.

```linh
let item_id :<str, int> = 101;
item_id = "ITEM-102"; // Hợp lệ

func get_data_value(is_numeric: bool): <str, int> {
    if (is_numeric) {
        return 123;
    } else {
        return "String data";
    }
}
```

### 2. Kiểu Dữ Liệu

Linh không có `null` hay `undefined`. Thay vào đó, nó sử dụng khái niệm **giá trị zero** cho các kiểu dữ liệu khi không có giá trị khởi tạo cụ thể.

**Kiểu Dữ Liệu Cơ Bản:**

| Kiểu    | Mô tả                                     | Giá trị Zero | Ví dụ Literal          |
| :------ | :---------------------------------------- | :----------- | :--------------------- |
| `bool`  | Logic (đúng/sai)                          | `false`      | `true`, `false`        |
| `int`   | Số nguyên 64-bit có dấu (mặc định)        | `0`          | `10`, `-5`             |
| `int<N>`| Số nguyên N-bit có dấu (N=8,16,32,64)    | `0`          |                        |
| `uint`  | Số nguyên 64-bit không dấu (mặc định)     | `0`          | `100`, `0`             |
| `uint<N>`| Số nguyên N-bit không dấu (N=8,16,32,64) | `0`          |                        |
| `float` | Số thực 64-bit (mặc định)                | `0.0`        | `3.14`, `-0.5`         |
| `float<N>`| Số thực N-bit (N=32,64)                 | `0.0`        |                        |
| `str`   | Chuỗi ký tự Unicode                       | `""`         | `"text"`, `'text'`, `` `&{variable_name}` `` |

**Kiểu Dữ Liệu Đối Tượng:**

| Kiểu                          | Mô tả                                                     | Giá trị Zero | Ví dụ Literal     |
| :---------------------------- | :-------------------------------------------------------- | :----------- | :---------------- |
| `Map<K, V>`                   | Ánh xạ khóa-giá trị (Mặc định `Map<any, any>`)           | `{}`         | `{"key": value}`  |
| `Array`                       | Mảng động, hỗn hợp kiểu (ngầm là `Array<any>`)           | `[]`         | `[1, "two", true]`|
| `Type[]`                      | Mảng đồng nhất kiểu `Type`                                | `[]`         | `[1, 2, 3]` (nếu `int[]`) |

**Kiểu Dữ Liệu Đặc Biệt (Không dùng để khai báo biến trực tiếp):**

*   **`void`:** Chỉ dùng làm kiểu trả về của hàm khi hàm không trả về giá trị nào.
*   **`any`:** Đại diện cho "bất kỳ kiểu nào". Chỉ dùng trong khai báo generic của `Map`, `Array`, hoặc làm kiểu tham số/trả về của hàm khi cần sự linh hoạt tối đa. **Không thể khai báo `var tên: any;`**.

### 3. Quy Tắc Đặt Tên (Identifiers)

*   Chỉ sử dụng chữ cái tiếng Anh (`a-z`, `A-Z`), chữ số (`0-9`), và dấu gạch dưới (`_`).
*   Tên không được bắt đầu bằng chữ số.
*   Không sử dụng các ký tự đặc biệt khác hoặc chữ tiếng Việt có dấu.
    ```linh
    let player_score = 1000; // Hợp lệ
    // var product-code = "P001"; // LỖI
    ```

### 4. Từ Khóa (Keywords)

*   Tất cả từ khóa đều bằng tiếng Anh và có độ dài tối đa 6 ký tự.
*   Ví dụ: `var`, `let`, `const`, `if`, `else`, `for`, `while`, `func`, `return`, `true`, `false`, `int`, `str`, `bool`, `float`, `map`, `array`, `void`, `input`, `print`.

### 5. Hàm (Functions)

```linh
func function_name(param1: type1, param2: type2): return_type {
  // function body
  return value; // if return_type is not void
}
```

**Ví dụ:**
```linh
// Hàm cộng hai số nguyên
func add_numbers(a: int, b: int): int {
  return a + b;
}

// Hàm không trả về giá trị
func display_greeting(greeting_message: str): void {
  print(greeting_message);
}

// Hàm trả về kiểu kết hợp
func get_information_by_id(id_value: int): <str, bool> {
  if (id_value > 0) {
    return "Valid ID";
  } else {
    return false;
  }
}

let sum_result = add_numbers(5, 3); // 8
display_greeting("Hello from Linh!");
```

### 6. Nhập/Xuất (I/O)

Các hàm I/O cơ bản được tích hợp sẵn.

*   **`print(...)`**: In giá trị ra console.
    ```linh
    let current_age = 25;
    print("Your age is:", current_age); // Output: Your age is: 25
    print(1, "two", 3.0, false);   // Output: 1 two 3 false
    ```

*   **`input(variable_ref)`**: Đọc dữ liệu từ console và gán vào `variable_ref`. Linh sẽ cố gắng chuyển đổi chuỗi nhập vào sang kiểu của `variable_ref`.
    ```linh
    var input_name: str;
    var input_age: int;

    print("Enter your name: ");
    input(input_name);

    print("Enter your age: ");
    input(input_age); // Sẽ gây lỗi runtime nếu nhập không phải là số nguyên

    print("Hello &{input_name}, you are &{input_age} years old.");
    ```

### 7. Toán Tử

Linh hỗ trợ các toán tử số học, so sánh, logic quen thuộc giống như trong C/Java/JavaScript.
*   Số học: `+`, `-`, `*`, `/`, `%`
*   So sánh: `==`, `!=`, `>`, `<`, `>=`, `<=`
*   Logic: `&&` (và), `||` (hoặc), `!` (phủ định)

### 8. Cấu Trúc Điều Khiển

Linh sử dụng các cấu trúc điều khiển phổ biến:
*   `if (condition) { ... } else if (other_condition) { ... } else { ... }`
*   `while (condition) { ... }`
*   `for (initializer; condition; step) { ... }` (C-style for loop)
*   `for (element in collection) { ... }` (for-in/for-of style, cần định nghĩa rõ hơn cho Map và Array)

### 9. Chú Thích (Comments)

```linh
// This is a single-line comment

/*
  This is a
  multi-line
  comment.
*/
```

## Một Ví dụ Đầy Đủ Hơn

Chương trình tìm người dùng theo ID, yêu cầu người dùng cung cấp giá trị mặc định nếu không tìm thấy để tránh `null`.

```linh
// User data type assumption (could be a Map)
// let user_template: Map<str, any> = {"id": 0, "name": "", "is_active": false};

let user_database: Map<int, Map<str, any>> = {
    101: { "id": 101, "name": "Alice", "is_active": true },
    102: { "id": 102, "name": "Bob", "is_active": false }
};

// Function to find a user, requires a default value
func find_user_by_id(search_id: int, default_user: Map<str, any>): Map<str, any> {
    // Assume Map has a .has_key() method or similar
    if (user_database.has_key(search_id)) { // Replace with actual key check method
        return user_database[search_id];
    } else {
        return default_user;
    }
}

let guest_user_profile: Map<str, any> = { "id": 0, "name": "Guest", "is_active": false };

let found_user1 = find_user_by_id(101, guest_user_profile);
print("Found (ID 101): Name - ", found_user1["name"]); // Output: Alice

let not_found_user = find_user_by_id(999, guest_user_profile);
print("Not found (ID 999): Name - ", not_found_user["name"]); // Output: Guest

// User can also provide a different default object inline
let found_user2 = find_user_by_id(102, { "id": -1, "name": "Unknown", "is_active": false });
print("Found (ID 102): Name - ", found_user2["name"]); // Output: Bob
```

## Cơ Chế Hoạt Động

1.  **Mã Nguồn Linh (`.linh`) hoặc (`.li`):** Người dùng viết mã bằng cú pháp Linh.
2.  **Trình Biên Dịch Linh (LinhC):**
    *   Phân tích cú pháp và ngữ nghĩa.
    *   Thực hiện kiểm tra kiểu tùy chọn.
    *   Biên dịch mã nguồn thành **Linh Bytecode**.
3.  **Máy Ảo Linh (LiVM):**
    *   Nạp và thực thi Linh Bytecode.
    *   Quản lý bộ nhớ (Garbage Collection).
    *   Cung cấp API runtime.
---
