# Truthy và Falsy

Mục lục

* [Truthy và Falsy là gì?](truthy-va-falsy.md#truthy-va-falsy-la-gi)
  * [Các giá trị “falsy” trong JavaScript](truthy-va-falsy.md#cac-gia-tri-falsy-trong-javascript)
  * [Các giá trị “truthy” trong JavaScript](truthy-va-falsy.md#cac-gia-tri-truthy-trong-javascript)
  * [“document.all” là một ngoại lệ duy nhất](truthy-va-falsy.md#document.all-la-mot-ngoai-le-duy-nhat)
* [Tính ứng dụng trong thực tế](truthy-va-falsy.md#tinh-ung-dung-trong-thuc-te)

### Truthy và Falsy là gì?

Trong JavaScript, mọi giá trị đều có thể được coi là “truthy” hoặc “falsy”. Một giá trị khi được chuyển sang boolean trả về `true` được xem là “truthy”. Ngược lại, nếu giá trị tạo ra `false`, nó được gọi là “falsy”.

#### Các giá trị “falsy” trong JavaScript

* `false`: Đây là giá trị Boolean `false` rõ ràng.
* `0`: Số không. Bao gồm `-0` (số không âm) và `0n` (số 0 kiểu bigint).
* `""`: Chuỗi rỗng.
* `null`: Đại diện cho một giá trị “không có gì” hay “trống rỗng”.
* `undefined`: Biến chưa được gán giá trị, hoặc hàm không có giá trị trả về sẽ trả về `undefined`, v.v.
* `NaN`: Kết quả của một phép toán số học không hợp lệ.

#### Các giá trị “truthy” trong JavaScript

Toàn bộ các giá trị không phải “falsy” sẽ là “truthy”. Các giá trị này bao gồm:

* Chính giá trị Boolean `true`.
* Tất cả các chuỗi khác rỗng (`" "` (_chứa khoảng trắng_), `"0"`, `"false"`, v.v).
* Tất cả các Number khác `0`, `-0` và không phải `NaN` (bao gồm số âm và số dương).
* Các giá trị BigInt khác `0n`.
* Tất cả các đối tượng, kể cả các mảng và đối tượng rỗng (`[]` và `{}`).

#### “document.all” là một ngoại lệ duy nhất

`document.all`, từng được sử dụng để truy cập các phần tử HTML trong DOM, giờ đây đã lỗi thời. Mặc dù vậy, nó vẫn là một giá trị “falsy”, không thuộc vào nhóm `false`, `0`, `-0`, `0n`, `""`, `null`, `undefined`, hoặc `NaN`. Điều này làm nó trở thành một ngoại lệ trong quy tắc “falsy” thông thường của JavaScript.

```js
if (document.all) {
  console.log("Truthy");
} else {
  console.log("Falsy");  // Đoạn code này sẽ được thực thi
}
```

Khi kiểm tra loại của `document.all` với `typeof`, nó lại trả về `"undefined"`, mặc dù nó không phải là `undefined`:

```js
console.log(typeof document.all);  // "undefined"
```

Điều này là một phần nỗ lực của các nhà phát triển trình duyệt nhằm loại bỏ `document.all` mà không làm hỏng các trang web cũ sử dụng nó.

> _**Lưu ý**: `document.all` không thuộc JavaScript tiêu chuẩn mà là một tính năng cũ của các trình duyệt, ban đầu được phát triển bởi Internet Explorer để truy cập các phần tử HTML. Mặc dù không nằm trong tiêu chuẩn ECMAScript, các trình duyệt ngày nay vẫn hỗ trợ `document.all` để đảm bảo tương thích với các trang web cũ. Tuy nhiên, việc sử dụng `document.all` không còn được khuyến khích do đã lỗi thời và có các cách tiếp cận tiêu chuẩn như `document.getElementById()`, `document.querySelector()`, v.v._
>
> _**Tham khảo thêm**:_ [_https://developer.mozilla.org/en-US/docs/Web/API/Document/all_](https://developer.mozilla.org/en-US/docs/Web/API/Document/all)

***

### Tính ứng dụng trong thực tế

Câu lệnh `if` trong JavaScript được thực thi nếu giá trị của điều kiện là “truthy”. Điều này có nghĩa là không cần giá trị phải chính xác là `true` hay `false` theo nghĩa Boolean thuần túy, mà dựa trên khái niệm “truthy” và “falsy” của JavaScript.

**Đánh giá điều kiện trong if:**

* **Nếu giá trị là Truthy**: Câu lệnh `if` sẽ được thực thi.
* **Nếu giá trị là Falsy**: Câu lệnh trong `if` sẽ không được thực thi, câu lệnh trong `else` sẽ được thực thi (nếu có).

Ví dụ: Kiểm tra xem một chuỗi có phải là rỗng hay không.

Thay vì viết như sau:

```js
let myString = "";

if (myString === "") { // <-- Chú ý chỗ này
  console.log("Chuỗi rỗng"); // Kết quả này sẽ được in ra
} else {
  console.log("Chuỗi có dữ liệu");
}
```

Hoặc như này:

```js
let myString = "";

if (myString !== "") { // <-- Chú ý chỗ này
  console.log("Chuỗi có dữ liệu");
} else {
  console.log("Chuỗi rỗng"); // Kết quả này sẽ được in ra
}
```

Có thể viết ngắn gọn hơn:

```js
let myString = "";

if (myString) { // Giờ chỉ còn thế này
  console.log("Chuỗi có dữ liệu");
} else {
  console.log("Chuỗi rỗng"); // Kết quả này sẽ được in ra
}
```

**Giải thích**: `myString` là một chuỗi rỗng (`""`) và được đánh giá là “falsy”. Do đó, điều kiện trong `if` trả về `false` và khối lệnh `else` được thực thi.

{% hint style="info" %}
Tóm tắt

* **Khái niệm**:
  * “Truthy” là giá trị chuyển đổi sang boolean trả về `true`.
  * “Falsy” là giá trị chuyển đổi sang boolean trả về `false`.
* **Các giá trị “Falsy”**:
  * `false`, `0` (bao gồm `-0`, `0n`), `""` (chuỗi rỗng), `null`, `undefined`, `NaN`.
* **Các giá trị “Truthy”**:
  * **Toàn bộ các giá trị khác “Falsy”**: Boolean `true`, chuỗi không rỗng, số khác `0` và không là `NaN`, BigInt khác `0n`, tất cả đối tượng (bao gồm mảng và đối tượng rỗng) và ngoại lệ `document.all`.
* **Ngoại lệ “document.all”**:
  * Là giá trị “falsy” đặc biệt, không thuộc các loại “falsy” thông thường. `typeof document.all` trả về `"undefined"` dù nó không phải là `undefined`.
  * Lưu ý: `document.all` là tính năng cũ của trình duyệt, không thuộc JavaScript chuẩn.
* **Ứng dụng thực tế**:
  * Câu lệnh `if` dựa trên giá trị “truthy” và “falsy”.
  * Ví dụ: `if (myString)` sẽ kiểm tra nếu `myString` không rỗng (truthy) thì thực thi, ngược lại (falsy) thì không thực thi.
{% endhint %}

