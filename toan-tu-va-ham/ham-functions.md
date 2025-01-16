# Hàm (Functions)

Mục lục

* [Hàm là gì?](ham-functions.md#ham-la-gi)
* [Cách sử dụng hàm](ham-functions.md#cach-su-dung-ham)
  * [Định nghĩa hàm (Function definition)](ham-functions.md#dinh-nghia-ham-function-definition)
  * [Gọi hàm (Calling a function)](ham-functions.md#goi-ham-calling-a-function)
  * [Hàm có tham số (Parameters)](ham-functions.md#ham-co-tham-so-parameters)
  * [Tham số mặc định (Default parameters)](ham-functions.md#tham-so-mac-dinh-default-parameters)
  * [Hàm trả về giá trị (Return value)](ham-functions.md#ham-tra-ve-gia-tri-return-value)
* [Lợi ích khi sử dụng hàm](ham-functions.md#loi-ich-khi-su-dung-ham)
  * [Tránh lặp code](ham-functions.md#tranh-lap-code)
  * [Phân chia vấn đề lớn thành các phần nhỏ](ham-functions.md#phan-chia-van-de-lon-thanh-cac-phan-nho)
* [Lỗi thường gặp](ham-functions.md#loi-thuong-gap)

### Hàm là gì?

Hàm trong JavaScript là một khối code được thiết kế để thực hiện một tác vụ cụ thể. Hàm cho phép tái sử dụng code, thay vì viết lại cùng một đoạn code nhiều lần, bạn chỉ cần định nghĩa hàm một lần và gọi hàm đó khi cần.

***

### Cách sử dụng hàm

#### Định nghĩa hàm (Function definition)

Để tạo một hàm, bạn sử dụng từ khóa `function`, sau đó là tên của hàm, tiếp theo là một cặp dấu ngoặc đơn `()`, và một cặp dấu ngoặc nhọn `{}` bao quanh phần thân của hàm.

Cú pháp:

```js
function functionName() {
  // code block
}
```

Ví dụ:

```js
function showGreeting() {
  console.log("Xin chào!");
  console.log("Đây là khóa học JavaScript Pro!");
}
```

Khi hàm mới chỉ được định nghĩa, phần code trong thân của hàm sẽ không được chạy cho tới khi hàm được gọi.

#### Gọi hàm (Calling a function)

Để gọi hàm, ta sử dụng `()` sau tên một hàm.

```js
showGreeting(); // In ra: Xin chào!
// Đây là khóa học JavaScript Pro!
```

Bạn có thể gọi hàm nhiều lần, mỗi lần hàm được gọi thì code trong phần thân hàm sẽ được thực thi lại từ đầu.

```js
showGreeting(); // In ra: Xin chào!
// Đây là khóa học JavaScript Pro!

showGreeting(); // In ra: Xin chào!
// Đây là khóa học JavaScript Pro!
```

Ở đây hàm `showGreeting` vừa được gọi thêm hai lần, nội dung xin chào sẽ được in ra tương ứng cho mỗi lần gọi hàm.

#### Hàm có tham số (Parameters)

Hàm `showGreeting` ở trên đã có thể sử dụng lại nhiều lần. Tuy nhiên nó chưa đủ linh hoạt, vì nội dung trong `console.log()` đang được viết cố định bên trong phần thân của hàm. Để linh hoạt hơn, ta có thể định nghĩa **tham số** như sau.

Thêm tham số `message` cho hàm:

```js
function showGreeting(message) {
  console.log("Xin chào!");
  console.log(message);
}
```

Tại `console.log()` bên dưới, thay vì viết cố định nội dung như trước thì bây giờ nó nhận vào tham số `message`.

Cách gọi hàm có tham số như sau:

```js
showGreeting("Đây là khóa học của F8!"); // In ra: Xin chào!
// Đây là khóa học của F8!

showGreeting("Chào mừng bạn đã gia nhập F8!"); // In ra: Xin chào!
// Chào mừng bạn đã gia nhập F8!
```

Lúc này, nội dung được in ra từ `console.log()` bên dưới sẽ tương ứng với giá trị được truyền vào khi gọi hàm.

> **Lưu ý**: Giá trị được truyền vào khi gọi hàm được gọi là **đối số**. Ví dụ: `showGreeting("Đây là khóa học của F8!")` thì chuỗi `"Đây là khóa học của F8!"` là **đối số** của **tham số** `message`.

Một hàm có thể có nhiều tham số:

```js
// Mỗi tham số ngăn cách bằng một dấu phẩy (,)
function demo(param1, param2, param3) {
  console.log(param1, param2, param3);
}
```

Khi gọi hàm, ta có thể truyền nhiều đối số tương ứng:

```js
demo("Value 1", "Value 2", "Value 3"); // In ra: Value 1, Value 2, Value 3
```

Có thể gọi hàm với số lượng đối số không giống với số lượng tham số:

```js
demo("Value 1", "Value 2"); // In ra: Value 1, Value 2, undefined
```

Mặc dù hàm `demo()` được định nghĩa có 3 tham số là `param1`, `param2`, `param3`. Tuy nhiên khi gọi chỉ truyền có 2 đối số là `"Value 1"` và `"Value 2"`, lúc này giá trị của `param3` sẽ là `undefined` (vì không được truyền đối số tương ứng).

#### Tham số mặc định (Default parameters)

Giá trị mặc định của tham số sẽ được sử dụng khi đối số tương ứng không được truyền giá trị, hoặc khi truyền giá trị là `undefined`.

Sửa lại hàm `demo`, đặt `"Default value 3"` làm mặc định cho `param3`:

```js
function demo(param1, param2, param3 = "Default value 3") {
  console.log(param1, param2, param3);
}
```

Sau đó gọi hàm `demo()` mà không truyền đối số thứ 3:

```js
demo("Value 1", "Value 2"); // In ra: Value 1, Value 2, Default value 3
```

Khi không truyền đối số thứ 3, giá trị mặc định `"Default value 3"` đã được sử dụng, nên khi `console.log()` tham số `param3` thì `Default value 3` được in ra.

Hoặc khi gọi `demo()` với đối số thứ 3 là giá trị `undefined`:

```js
demo("Value 1", "Value 2", undefined); // In ra: Value 1, Value 2, Default value 3
```

Lúc này, giá trị mặc định của `param3` cũng sẽ được sử dụng. Tóm lại, chỉ cần tham số có giá trị mặc định và khi gọi hàm nó là `undefined` thì giá trị mặc định sẽ được sử dụng.

Nếu ta truyền đầy đủ đối số, thì giá trị mặc định sẽ không được sử dụng:

```js
demo("Value 1", "Value 2", "Value 3"); // In ra: Value 1, Value 2, Value 3
```

Lúc này, giá trị của `param3` sẽ là `"Value 3"`.

#### Hàm trả về giá trị (Return value)

Hàm có thể trả về một giá trị, nó tương tự như việc sử dụng “công thức nấu ăn” cuối cùng sẽ trả về “món ăn” vậy.

Hãy xem xét hàm sau:

```js
function sum(a, b) {
  console.log(a + b);
}
```

Hàm này tên là `sum`, nhận tham số `a`, `b` và in ra tổng của `a + b`.

Nếu chúng ta cần nhận lại được kết quả của phép cộng trên sau khi gọi hàm, thay vì in nó ra thì làm thế nào?

Chỉ cần sử dụng từ khóa `return` như sau:

```js
function sum(a, b) {
  return a + b;
}
```

Từ khóa `return` được sử dụng để trả về kết quả khi gọi một hàm.

> _Từ khóa `return` sẽ trả về giá trị và thoát hàm. Khi `return` được thực thi, những dòng code trong hàm nằm phía sau `return` sẽ bị bỏ qua._

Khi gọi hàm có sử dụng `return` ta sẽ nhận lại giá trị tương ứng:

In kết quả của hàm `sum()`:

```js
console.log(sum(2, 3)); // In ra: 5
```

Hoặc gán kết quả vào một biến:

```js
const result = sum(2, 3);
console.log(result); // In ra: 5
```

Ta có thể sử dụng lại hàm nhiều lần với các đối số khác nhau:

```js
const result1 = sum(3, 3);
console.log(result1); // In ra: 6

const result2 = sum(5, 3);
console.log(result2); // In ra: 8
```

Chỉ cần thay đổi đối số đầu vào thì kết quả trả về sẽ thay đổi tương ứng.

Lưu ý, một hàm không `return` thì sẽ nhận lại `undefined` khi gọi hàm:

```js
function sum(a, b) {
  a + b;
}
console.log(sum(1, 2)); // In ra: undefined
```

Một lưu ý khác, tránh nhầm lẫn `console.log()` với `return`.

Xem xét ví dụ sau:

```js
function sum(a, b) {
  console.log(a + b);
}
sum(2, 5); // In ra: 7
```

Lúc này, hàm `sum` không hề trả về giá trị `5`, số `5` được in ra bởi `console.log()` được sử dụng trong phần thân của hàm.

***

### Lợi ích khi sử dụng hàm

#### Tránh lặp code

Khi bạn thấy mình đang lặp lại cùng một đoạn code ở nhiều nơi, đó là lúc hàm trở nên hữu ích. Hàm giúp tập trung chức năng và giảm bớt sự trùng lặp.

#### Phân chia vấn đề lớn thành các phần nhỏ

Trong các dự án phức tạp, việc phân chia vấn đề thành các phần nhỏ, mỗi phần được xử lý bởi một hàm, giúp quản lý và hiểu code dễ dàng hơn.

***

### Lỗi thường gặp

* Không đặt tên hàm rõ ràng, không phản ánh được công việc mà hàm thực hiện.
* Quên `return` trong hàm, dẫn đến kết quả không như mong đợi.
* Sử dụng quá nhiều tham số, làm hàm khó hiểu và khó sử dụng.
* Viết thừa hoặc thiếu các dấu mở/đóng ngoặc như: `(`, `)`, `{`, `}`.

{% hint style="info" %}
Tóm tắt

* **Hàm trong JavaScript**: Là khối mã được thiết kế để thực hiện một tác vụ cụ thể, giúp tái sử dụng code và tránh lặp lại.
* **Định nghĩa hàm**: Sử dụng từ khóa `function`, tiếp theo là tên hàm, dấu ngoặc đơn `()` và tham số bên trong (nếu có), và dấu ngoặc nhọn `{}` cho phần thân của hàm.
* **Gọi hàm**: Sử dụng tên hàm với cặp dấu ngoặc đơn `()` để kích hoạt và thực thi mã trong hàm.
* **Hàm có tham số**: Cho phép truyền giá trị vào hàm để tăng tính linh hoạt và sự đa dạng trong việc xử lý.
* **Giá trị mặc định cho tham số**: Được sử dụng khi không có đối số tương ứng được truyền vào hoặc khi truyền giá trị là `undefined`.
* **Hàm trả về giá trị**: Sử dụng `return` để trả về giá trị từ hàm, giúp tái sử dụng kết quả của hàm trong các tác vụ khác.
* **Lợi ích khi sử dụng hàm**: Giúp tránh lặp code và phân chia vấn đề lớn thành các phần nhỏ, dễ quản lý.
* **Lỗi thường gặp**: Bao gồm đặt tên hàm không rõ ràng, quên sử dụng `return`, hoặc sử dụng quá nhiều tham số làm hàm khó hiểu.
{% endhint %}

