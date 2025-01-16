# Tổng quan về chuỗi

Mục lục

* [Đối tượng String](tong-quan-ve-chuoi.md#doi-tuong-string)
* [Tạo chuỗi](tong-quan-ve-chuoi.md#tao-chuoi)
* [Truy cập ký tự trong chuỗi](tong-quan-ve-chuoi.md#try-cap-ki-tu-trong-chuoi)
  * [Sử dụng phương thức charAt()](tong-quan-ve-chuoi.md#su-dung-phuong-thuc-charat)
  * [Sử dụng phương thức at()](tong-quan-ve-chuoi.md#su-dung-phuong-thuc-at)
  * [Sử dụng cú pháp ngoặc vuông](tong-quan-ve-chuoi.md#su-dung-cu-phap-ngoac-vuong)
* [So sánh chuỗi](tong-quan-ve-chuoi.md#so-sanh-chuoi)
* [Chuỗi nguyên thủy và chuỗi đối tượng](tong-quan-ve-chuoi.md#chuoi-nguyen-thuy-va-chuoi-doi-tuong)
* [Ép kiểu chuỗi (String coercion)](tong-quan-ve-chuoi.md#ep-kieu-chuoi-string-coercion)
* [Thuộc tính của đối tượng chuỗi](tong-quan-ve-chuoi.md#thuoc-tinh-cua-doi-tuong-chuoi)

### Đối tượng string

Đối tượng `String` được sử dụng để biểu diễn và thao tác với chuỗi ký tự trong JavaScript.

***

### Tạo chuỗi

Chuỗi có thể được tạo dưới dạng nguyên thủy hoặc dưới dạng đối tượng bằng cách sử dụng hàm tạo `String()`.

Ví dụ:

```javascript
const string1 = "A string primitive";
const string2 = 'Also a string primitive';
const string3 = `Yet another string primitive`;
const string4 = new String("A String object");
```

***

### Try cập kí tự trong chuỗi

Có ba cách để truy cập ký tự trong chuỗi:

#### Sử dụng phương thức charAt()

Phương thức `charAt()` nhận một chỉ số (`index`) và trả về ký tự tại vị trí tương ứng.

Ví dụ:

```javascript
"cat".charAt(1); // "a"
```

> Lưu ý: Nếu chỉ số nằm ngoài phạm vi `[0, str.length - 1]`, phương thức sẽ trả về chuỗi rỗng.

#### Sử dụng phương thức at()

Phương thức `at()` hỗ trợ chỉ số âm, cho phép truy cập từ cuối chuỗi.

Ví dụ:&#x20;

```javascript
console.log("cat".at(1)); // a
console.log("cat".at(-1)); // t
console.log("cat".at(5)); // undefined
```

> Lưu ý: Nếu chỉ số nhỏ hơn `-str.length` hoặc lớn hơn hoặc bằng `str.length`, kết quả trả về là `undefined`.

#### Sử dụng cú pháp ngoặc vuông

Bạn có thể truy cập ký tự trong chuỗi bằng cú pháp giống như truy cập phần tử mảng.

Ví dụ:

```javascript
console.log("cat"[0]); // c
console.log("cat"[3]); // undefined
```

> Lưu ý: Nếu chỉ số nằm ngoài phạm vi `[0, str.length - 1]`, kết quả trả về là `undefined`.

***

### So Sánh chuỗi

Chuỗi có thể được so sánh bằng các toán tử `<`, `>`, `===`, và `==`.

Vi dụ:

```javascript
const a = "a";
const b = "b";
if (a < b) {
  // true
  console.log(`${a} is less than ${b}`);
} else if (a > b) {
  console.log(`${a} is greater than ${b}`);
} else {
  console.log(`${a} and ${b} are equal.`);
}
// a is less than b
```

> Lưu ý: So sánh chuỗi phân biệt chữ hoa và chữ thường. Để so sánh không phân biệt, chuyển cả hai chuỗi về cùng một dạng (chữ hoa hoặc chữ thường) trước khi so sánh.

**Phương pháp so sánh chuỗi nâng cao:**

* `Intl.Collator` API
* `localeCompare()`

***

### Chuỗi nguyên thuỷ và chuỗi đối tượng

JavaScript phân biệt giữa chuỗi nguyên thủy và chuỗi đối tượng:

* **Chuỗi nguyên thủy:** Được tạo bằng string literals hoặc khi gọi `String()` không có từ khóa `new`.
* **Chuỗi đối tượng:** Được tạo bằng `new String()`.

***

### Ép kiểu chuỗi(String coercion)

&#x20;Một số thao tác trong JavaScript tự động ép các giá trị khác thành chuỗi.

Hoạt động ép kiểu sang chuỗi có thể tóm tắt như sau:

* `undefined` chuyển thành "undefined".
* `null` chuyển thành "null".
* `true` biến thành "true"; `false` biến thành "false".
* Số được chuyển đổi bằng cùng thuật toán như `toString(10)`.
* BigInts được chuyển đổi bằng cùng thuật toán như `toString(10)`.
* Symbols ném lỗi `TypeError`.
* Đối tượng được chuyển đổi thành một nguyên thủy bằng cách gọi các phương thức `Symbol.toPrimitive("string")`, `toString()` và `valueOf()` được gọi sau. Sau đó,  kết quả nguyên thủy được chuyển đổi thành một chuỗi.

Có một số cách để đạt được hiệu ứng gần như tương tự trong JavaScript:

* **Template literal**: thực hiện chính xác các bước ép buộc chuỗi được giải thích ở trên cho biểu thức nhúng vào template.
* **Hàm String()**: `String(x)` sử dụng cùng một thuật toán để chuyển đổi x, ngoại trừ việc Symbols không tạo ra lỗi `TypeError` mà trả về "Symbol(description)", trong đó description là mô tả của Symbol.
* **Sử dụng toán tử +**: "" + x ép toán hạng của nó thành một nguyên hàm thay vì một chuỗi và, đối với một số đối tượng, có hành vi hoàn toàn khác so với ép chuỗi thông thường.

***

### Thuộc tính của đối tượng chuỗi

* `String.prototype.constructor`**:** Hàm tạo cho các đối tượng chuỗi.
* `length`**:** Thuộc tính chỉ đọc, trả về độ dài của chuỗi.

Ví dụ:

```javascript
const str = "example";
console.log(str.length);  // 7
```

{% hint style="info" %}
Tóm tắt

* **Đối tượng String**: Là công cụ quan trọng để biểu diễn và thao tác các chuỗi ký tự.
* **Tạo chuỗi**: Có thể tạo chuỗi dưới dạng nguyên thủy hoặc đối tượng.
* **Truy cập ký tự**: Cung cấp ba phương pháp (`charAt`, `at`, và cú pháp ngoặc vuông) để truy cập các ký tự trong chuỗi.
* **So sánh chuỗi**: Có thể thực hiện so sánh phân biệt hoặc không phân biệt chữ hoa - chữ thường bằng cách sử dụng các phương pháp như `localeCompare`.
* **Chuỗi nguyên thủy và đối tượng**: Phân biệt rõ ràng giữa chuỗi nguyên thủy và chuỗi đối tượng.
* **Ép kiểu chuỗi**: Giới thiệu các phương pháp để chuyển đổi giá trị sang chuỗi như `String()`, template literals, và toán tử cộng (`+`).
* **Thuộc tính chuỗi**: Bao gồm `constructor` và `length`, giúp thao tác hiệu quả với chuỗi.
{% endhint %}
