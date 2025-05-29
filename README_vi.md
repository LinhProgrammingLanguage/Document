# Ngôn Ngữ Lập Trình Linh (Tinh Linh Lang)

Trang web chính thức: https://linh.kesug.com/

## Giới Thiệu

**Linh (Tinh Linh Lang)** là một ngôn ngữ lập trình mới, được thiết kế với mục tiêu kết hợp sự linh hoạt của các ngôn ngữ kịch bản động với sự an toàn và rõ ràng của các gợi ý kiểu tùy chọn từ ngôn ngữ tĩnh. Linh hướng đến cú pháp quen thuộc, dễ học và dễ sử dụng, lấy cảm hứng từ các ngôn ngữ phổ biến như C, Java, JavaScript và Python. Mục tiêu chính của Linh là cung cấp một môi trường phát triển mạnh mẽ và đáng tin cậy, giảm thiểu các lỗi phổ biến liên quan đến kiểu dữ liệu và trạng thái biến, đồng thời duy trì hiệu suất tốt.

Tên "Tinh Linh Lang" gợi ý sự nhẹ nhàng, uyển chuyển và thông minh trong thiết kế của ngôn ngữ, phản ánh khả năng thích ứng cao và cách tiếp cận tinh tế trong việc giải quyết các thách thức lập trình hiện đại. Với Linh, các nhà phát triển có thể xây dựng các ứng dụng từ quy mô nhỏ đến lớn một cách tự tin và hiệu quả.

## Đặc Điểm Chính

* **Kiểu Dữ Liệu Giả Tĩnh + Động:** Linh mang đến sự linh hoạt đáng kể trong việc xử lý kiểu dữ liệu, cho phép bạn lựa chọn giữa khai báo biến động hoàn toàn (`var`) hoặc biến có kiểu cố định sau khi khởi tạo (`let`, `const`) với gợi ý kiểu tùy chọn. Điều này cho phép lập trình viên tận dụng sự tiện lợi của kiểu động trong các kịch bản nhanh chóng, đồng thời hưởng lợi từ sự an toàn và khả năng tối ưu hóa của kiểu tĩnh trong các phần mã quan trọng, giúp phát hiện lỗi sớm hơn trong quá trình phát triển.

* **Không `null` hay `undefined`:** Để tăng cường độ an toàn và giảm thiểu các lỗi runtime phổ biến, Linh loại bỏ hoàn toàn khái niệm `null` và `undefined` truyền thống. Thay vào đó, Linh sử dụng một hệ thống hai cấp độ rõ ràng và không mơ hồ cho các giá trị vắng mặt, đảm bảo mọi biến luôn ở trạng thái xác định:

    * **Giá trị Zero (Zero Value):** Khi một biến được khai báo với một kiểu dữ liệu cụ thể (ví dụ: `int`, `str`, `bool`) nhưng không được gán giá trị khởi tạo tường minh, nó sẽ tự động nhận "giá trị zero" mặc định của kiểu đó. Đây là các giá trị *hợp lệ và có ý nghĩa* của kiểu dữ liệu tương ứng, không phải là một trạng thái "chưa xác định". Ví dụ, `0` cho `int`, `""` (chuỗi rỗng) cho `str`, và `false` cho `bool`. Điều này giúp tránh việc truy cập vào các giá trị không xác định và cung cấp một điểm khởi đầu an toàn cho mọi biến.

    * **`uninit`:** Là một kiểu dữ liệu và đồng thời là một giá trị đặc biệt, `uninit` đại diện cho trạng thái *chưa được khởi tạo có ý nghĩa*. Khác với các giá trị zero, `uninit` rõ ràng chỉ ra rằng biến đó chưa chứa bất kỳ dữ liệu hữu ích nào. Mọi biến có giá trị `uninit` sẽ trỏ đến một vị trí bộ nhớ đặc biệt, cố định (vị trí đầu tiên) trong Máy Ảo Linh (LiVM). Cách tiếp cận này giúp Linh loại bỏ sự mơ hồ cố hữu của `null` và `undefined` (vốn có thể có nhiều ngữ nghĩa khác nhau), đảm bảo mọi biến luôn ở trạng thái xác định và an toàn. Nó cũng giảm thiểu đáng kể các lỗi liên quan đến con trỏ rỗng (null pointer exceptions) vì không có con trỏ nào thực sự "rỗng" theo nghĩa không hợp lệ. Khi một thao tác được thực hiện trên một giá trị `uninit`, LiVM có thể phát hiện và xử lý nó một cách an toàn, thường là bằng cách báo lỗi rõ ràng hoặc thực hiện một hành vi mặc định đã định trước.

* **Cơ Chế Hoạt Động:** Mã nguồn Linh được biên dịch thành bytecode bởi trình biên dịch LinhC. Trình biên dịch này không chỉ phân tích cú pháp và ngữ nghĩa mà còn thực hiện các kiểm tra kiểu mạnh mẽ (đối với `let`, `const` và các gợi ý kiểu tùy chọn) để đảm bảo tính an toàn của chương trình. Sau đó, Linh Bytecode được tạo ra và chạy trên Máy Ảo Linh (LiVM). LiVM chịu trách nhiệm nạp và thực thi bytecode một cách hiệu quả, quản lý bộ nhớ thông qua cơ chế thu gom rác (Garbage Collection), và cung cấp các API runtime cần thiết. Cơ chế này mang lại khả năng di động cao (chạy trên nhiều nền tảng) và hiệu suất tốt hơn so với các ngôn ngữ chỉ thông dịch thuần túy, trong khi vẫn giữ được cảm giác phát triển nhanh chóng và linh hoạt của một ngôn ngữ kịch bản.

* **Cú Pháp Quen Thuộc:** Ngữ pháp và cấu trúc lệnh của Linh được thiết kế để quen thuộc với các nhà phát triển đến từ các ngôn ngữ thuộc nhóm C như C, C++, Java, JavaScript, và C#. Điều này giúp giảm đáng kể thời gian học hỏi và chuyển đổi cho những người đã có kinh nghiệm. Các cấu trúc như vòng lặp `for`, `while`, câu lệnh điều kiện `if-else`, và cách khai báo hàm đều mang tính trực quan và dễ tiếp cận.

* **Nhập/Xuất Tích Hợp:** Các hàm `print()` và `input()` được tích hợp sẵn trong ngôn ngữ mà không cần phải import thư viện. Điều này đơn giản hóa việc thực hiện các tác vụ nhập/xuất cơ bản, đặc biệt hữu ích cho việc học tập, thử nghiệm nhanh chóng và các ứng dụng console.

## Cú Pháp Cơ Bản (Cập nhật)

### 1. Khai Báo Biến

Linh sử dụng ba từ khóa để khai báo biến: `var`, `let`, và `const`. Tất cả đều tuân theo phạm vi khối (block scope `{...}`), nghĩa là chúng chỉ có thể được truy cập trong khối mã mà chúng được định nghĩa.

| Từ khóa | Thay đổi Giá Trị | Thay đổi Kiểu Dữ Liệu | Mô tả |
| :------- | :--------------- | :-------------------- | :-------------------------------------------------------------------- |
| `var`    | Có               | Có                    | Biến động hoàn toàn. Có thể thay đổi cả giá trị và kiểu sau khi khai báo. Đây là lựa chọn linh hoạt nhất. |
| `let`    | Có               | Không                 | Biến giả tĩnh. Giá trị có thể thay đổi, nhưng kiểu phải giữ nguyên sau khi được suy luận hoặc khai báo tường minh. Cung cấp sự an toàn kiểu ở mức độ cao. |
| `const`  | Không            | Không                 | Hằng số. Giá trị và kiểu không thể thay đổi sau khi khởi tạo. Được sử dụng cho các giá trị bất biến. |

**Ví dụ:**

```linh
var score = 90;           // score là int
print(score);             // Output: 90
score = 95;               // OK, score vẫn là int
print(score);             // Output: 95
score = "Excellent";      // OK, 'var' cho phép thay đổi kiểu, score giờ là str
print(score);             // Output: Excellent

let retry_count = 3;      // retry_count là int
print(retry_count);       // Output: 3
retry_count = 4;          // OK, giá trị thay đổi nhưng kiểu vẫn là int
print(retry_count);       // Output: 4
// retry_count = "Four";  // LỖI! 'let' không cho thay đổi kiểu sau khi đã được suy luận là int

const PI_VALUE = 3.14159; // PI_VALUE là float
print(PI_VALUE);          // Output: 3.14159
// PI_VALUE = 3.14;       // LỖI! 'const' không cho thay đổi giá trị
```

**Suy luận kiểu:** Nếu bạn không chỉ định kiểu dữ liệu một cách tường minh, Linh sẽ tự động suy luận kiểu của biến dựa trên giá trị khởi tạo ban đầu. Điều này giúp mã nguồn ngắn gọn và dễ đọc hơn.

```linh
let user_name = "Alice";    // Suy luận là str
var current_age = 30;       // Suy luận là int (ban đầu), có thể thay đổi sau này
let is_admin = true;        // Suy luận là bool
```

**Khai báo với kiểu và Giá trị Zero:** Khi bạn khai báo một biến với một kiểu dữ liệu cụ thể nhưng không gán giá trị khởi tạo, biến đó sẽ nhận "giá trị zero" mặc định của kiểu đó. Điều này đảm bảo rằng biến luôn có một giá trị hợp lệ, ngay cả khi nó chưa được sử dụng.

```linh
let quantity: int;          // quantity = 0
print(quantity);            // Output: 0

var message_text: str;      // message_text = "" (chuỗi rỗng)
print(message_text);        // Output: (một dòng trống)

const IS_ACTIVATED: bool;   // IS_ACTIVATED = false
print(IS_ACTIVATED);        // Output: false
```

**Khai báo với `uninit`:**

* **`var` không khởi tạo:** Đây là điểm khác biệt quan trọng của phiên bản Linh mới. Khi bạn khai báo một biến `var` mà không gán bất kỳ giá trị nào và không chỉ định kiểu, biến đó sẽ mặc định có kiểu và giá trị là `uninit`. Điều này cho phép khai báo biến linh hoạt mà vẫn đảm bảo tính xác định.
    ```linh
    var a // Hợp lệ! 'a' có kiểu là uninit, và trỏ đến vị trí bộ nhớ 0
    id(a)   // Hàm giả định trả về ID của giá trị mà biến trỏ tới (vị trí bộ nhớ) -> Output: <id: 0>
    type(a) // Hàm giả định trả về kiểu dữ liệu hiện tại của biến -> Output: <type: 'uninit'>

    // Thử gán giá trị sau đó
    a = 123; // OK, 'a' giờ có kiểu int và giá trị 123
    print(type(a)); // Output: <type: 'int'>
    ```

* **`let`/`const` không khởi tạo:** Khai báo `let` hoặc `const` mà không gán giá trị khởi tạo (và không khai báo kiểu tường minh kèm gán `uninit`) sẽ gây lỗi biên dịch. Lý do là `let` và `const` yêu cầu một giá trị có ý nghĩa ngay lập tức để xác định kiểu cố định của chúng.
    ```linh
    // let b; // LỖI! Phải khởi tạo hoặc khai báo kiểu tường minh với uninit
    // const c; // LỖI! Phải khởi tạo
    ```

* **Gán `uninit` tường minh cho `let`:** Bạn có thể gán `uninit` một cách tường minh cho biến `let` đã khai báo kiểu. Điều này cho biết biến đó hiện tại chưa có giá trị hữu ích (tức là chưa được gán dữ liệu thực tế), nhưng vẫn cam kết với kiểu dữ liệu đã khai báo. Điều này hữu ích khi bạn muốn một biến có kiểu cố định nhưng giá trị ban đầu là "trống rỗng".
    ```linh
    let b: str = uninit // Hợp lệ! 'b' có kiểu 'str', giá trị là uninit.
                        // Sau này có thể gán b = "Hello";
    print(type(b));     // Output: <type: 'str'>
    print(id(b));       // Output: <id: 0>

    b = "Linh Lang";    // OK, gán giá trị chuỗi
    print(b);           // Output: Linh Lang
    print(id(b));       // Output: <id: [một ID khác 0]>
    ```

### 2. Kiểu Dữ Liệu

Linh không có `null` hay `undefined`. Thay vào đó, nó sử dụng khái niệm **giá trị zero** cho các kiểu dữ liệu cơ bản và đối tượng, cùng với kiểu đặc biệt **`uninit`** để biểu thị trạng thái chưa khởi tạo. Sự kết hợp này mang lại hệ thống kiểu mạnh mẽ và rõ ràng.

**Kiểu Dữ Liệu Cơ Bản:**

| Kiểu      | Mô tả                                                               | Giá trị Zero | Ví dụ Literal          |
| :-------- | :------------------------------------------------------------------ | :----------- | :--------------------- |
| `bool`    | Biểu diễn giá trị logic, chỉ có thể là đúng (`true`) hoặc sai (`false`). | `false`      | `true`, `false`        |
| `int`     | Số nguyên 64-bit có dấu, là kiểu số nguyên mặc định. Phạm vi giá trị rất rộng. | `0`          | `10`, `-5`, `1000000`  |
| `int<N>`  | Số nguyên N-bit có dấu, cho phép chỉ định kích thước bit cụ thể (N=8, 16, 32, 64). Hữu ích cho việc tối ưu hóa bộ nhớ hoặc tương tác với hệ thống cấp thấp. | `0`          | `int<8> small_num = 120;` |
| `uint`    | Số nguyên 64-bit không dấu, chỉ chứa các giá trị không âm. | `0`          | `100`, `0`, `2000000000` |
| `uint<N>` | Số nguyên N-bit không dấu (N=8, 16, 32, 64). | `0`          | `uint<16> port = 8080;` |
| `float`   | Số thực dấu phẩy động 64-bit, là kiểu số thực mặc định, cung cấp độ chính xác cao. | `0.0`        | `3.14`, `-0.5`, `1.23e-5` |
| `float<N>`| Số thực dấu phẩy động N-bit (N=32, 64). `float<32>` tương đương với `float` đơn trong C/Java. | `0.0`        | `float<32> temp = 25.5f;` |
| `str`     | Chuỗi ký tự Unicode, hỗ trợ đầy đủ các ký tự từ nhiều ngôn ngữ khác nhau. Có thể được khai báo bằng dấu nháy đơn, kép hoặc backtick (cho chuỗi nội suy). | `""`         | `"text"`, `'text'`, `` `Hello, &{user_name}!` `` |

**Kiểu Dữ Liệu Đối Tượng:**

| Kiểu                          | Mô tả                                                               | Giá trị Zero | Ví dụ Literal     |
| :---------------------------- | :------------------------------------------------------------------ | :----------- | :---------------- |
| `map<K, V>`                   | Ánh xạ khóa-giá trị, tương tự như từ điển (dictionary) hoặc đối tượng (object) trong các ngôn ngữ khác. Mặc định là `Map<any, any>`. | `{}`         | `{"name": "Linh", "age": 1}` |
| `array`                       | Mảng động, có thể chứa các phần tử thuộc nhiều kiểu khác nhau (ngầm định là `Array<any>`). | `[]`         | `[1, "two", true]`|
| `Type[]`                      | Mảng đồng nhất kiểu `Type`, nghĩa là tất cả các phần tử trong mảng phải cùng một kiểu dữ liệu cụ thể. | `[]`         | `[1, 2, 3]` (nếu `int[]`), `["apple", "banana"]` (nếu `str[]`) |

**Kiểu Dữ Liệu Đặc Biệt (Không dùng để khai báo biến trực tiếp):**

* **`void`:** Chỉ dùng làm kiểu trả về của hàm khi hàm không trả về giá trị nào.
* **`any`:** Đại diện cho "bất kỳ kiểu nào". Chủ yếu được sử dụng trong khai báo generic của `Map`, `Array`, hoặc làm kiểu tham số/trả về của hàm khi cần sự linh hoạt tối đa. **Không thể khai báo `var tên: any;`** vì Linh luôn muốn một kiểu dữ liệu xác định.
* **`uninit`:** Là một kiểu dữ liệu đặc biệt đại diện cho trạng thái chưa khởi tạo. Biến có kiểu `uninit` sẽ trỏ đến vị trí bộ nhớ đầu tiên của LiVM, đảm bảo mọi biến luôn ở trạng thái xác định.

### 3. Quy Tắc Đặt Tên (Identifiers)

Quy tắc đặt tên trong Linh rất rõ ràng để đảm bảo tính nhất quán và dễ đọc:

* Chỉ sử dụng chữ cái tiếng Anh (`a-z`, `A-Z`), chữ số (`0-9`), và dấu gạch dưới (`_`).
* Tên không được bắt đầu bằng chữ số.
* Không sử dụng các ký tự đặc biệt khác hoặc chữ tiếng Việt có dấu.
    ```linh
    let player_score = 1000; // Hợp lệ
    var user_id_2 = "U002";  // Hợp lệ
    // var product-code = "P001"; // LỖI: chứa dấu gạch ngang
    // let 1st_item = "Item A"; // LỖI: bắt đầu bằng chữ số
    ```

### 4. Từ Khóa (Keywords)

Các từ khóa trong Linh đều bằng tiếng Anh và được dành riêng cho cú pháp ngôn ngữ. Bạn không thể sử dụng chúng làm tên biến hoặc hàm.

* Ví dụ: `var`, `let`, `const`, `if`, `else`, `for`, `while`, `func`, `return`, `true`, `false`, `int`, `str`, `bool`, `float`, `map`, `array`, `void`, `input`, `print`, `uninit`.

### 5. Hàm (Functions)

Hàm là các khối mã có thể tái sử dụng để thực hiện một tác vụ cụ thể. Cú pháp khai báo hàm trong Linh tương tự như nhiều ngôn ngữ phổ biến khác, với việc chỉ định rõ ràng các tham số và kiểu trả về.

```linh
func function_name(param1: type1, param2: type2): return_type {
  // Thân hàm chứa logic thực thi
  return value; // Câu lệnh 'return' được sử dụng nếu return_type không phải là void
}
```

**Ví dụ:**
```linh
// Hàm cộng hai số nguyên và trả về tổng
func add_numbers(a: int, b: int): int {
  return a + b;
}

// Hàm không trả về giá trị (void)
func display_greeting(greeting_message: str): void {
  print(greeting_message);
}

// Hàm trả về kiểu kết hợp (Union Type), có thể là str hoặc bool
func get_information_by_id(id_value: int): <str, bool> {
  if (id_value > 0) {
    return "Valid ID found"; // Trả về chuỗi
  } else {
    return false;            // Trả về boolean
  }
}

let sum_result = add_numbers(5, 3); // sum_result = 8
print("Tổng là:", sum_result);       // Output: Tổng là: 8

display_greeting("Chào mừng đến với Linh!"); // Output: Chào mừng đến với Linh!

let info1 = get_information_by_id(10); // info1 sẽ là "Valid ID found" (kiểu str)
print(info1);

let info2 = get_information_by_id(-5); // info2 sẽ là false (kiểu bool)
print(info2);
```

### 6. Nhập/Xuất (I/O)

Các hàm I/O cơ bản được tích hợp sẵn trong Linh, giúp việc tương tác với người dùng qua console trở nên dễ dàng.

* **`print(...)`**: In một hoặc nhiều giá trị ra console. Các giá trị sẽ được chuyển đổi thành chuỗi và nối với nhau, thường có một khoảng trắng mặc định giữa chúng.
    ```linh
    let current_age = 25;
    print("Tuổi của bạn là:", current_age, "năm."); // Output: Tuổi của bạn là: 25 năm.
    print(1, "hai", 3.0, false);                   // Output: 1 hai 3 false
    print("Kết thúc chương trình.");               // Output: Kết thúc chương trình.
    ```

* **`input(variable_ref)`**: Đọc một dòng dữ liệu từ console và cố gắng gán nó vào biến được tham chiếu (`variable_ref`). Linh sẽ tự động cố gắng chuyển đổi chuỗi nhập vào sang kiểu dữ liệu của `variable_ref`. Nếu việc chuyển đổi không thành công (ví dụ: nhập chữ vào biến `int`), một lỗi runtime sẽ xảy ra.
    ```linh
    var input_name: str;
    var input_age: int;

    print("Vui lòng nhập tên của bạn: ");
    input(input_name); // Người dùng nhập "An"

    print("Vui lòng nhập tuổi của bạn: ");
    input(input_age);  // Người dùng nhập "30" (sẽ được chuyển đổi thành int)

    print("Xin chào &{input_name}, bạn &{input_age} tuổi.");
    // Output ví dụ: Xin chào An, bạn 30 tuổi.

    // Ví dụ lỗi:
    // print("Nhập một số: ");
    // input(input_age); // Nếu người dùng nhập "abc", sẽ gây lỗi runtime
    ```

### 7. Toán Tử

Linh hỗ trợ đầy đủ các toán tử số học, so sánh và logic quen thuộc, giúp thực hiện các phép tính và điều kiện phức tạp.

* **Số học:** `+` (cộng), `-` (trừ), `*` (nhân), `/` (chia), `%` (chia lấy dư).
    ```linh
    let result = (10 + 5) * 2 / 3; // result = 10.0 (float)
    let remainder = 17 % 5;        // remainder = 2 (int)
    ```
* **So sánh:** `==` (bằng), `!=` (khác), `>` (lớn hơn), `<` (nhỏ hơn), `>=` (lớn hơn hoặc bằng), `<=` (nhỏ hơn hoặc bằng). Các toán tử này trả về giá trị `bool`.
    ```linh
    let is_equal = (5 == 5);   // is_equal = true
    let is_greater = (10 > 7); // is_greater = true
    let is_not_equal = ("apple" != "orange"); // is_not_equal = true
    ```
* **Logic:** `&&` (và logic), `||` (hoặc logic), `!` (phủ định logic).
    ```linh
    let condition1 = true;
    let condition2 = false;
    let combined = condition1 && condition2; // combined = false
    let either = condition1 || condition2;   // either = true
    let not_condition1 = !condition1;        // not_condition1 = false
    ```

### 8. Cấu Trúc Điều Khiển

Linh sử dụng các cấu trúc điều khiển phổ biến để quản lý luồng thực thi của chương trình.

* **`if (condition) { ... } else if (other_condition) { ... } else { ... }`**: Thực thi các khối mã khác nhau dựa trên các điều kiện.
    ```linh
    let temperature = 28;
    if (temperature > 30) {
      print("Trời rất nóng!");
    } else if (temperature > 25) {
      print("Trời ấm áp.");
    } else {
      print("Trời mát mẻ.");
    }
    // Output: Trời ấm áp.
    ```
* **`while (condition) { ... }`**: Lặp lại một khối mã miễn là điều kiện còn đúng.
    ```linh
    var count = 0;
    while (count < 5) {
      print("Count:", count);
      count = count + 1;
    }
    // Output: Count: 0, Count: 1, Count: 2, Count: 3, Count: 4
    ```
* **`for (initializer; condition; step) { ... }`**: Vòng lặp `for` kiểu C, hữu ích cho việc lặp lại một số lần xác định.
    ```linh
    for (let i = 0; i < 3; i = i + 1) {
      print("Lặp lần thứ:", i);
    }
    // Output: Lặp lần thứ: 0, Lặp lần thứ: 1, Lặp lần thứ: 2
    ```

### 9. Chú Thích (Comments)

Chú thích giúp làm cho mã nguồn dễ hiểu hơn. Linh hỗ trợ hai loại chú thích:

```linh
// Đây là chú thích một dòng

/*
  Đây là một
  khối chú thích
  đa dòng.
*/
```

## Một Ví Dụ Đầy Đủ Hơn

Chương trình tìm người dùng theo ID, yêu cầu người dùng cung cấp giá trị mặc định nếu không tìm thấy để tránh `uninit` hoặc các giá trị không mong muốn.

```linh
// Định nghĩa một Map để lưu trữ cơ sở dữ liệu người dùng
let user_database: Map<int, Map<str, any>> = {
    101: { "id": 101, "name": "Alice", "is_active": true, "email": "alice@example.com" },
    102: { "id": 102, "name": "Bob", "is_active": false, "email": "bob@example.com" },
    103: { "id": 103, "name": "Charlie", "is_active": true, "email": "charlie@example.com" }
};

// Hàm để tìm người dùng theo ID.
// Hàm này yêu cầu một giá trị mặc định để trả về nếu người dùng không được tìm thấy,
// đảm bảo rằng hàm luôn trả về một đối tượng Map hợp lệ, không bao giờ là uninit.
func find_user_by_id(search_id: int, default_user: Map<str, any>): Map<str, any> {
    // Trong Linh, truy cập một khóa không tồn tại trong Map sẽ trả về uninit.
    // Do đó, chúng ta kiểm tra giá trị trả về có phải là uninit hay không.
    var found_user_data = user_database[search_id];
    if (type(found_user_data) != type(uninit)) {
        return found_user_data; // Trả về thông tin người dùng nếu tìm thấy
    } else {
        return default_user;             // Trả về giá trị mặc định nếu không tìm thấy
    }
}

// Định nghĩa một hồ sơ người dùng khách mặc định
let guest_user_profile: Map<str, any> = { "id": 0, "name": "Guest", "is_active": false, "email": "guest@example.com" };

// Tìm người dùng có ID 101
let found_user1 = find_user_by_id(101, guest_user_profile);
print("Tìm thấy (ID 101): Tên - ", found_user1["name"], ", Email - ", found_user1["email"]); // Output: Tìm thấy (ID 101): Tên - Alice, Email - alice@example.com

// Tìm người dùng không tồn tại (ID 999)
let not_found_user = find_user_by_id(999, guest_user_profile);
print("Không tìm thấy (ID 999): Tên - ", not_found_user["name"], ", Email - ", not_found_user["email"]); // Output: Không tìm thấy (ID 999): Tên - Guest, Email - guest@example.com

// Người dùng cũng có thể cung cấp một đối tượng mặc định khác ngay tại chỗ
let found_user2 = find_user_by_id(102, { "id": -1, "name": "Unknown", "is_active": false, "email": "unknown@example.com" });
print("Tìm thấy (ID 102): Tên - ", found_user2["name"], ", Email - ", found_user2["email"]); // Output: Tìm thấy (ID 102): Tên - Bob, Email - bob@example.com

// Ví dụ về việc sử dụng uninit trong một tình huống thực tế
func get_optional_data(should_return: bool): <str, uninit> {
    if (should_return) {
        return "Dữ liệu có sẵn";
    } else {
        return uninit; // Trả về uninit khi không có dữ liệu hữu ích
    }
}

var data_status = get_optional_data(true);
if (type(data_status) != type(uninit)) { // Kiểm tra nếu giá trị không phải là uninit
    print("Trạng thái dữ liệu:", data_status); // Output: Trạng thái dữ liệu: Dữ liệu có sẵn
} else {
    print("Không có dữ liệu.");
}

data_status = get_optional_data(false);
if (type(data_status) != type(uninit)) {
    print("Trạng thái dữ liệu:", data_status);
} else {
    print("Không có dữ liệu."); // Output: Không có dữ liệu.
}
```

## Cơ Chế Hoạt Động

1.  **Mã Nguồn Linh (`.linh`) hoặc (`.li`):** Người dùng viết mã bằng cú pháp Linh. Mã nguồn này được thiết kế để dễ đọc và dễ bảo trì, tuân thủ các quy tắc kiểu dữ liệu chặt chẽ của Linh.
2.  **Trình Biên Dịch Linh (LinhC):**
    * **Phân tích cú pháp và ngữ nghĩa:** LinhC đọc mã nguồn, kiểm tra cú pháp và đảm bảo rằng mã tuân thủ các quy tắc ngữ nghĩa của ngôn ngữ.
    * **Thực hiện kiểm tra kiểu tùy chọn:** Dựa trên các khai báo `let`, `const` và gợi ý kiểu, LinhC thực hiện kiểm tra kiểu tĩnh để phát hiện lỗi sớm ngay tại thời điểm biên dịch, trước khi chương trình chạy. Điều này giúp tăng cường độ tin cậy của mã.
    * **Biên dịch mã nguồn thành Linh Bytecode:** Sau khi xác minh, LinhC chuyển đổi mã nguồn cấp cao thành một dạng trung gian, hiệu quả hơn là Linh Bytecode. Bytecode này được tối ưu hóa để thực thi nhanh chóng trên LiVM.
3.  **Máy Ảo Linh (LiVM):**
    * **Nạp và thực thi Linh Bytecode:** LiVM chịu trách nhiệm nạp Linh Bytecode đã biên dịch và thực thi từng lệnh một cách tuần tự.
    * **Quản lý bộ nhớ (Garbage Collection):** LiVM tự động quản lý bộ nhớ, giải phóng các đối tượng không còn được sử dụng thông qua cơ chế thu gom rác. Điều này giúp lập trình viên không phải lo lắng về việc quản lý bộ nhớ thủ công, giảm thiểu lỗi rò rỉ bộ nhớ.
    * **Cung cấp API runtime:** LiVM cung cấp một bộ các API và dịch vụ runtime cần thiết để chương trình có thể tương tác với hệ điều hành, thực hiện các tác vụ I/O, và quản lý các tài nguyên khác.

Cơ chế hoạt động này đảm bảo rằng Linh là một ngôn ngữ mạnh mẽ, an toàn và có hiệu suất cao, phù hợp cho nhiều loại ứng dụng khác nhau.
