# Toán tử Nullish Coalescing

Mục lục

* [Toán tử Nullish coalescing](toan-tu-nullish-coalescing.md#toan-tu-nullish-coalescing)
  * [Cú pháp sử dụng](toan-tu-nullish-coalescing.md#cu-phap-su-dung)
  * [Ví dụ sử dụng](toan-tu-nullish-coalescing.md#vi-du-su-dung)
* [Ví dụ thực tế sử dụng Nullish coalescing](toan-tu-nullish-coalescing.md#vi-du-thuc-te-su-dung-nullish-coalescing)
  * [Tình huống trong thực tế](toan-tu-nullish-coalescing.md#tinh-huong-trong-thuc-te)
  * [Cách khắc phục với Nullish coalescing](toan-tu-nullish-coalescing.md#cach-khac-phuc-voi-nullish-coalescing)
* [Những lưu ý quan trọng](toan-tu-nullish-coalescing.md#nhung-luu-y-quan-trong)
  * [Khi nào nên sử dụng Nullish coalescing?](toan-tu-nullish-coalescing.md#khi-nao-nen-su-dung-nullish-coalescing)
  * [So sánh Nullish Coalescing (??) và OR (||):](toan-tu-nullish-coalescing.md#so-sanh-nullish-coalescing-va-or-or-or)
  * [“Đánh giá ngắn gọn” (short-circuit evaluation)](toan-tu-nullish-coalescing.md#danh-gia-ngan-gon-short-circuit-evaluation)
  * [Có thể lỗi cú pháp khi dùng với AND hoặc OR](toan-tu-nullish-coalescing.md#co-the-loi-cu-phap-khi-dung-voi-and-hoac-or)

### Toán tử Nullish coalescing

Toán tử _Nullish coalescing_ (`??`) là toán tử logical trả về toán hạng bên phải của nó khi toán hạng bên trái là `null` hoặc `undefined`. Ngược lại trả về toán hạng bên trái của nó.

> _Toán tử Nullish coalescing (`??`) được giới thiệu trong ECMAScript 2020 (ES11) cung cấp một cách tiện lợi để xử lý các giá trị `null` và `undefined`._

#### Cú pháp sử dụng

Cú pháp của nullish coalescing trong JavaScript là sử dụng hai dấu hỏi ??. Cấu trúc cơ bản như sau:

```js
let kết_quả = biến ?? giá_trị_mặc_định;
```

Ở đây, `biến` là giá trị bạn muốn kiểm tra, và `giá_trị_mặc_định` là giá trị sẽ được sử dụng nếu biến có giá trị `null` hoặc `undefined`. Nếu `biến` có bất kỳ giá trị nào khác `null` và `undefined` thì giá trị của `biến` sẽ được sử dụng.

#### Ví dụ sử dụng

**Ví dụ 1**: Đặt giá trị mặc định khi `tenHienThi` là `null`.

```js
let tenNguoiDung = null; // Giả sử tên người dùng trống
let macDinh = "Khách";

let tenHienThi = tenNguoiDung ?? macDinh;
console.log(tenHienThi); // Khách
```

Ở đây, `tenNguoiDung` là `null`, do đó `tenHienThi` nhận giá trị `"Khách"` từ biến `macDinh`.

**Ví dụ 2**: Hoặc khi `tenNguoiDung` là `undefined`.

```js
let tenNguoiDung; // Giả sử tên người dùng chưa khởi tạo
let macDinh = "Khách";

let tenHienThi = tenNguoiDung ?? macDinh;
console.log(tenHienThi); // Khách
```

Trong trường hợp này, `tenNguoiDung` là `undefined`, do đó `tenHienThi` nhận giá trị `"Khách"` từ biến `macDinh`.

**Ví dụ 3**: Trường hợp có tên người dùng.

```js
let tenNguoiDung = "Nguyễn Văn A";
let macDinh = "Khách";

let tenHienThi = tenNguoiDung ?? macDinh;
console.log(tenHienThi); // Nguyễn Văn A
```

Trường hợp này, `tenNguoiDung` khác `null` và `undefined`, do đó `tenHienThi` nhận giá trị `"Nguyễn Văn A"` từ biến `tenNguoiDung`.

***

### Ví dụ thực tế sử dụng Nullish coalescing

_Nullish coalescing_ thường được sử dụng để **cung cấp một giá trị mặc định** khi giá trị hiện tại của nó là `null` hoặc `undefined`.

#### Tình huống trong thực tế

Tạo một hàm `getElement` có ba tham số là `array`, `index` và `defaultValue`. Hàm sẽ trả về giá trị của phần tử tương ứng với `index`, nếu giá trị là `undefined` thì trả về giá trị mặc định (`defaultValue`).

**Ví dụ 1**: Sử dụng toán tử OR `||`.

```js
function getElement(array, index, defaultValue) {
  return array[index] || defaultValue;
}
```

Kết quả có vẻ như mong đợi:

```js
let colors = ["Red", "Green", "Blue"];

getElement(colors, 0, "Empty"); // "Red"
getElement(colors, 1, "Empty"); // "Green"
getElement(colors, 2, "Empty"); // "Blue"

getElement(colors, 3, "Empty"); // "Empty"
```

Biểu thức trong hàm là `array[index] || defaultValue`, khi truyền giá trị `index` là `3` - là một `index` không tồn tại trong mảng `colors`, lúc này `array[index]` sẽ trả về `undefined` (_falsy_). Toán tử OR nhận được “falsy” nên tiếp tục đánh giá điều kiện sau, lúc này là `defaultValue` đang có giá trị `"Empty"` (_truthy_) nên giá trị này được trả về.

**Ví dụ 2**: Tuy nhiên, trong trường hợp mảng chứa phần tử là “falsy”.

```js
let numbers = [1, 5, 0];

getElement(numbers, 0, "Empty"); // 1
getElement(numbers, 1, "Empty"); // 5
getElement(numbers, 2, "Empty"); // "Empty"
```

Trường hợp này, mặc dù với `index` là `2` sẽ có giá trị tương ứng là `0`. Tuy nhiên, `0` là giá trị “falsy” nên toán tử OR sẽ bỏ qua và lấy giá trị mặc định từ `defaultValue`, nên giá trị `"Empty"` được trả về. Điều này có thể dẫn tới kết quả không như mong đợi.

**Ví dụ 3**: Hoặc, tương tự như trên - một mảng chứa “falsy”.

```js
let strings = ["Hello", ""];

getElement(strings, 0, "Empty"); // "Hello"
getElement(strings, 1, "Empty"); // "Empty"
```

Tương tự như ví dụ trên, mặc dù `index` là `1` sẽ có giá trị là chuỗi rỗng `""` (_falsy_), toán tử OR bỏ qua kiều kiện này và đánh giá tới `defaultValue` - nên kết quả trả về là `"Empty"`. Điều này có thể dẫn tới kết quả không như mong đợi.

#### Cách khắc phục với Nullish coalescing

Trước tiên, mình sẽ dùng `if-else` để làm, sau đó mởi sử dụng _Nullish coalescing_ để các bạn có thể so sánh được sự khác nhau.

**Ví dụ 1**: Sử dụng `if-else`.

```js
function getElement(array, index, defaultValue) {
  if (array[index] !== null && array[index] !== undefined) {
    return array[index];
  }
  return defaultValue;
}
```

Viết lại cho gọn hơn:

```js
function getElement(array, index, defaultValue) {
  const value = array[index];
  if (value !== null && value !== undefined)
    return value;
  return defaultValue;
}
```

Hoặc dùng toán tử 3 ngôi:

```js
function getElement(array, index, defaultValue) {
  const value = array[index];
  const hasValue = value !== null && value !== undefined;
  return hasValue ? array[index] : defaultValue;
}
```

Kết quả đã được như mong đợi:

```js
getElement(["Helo", ""], 1, "Empty"); // ""
getElement([1, 2, 0], 2, "Empty"); // 0
```

Tuy nhiên, cách sử dụng `if-else` và toán tử 3 ngôi có thể đúng về mặt logic, nhưng chưa mang lại ưu điểm về tính “ngắn gọn và dễ hiểu”. Sử dụng toán tử _Nullish coalescing_ trong tình huống này là một lựa chọn tốt.

Ví dụ: Sử dụng toán tử Nullish coalescing.

```js
function getElement(array, index, defaultValue) {
  return array[index] ?? defaultValue;
}
```

Hàm này sẽ trực tiếp trả về giá trị tại index nếu nó không phải là `null` hoặc `undefined`. Nếu không, nó sẽ trả về `defaultValue`. Code lúc này trở nên ngắn gọn và dễ hiểu hơn, đồng thời vẫn giữ được chức năng ban đầu.

Kết quả như mong đợi:

```js
let strings = ["Helo", ""];
getElement(strings, 0, "Empty"); // "Helo"
getElement(strings, 1, "Empty"); // ""
getElement(strings, 2, "Empty"); // "Empty"

let numbers = [2, 0];
getElement(numbers, 0, "Empty"); // 2
getElement(numbers, 1, "Empty"); // 0
getElement(numbers, 2, "Empty"); // "Empty"
```

Sử dụng _Nullish coalescing_ có thể giúp tăng tính rõ ràng của code. Nó giúp xác định giá trị mặc định cho các biến có thể không được khởi tạo (`undefined`) hoặc `null`, mà không nhầm lẫn với các giá trị “falsy” khác.

**Lưu ý**: Khi sử dụng _Nullish coalescing_, hãy luôn cân nhắc mục đích của bạn tránh ảnh hưởng đến logic tổng thể của chương trình.

***

### Những lưu ý quan trọng

#### Khi nào nên sử dụng _Nullish coalescing_?

* **Khi xử lý các giá trị có thể là `null` hoặc `undefined`**: Sử dụng _Nullish coalescing_ khi bạn muốn kiểm tra và xử lý các giá trị không chắc chắn như `null` hoặc `undefined`. Nó đặc biệt hữu ích trong các tình huống như: lấy giá trị từ mảng, object hoặc kiểm tra giá trị của một biến.
* **Đặt giá mặc định và tránh nhầm với các “falsy” khác**: Khi bạn muốn giữ lại các giá trị “falsy” khác như: `0`, `false`, chuỗi rỗng `""` v.v, nhưng vẫn muốn xử lý `null` và `undefined`.

#### So sánh Nullish Coalescing (??) và OR (||):

* Toán tử _OR_ (`||`) sẽ trả về giá trị đầu tiên nếu nó là “truthy”, hoặc giá trị thứ hai nếu giá trị đầu tiên là “falsy”. Điều này có thể dẫn đến việc không mong muốn khi xử lý các giá trị “falsy” khác như `0`, `false`, `""`, v.v.
* Ngược lại, _Nullish coalescing_ chỉ xét đến `null` và `undefined`, toán tử này trở thành lựa chọn tốt hơn khi bạn không muốn các giá trị “falsy” khác bị ảnh hưởng.

#### “Đánh giá ngắn gọn” (_short-circuit evaluation_)

_Nullish coalescing_ có tính chất “đánh giá ngắn gọn” (_short-circuit evaluation_). Có nghĩa là toán tử `??` chỉ đánh giá toán hạng thứ hai nếu toán hạng thứ nhất là `null` hoặc `undefined`. Nếu toán hạng thứ nhất có giá trị khác `null` hoặc `undefined`, nó sẽ trả về giá trị đó mà không cần đánh giá toán hạng thứ hai.

Ví vậy, bạn có thể gọi một hàm nếu giá trị của biến là `null` và `undefined`:

```js
let message = null;
message ?? alert("Không có message");
```

Ở đây, `message` có giá trị `null`. Toán tử _Nullish coalescing_ (`??`) kiểm tra toán hạng thứ nhất (`message`), và vì nó là `null`, toán tử này sau đó sẽ đánh giá toán hạng thứ hai, tức là gọi hàm `alert("Không có message")`.

#### Có thể lỗi cú pháp khi dùng với AND hoặc OR

Khi sử dụng toán tử _Nullish coalescing_ (`??`) cùng với các toán tử logic AND (`&&`) hoặc OR (`||`), có thể xảy ra lỗi cú pháp.

Khi bạn kết hợp `??` với `&&` hoặc `||` mà không sử dụng dấu ngoặc đơn để chỉ rõ ưu tiên của các toán tử, JavaScript sẽ báo lỗi cú pháp. Điều này là quy tắc để tránh nhầm lẫn trong việc đọc code.

**Ví dụ lỗi cú pháp**:

```js
let result = value1 ?? value2 && value3; // Lỗi cú pháp
```

**Cách khắc phục**:

Để khắc phục lỗi này, bạn cần sử dụng dấu ngoặc đơn để rõ ràng về ưu tiên của các toán tử:

```js
let result = (value1 ?? value2) && value3;
// Hoặc
let result = value1 ?? (value2 && value3);
```

Dấu ngoặc đơn giúp chỉ rõ liệu bạn muốn thực hiện toán tử `&&` trước hay là `??` trước.

**Tại sao lại có quy tắc này?**

Quy tắc này được đặt ra để tránh sự mơ hồ và lỗi không mong muốn trong việc xử lý các toán tử logic. Do `&&`, `||` và `??` có tính chất “short-circuit” nên có thể không đánh giá tất cả các biểu thức, việc kết hợp các toán tử này với nhau mà không rõ ràng có thể dẫn đến kết quả không như mong đợi hoặc khó hiểu. Vì vậy cần sử dụng ngoặc đơn `()` để chỉ rõ thứ tự ưu tiên.

Nhìn chung, khi sử dụng nhiều toán tử logic cùng nhau, việc sử dụng dấu ngoặc để chỉ rõ ưu tiên và ý định của bạn là một thói quen lập trình tốt, giúp code của bạn dễ đọc và bảo trì hơn.

{% hint style="info" %}
Tóm tắt

* **Khái niệm toán tử Nullish coalescing**: Toán tử `??` kiểm tra giá trị `null` hoặc `undefined`, trả về toán hạng bên phải nếu toán hạng bên trái là `null` hoặc `undefined`, ngược lại trả về toán hạng bên trái.
* **Cú pháp sử dụng**: `let kết_quả = biến ?? giá_trị_mặc_định;` cho phép đặt giá trị mặc định cho biến.
* **Ứng dụng thực tế**:
  * **Tránh lầm với giá trị “falsy” khác**: Giải quyết vấn đề khi mảng hoặc object chứa các giá trị “falsy” khác `null` và `undefined` như `0`, `false`, chuỗi rỗng `""`.
  * **Đặt giá trị mặc định khi lấy giá trị trong mảng**: Sử dụng `array[index] ?? defaultValue` để trả về giá trị mặc định nếu phần tử tại index là `undefined`.
* **Lưu ý quan trọng**:
  * **Khi nào nên sử dụng**: Khi xử lý giá trị có thể là `null` hoặc `undefined` và tránh nhầm lẫn với các giá trị “falsy” khác.
  * **So sánh với toán tử OR (`||`)**: `??` chỉ xét `null` và `undefined`, còn `||` xét tất cả giá trị “falsy”.
  * **“Đánh giá ngắn gọn” (**_**short-circuit evaluation**_**)**: `??` chỉ đánh giá toán hạng thứ hai nếu thứ nhất là `null` hoặc `undefined`.
  * **Lỗi cú pháp khi kết hợp với AND (`&&`) hoặc OR (`||`)**: Cần sử dụng dấu ngoặc để rõ ràng về ưu tiên của các toán tử.
{% endhint %}
