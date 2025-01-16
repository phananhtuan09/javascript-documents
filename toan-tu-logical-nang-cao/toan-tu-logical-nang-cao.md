# Toán tử Logical nâng cao

Mục lục

* [Toán tử AND và OR không chỉ trả về Boolean](toan-tu-logical-nang-cao.md#toan-tu-and-va-or-khong-chi-tra-ve-boolean)
  * [Nguyên lý hoạt động toán tử AND](toan-tu-logical-nang-cao.md#nguyen-ly-hoat-dong-toan-tu-and)
  * [Nguyên lý hoạt động toán tử OR](toan-tu-logical-nang-cao.md#nguyen-ly-hoat-dong-toan-tu-or)
* [“Đánh giá ngắn gọn” là gì?](toan-tu-logical-nang-cao.md#danh-gia-ngan-gon-la-gi)
  * [Áp dụng “Đánh giá ngắn gọn”](toan-tu-logical-nang-cao.md#ap-dung-danh-gia-ngan-gon)
  * [Kết luận: Cách tận dụng “Đánh giá ngắn gọn”](toan-tu-logical-nang-cao.md#ket-luan-cach-tan-dung-danh-gia-ngan-gon)
* [Các ứng dụng khác của toán tử AND và OR](toan-tu-logical-nang-cao.md#cac-ung-dung-khac-cua-toan-tu-and-va-or)
  * [Kiểm tra điều kiện và gọi hàm](toan-tu-logical-nang-cao.md#kiem-tra-dieu-kien-va-goi-ham)
  * [Gán giá trị mặc định](toan-tu-logical-nang-cao.md#gan-gia-tri-mac-dinh)
  * [Lấy một giá trị theo độ ưu tiên](toan-tu-logical-nang-cao.md#lay-mot-gia-tri-theo-do-uu-tien)

### Toán tử AND và OR không chỉ trả về Boolean

Thực tế, toán tử `&&` và `||` sẽ trả về giá trị của một trong các toán hạng, không nhất thiết phải là giá trị Boolean.

#### &#x20;Nguyên lý hoạt động toán tử AND

Toán tử `&&` trả về giá trị “falsy” đầu tiên. Nếu không có giá trị “falsy”, trả về giá trị cuối cùng.

Ví dụ:

```js
// Trả về falsy đầu tiên
false && true; // false
0 && 1; // 0
"" && null; // ""
5 && NaN && 6; // NaN

// Không có falsy, trả về giá trị cuối cùng
6 && 8; // 8
["Red", "Blue"] && { name: "John" } && "Hello"; // "Hello"
true && 1 && "Hello" && ["Red", "Green"]; // ["Red", "Green"]
```

**Tại sao lại có nguyên lý này?**: Toán tử `&&` được dùng để kiểm tra tất cả điều kiện đều đúng. Vì vậy, chỉ cần gặp điều kiện sai đầu tiên là có thể kết luận biểu thức là sai. Trả về giá trị “falsy” đầu tiên để phục vụ `if` kiểm tra và tiết kiệm tài nguyên (_không cần kiểm tra các điều kiện còn lại_).

**Ví dụ 1**: Kiểm tra `obj` là Object và không phải `null`.

```js
let obj = { key: "value" };

if (obj && typeof obj === "object") {
  console.log("Là Object"); // Kết quả được in ra
} else {
  console.log("Không phải là Object");
}
```

Trường hợp này, `obj && typeof obj === "object"` trả về `true`. Lệnh `if` nhận được `true` và khối lệnh `if` được thực thi.

**Ví dụ 2**: Xét trường hợp `obj = null`.

```js
let obj = null;

if (obj && typeof obj === "object") {
  console.log("Là Object");
} else 
  console.log("Không phải là Object"); // Kết quả được in ra
}
```

Do `obj` là `null` (_falsy_), toán tử `&&` sẽ ngay lập tức trả về `null`. Lệnh `if` nhận được `null` (_falsy_) nên khối lệnh `else` được thực thi.

#### &#x20;Nguyên lý hoạt động toán tử OR

Trả về giá trị “truthy” đầu tiên. Nếu không có giá trị “truthy”, trả về giá trị cuối cùng.

```js
// Trả về truthy đầu tiên
1 || 0; // 1
"Hello" || ""; // "Hello"
"Hi" || "Hello"; // "Hi"
10 || "Hello" || true; // 10

// Không có truthy, trả về giá trị cuối cùng
0 || NaN; // NaN
"" || 0 || null; // null
NaN || -0 || undefined || false; // false
```

**Tại sao lại có nguyên lý này?**: Toán tử `||` được dùng để kiểm tra ít nhất có một điều kiện đều đúng. Vì vậy, chỉ cần gặp điều kiện đúng đầu tiên là có thể kết luận biểu thức là đúng. Trả về giá trị “truthy” đầu tiên để phục vụ `if` kiểm tra và tiết kiệm tài nguyên (_không cần kiểm tra các điều kiện còn lại_).

**Ví dụ 1**: Kiểm tra có `firstName` hoặc `lastName`.

```js
let firstName = "";
let lastName = "Nguyen Van A";

if (firstName || lastName) {
  console.log("Có tên"); // Kết quả được in ra
} else {
  console.log("Không có tên");
}
```

Trường hợp này, `firstName || lastName` trả về `"Nguyen Van A"`. Lệnh `if` nhận được `"Nguyen Van A"` (_truthy_) nên khối lệnh `if` được thực thi.

**Ví dụ 2**: Xét trường hợp “Không có tên”.

```js
let firstName = "";
let lastName = "";

if (firstName || lastName) {
  console.log("Có tên");
} else {
  console.log("Không có tên"); // Kết quả được in ra
}
```

Lúc này, kết quả biểu thức `firstName || lastName` trả về `""` (_chuỗi rỗng_). Lệnh `if` nhận được `""` (_falsy_) nên khối lệnh `else` được thực thi.

***

### “Đánh giá ngắn gọn” là gì?

Đánh giá ngắn gọn (_Short-Circuit Evaluation_) là khi có thể biết kết quả cuối cùng mà không cần xem xét hết biểu thức, quá trình kiểm tra sẽ dừng và trả về kết quả. Điều này giúp tránh làm công việc thừa, giúp tối ưu hơn vì xử lý trở nên nhanh hơn.

**Có hai loại “Đánh giá ngắn gọn”**:

* **Toán tử && (AND)**: Nếu biểu thức bên trái là “falsy”, toàn bộ biểu thức sẽ trả về giá trị của biểu thức bên trái mà không cần đánh giá biểu thức bên phải.
* **Toán tử || (OR)**: Nếu biểu thức bên trái là “truthy”, toàn bộ biểu thức sẽ trả về giá trị của biểu thức bên trái mà không cần đánh giá biểu thức bên phải.

#### Áp dụng “Đánh giá ngắn gọn”

Để áp dụng được lợi ích từ “Đánh giá ngắn gọn”, lập trình viên cần am hiểu chính chất này của toán tử `&&` và `||` trong JavaScript.

**Ví dụ 1**: Không tận dụng được lợi ích từ “Đánh giá ngắn gọn”.

```js
let obj = null;

if (typeof obj === "object" && obj) {
  console.log("Là Object");
} else 
  console.log("Không phải là Object"); // Kết quả được in ra
}
```

**Cách viết này chưa tối ưu**: Vì `typeof obj === "object"` trả về `true` cho cả `null`, nên dù `obj` là `null`, điều kiện `obj` vẫn được đánh giá.

**Ví dụ 2**: Tận dụng được lợi ích từ “Đánh giá ngắn gọn”.

```js
let obj = null;

if (obj && typeof obj === "object") {
  console.log("Là Object");
} else 
  console.log("Không phải là Object"); // Kết quả được in ra
}
```

**Cách viết này tối ưu hơn**: Vì nếu `obj` là `null`, biểu thức sẽ ngay lập tức trả về `null`, và phần còn lại của biểu thức (`typeof obj === "object"`) không cần được đánh giá. Điều này giúp tăng hiệu suất khi không cần phải thực hiện các đánh giá không cần thiết.

#### Kết luận: Cách tận dụng “Đánh giá ngắn gọn”

* **Toán tử && (AND)**: Sắp xếp các điều kiện có khả năng trả về “falsy” nhiều hơn lên trước.
* **Toán tử || (OR)**: Sắp xếp các điều kiện có khả năng trả về “truthy” nhiều hơn lên trước.

Điều này giúp tối ưu hóa việc đánh giá biểu thức và cải thiện hiệu suất của chương trình.

***

### Các ứng dụng khác của toán tử AND và OR

Dựa vào nguyên lý hoạt động của toán tử `&&` và `||` nên chúng có thể được sử dụng trong nhiều trường hợp khác nhau, không chỉ dùng với `if-else`.

#### Kiểm tra điều kiện và gọi hàm

**Đề bài**: Khi điều kiện đúng thì sẽ gọi một hàm.

Cách dùng `if-else`:

```js
let greeting = "Xin chào!";
if (greeting) {
  alert(greeting); // Xin chào!
}
```

Cách dùng toán tử AND:

```js
let greeting = "Xin chào!";
greeting && alert(greeting); // Xin chào!
```

Trong trường hợp này, `greeting` có giá trị “truthy” (`"Xin chào!"`), do đó toán tử AND tiếp tục đánh giá và thực thi hàm `alert(greeting)`.

#### Gán giá trị mặc định

**Đề bài**: Biến `displayName` chứa tên hiển thị được lấy từ `userName`, nếu không có `userName` thì giá trị mặc định là `"Guest"`.

Cách dùng `if-else`:

```js
let userName = null; // Có thể là null hoặc các chuỗi khác
let displayName = "Guest";

if (userName) {
  displayName = userName;
}

console.log(displayName); // Guest
```

Cách dùng toán tử OR:

```js
let userName = null; // Có thể là null hoặc các chuỗi khác
let displayName = userName || "Guest";

console.log(displayName); // Guest
```

Trường hợp này `userName` là `null` nên toán tử OR sẽ tiếp tục đánh giá tới giá trị `"Guest"` (_truthy_) và trả về giá trị này.

#### Lấy một giá trị theo độ ưu tiên

**Đề bài**: Cho 3 biến `firstName`, `lastName` và `email` phục vụ cho việc in ra tên người dùng. Luôn in ra một trong 3 giá trị, ưu tiên theo thứ tự `firstName`, `lastName` và `email`, nếu cả 3 biến không có giá trị thì không in ra.

Áp dụng toán tử OR và AND:

```js
let firstName = "John";
let lastName = "Smith";
let email = "johnsmith@gmail.com";
let displayName = firstName || lastName || email;

displayName && console.log(displayName); // John
```

Nếu cả 3 biến không có giá trị, hiển thị tên mặc định là `"Guest"`:

```js
let firstName = null;
let lastName = null;
let email = null;
let displayName = firstName || lastName || email || "Guest";

console.log(displayName); // Guest
```

> Cả toán tử AND và OR đều rất linh hoạt và có thể được sử dụng trong nhiều tình huống khác nhau, từ kiểm tra điều kiện đơn giản đến xây dựng logic phức tạp. Việc hiểu rõ cách sử dụng chúng sẽ giúp bạn viết code hiệu quả và dễ đọc hơn.

{% hint style="info" %}
Tóm tắt

* **Hoạt động của Toán tử AND (`&&`)**: Trả về giá trị “falsy” đầu tiên hoặc giá trị cuối cùng nếu không có giá trị “falsy”. Thí dụ: `false && true` trả về `false`, còn `6 && 8` trả về `8`.
  * **Ứng dụng trong kiểm tra điều kiện**: Ví dụ, sử dụng `obj && typeof obj === "object"` trong bài toán kiểm tra `obj` không phải `null` và là một Object.
* **Hoạt động của Toán tử OR (`||`)**: Trả về giá trị “truthy” đầu tiên hoặc giá trị cuối cùng nếu không có giá trị “truthy”. Thí dụ: `1 || 0` trả về `1`, còn `"" || 0 || null` trả về `null`.
  * **Ứng dụng trong việc gán giá trị mặc định**: Ví dụ, `let displayName = userName || "Guest"`.
* **Đánh giá ngắn gọn (Short-Circuit Evaluation)**: Toán tử `&&` và `||` dừng đánh giá biểu thức khi đã đủ thông tin để quyết định kết quả, giúp tối ưu hiệu suất.
  * **Ví dụ 1**: `obj && typeof obj === "object"` trả về `null` ngay lập tức nếu `obj` là `null`.
  * **Ví dụ 2**: `firstName || lastName || "Guest"` trả về `firstName` ngay lập tức nếu có giá trị, nếu không thì trả về `lastName`, hoặc `"Guest"`.
* **Các ứng dụng khác**: Toán tử `&&` và `||` không chỉ dùng trong `if-else` mà còn trong việc gọi hàm theo điều kiện, gán giá trị mặc định, và lựa chọn giá trị theo độ ưu tiên.
{% endhint %}
