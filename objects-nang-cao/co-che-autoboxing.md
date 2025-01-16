# Cơ chế Autoboxing

Mục lục

* [Autoboxing là gì?](co-che-autoboxing.md#autoboxing-la-gi)
* [Nguyên lý hoạt động](co-che-autoboxing.md#nguyen-ly-hoat-dong)
  * [Quá trình Autoboxing](co-che-autoboxing.md#qua-trinh-autoboxing)
  * [Code minh họa](co-che-autoboxing.md#code-minh-hoa)
* [Sai lầm thường gặp](co-che-autoboxing.md#sai-lam-thuong-gap)
  * [Quên rằng autoboxing không áp dụng cho null và undefined](co-che-autoboxing.md#quen-rang-autoboxing-khong-ap-dung-cho-null-va-undefined)

### Autoboxing là gì?

Autoboxing là một cơ chế trong JavaScript mà qua đó các giá trị nguyên thủy (_primitive values_) như number, string, và boolean được tự động chuyển đổi thành đối tượng tương ứng khi cần thiết. Cơ chế này cho phép các giá trị nguyên thủy sử dụng các phương thức và thuộc tính của đối tượng tương ứng.

```javascript
let str = "hello";
console.log(str.toUpperCase()); // "HELLO"
```

Ở đây, chuỗi nguyên thủy `"hello"` được tự động đóng gói thành đối tượng String để sử dụng phương thức `toUpperCase()`.

Autoboxing giúp việc làm việc với các giá trị nguyên thủy linh hoạt hơn bằng cách cung cấp quyền truy cập vào các phương thức hữu ích mà không cần phải chuyển đổi rõ ràng chúng thành đối tượng.

***

### Nguyên lý hoạt động

#### &#x20;Quá trình Autoboxing

Vẫn sử dụng ví dụ trên, nhưng chúng ta sẽ “mổ sẻ” từng bước trong nguyên lý hoạt động của Autoboxing. Ví dụ:

```js
let str = "hello";
console.log(str.toUpperCase()); // "HELLO"
```

**Bước 1: Khai báo và khởi tạo biến**

```js
let str = "hello";
```

**Bước 2: Gọi phương thức toUpperCase()**

```js
console.log(str.toUpperCase());
```

Khi gọi phương thức `toUpperCase()` trên biến `str`, các công việc được thực hiện như sau:

* **Autoboxing:** JavaScript nhận ra rằng `"hello"` là một chuỗi nguyên thủy và cần phải truy cập phương thức `toUpperCase()` của đối tượng `String`. Do đó, JavaScript tạm thời chuyển đổi chuỗi nguyên thủy `"hello"` thành một đối tượng (`new String("hello")`). Quá trình này được gọi là “autoboxing”, nơi giá trị nguyên thủy được “đóng gói” trong một đối tượng tương ứng tạm thời.
* **Thực hiện phương thức:** Sau khi chuỗi được chuyển đổi thành đối tượng, phương thức `toUpperCase()` được gọi trên đối tượng đó (phương thức này được kế thừa từ `String.prototype`). Phương thức này chuyển tất cả các ký tự trong chuỗi thành chữ hoa.
* **Kết quả:** Phương thức `toUpperCase()` trả về chuỗi mới `"HELLO"`.

#### Code minh họa

Để rõ ràng hơn, bạn có thể xem đoạn code sau đây, mô phỏng quá trình autoboxing:

```js
// Giá trị nguyên thủy
let str = "hello";

// Autoboxing ngầm: tạo đối tượng tạm thời
let strObject = new String(str);

// Gọi phương thức trên đối tượng
let upperStr = strObject.toUpperCase();

// In ra "HELLO"
console.log(upperStr);
```

Trong thực tế, bạn không cần phải viết code như ví dụ trên để autoboxing xảy ra, vì JavaScript tự động thực hiện điều này cho bạn khi cần.

***

### Sai lầm thường gặp

#### Quên rằng autoboxing không áp dụng cho null và undefined

Các giá trị `null` và `undefined` không có đối tượng bao bọc tương ứng và sẽ gây lỗi khi cố gắng truy cập thuộc tính hoặc phương thức.

**Cách giải quyết:** Kiểm tra giá trị trước khi thực hiện phương thức.

```js
let value = null;

if (value) {
  // Lỗi nếu không kiểm tra trước
  console.log(value.toString());
}
```

{% hint style="info" %}
Tóm tắt

* **Khái niệm Autoboxing**: Autoboxing là cơ chế trong JavaScript giúp chuyển đổi các giá trị nguyên thủy như string, number thành đối tượng tương ứng một cách tự động để có thể sử dụng các phương thức của đối tượng đó.
* **Quá trình hoạt động của Autoboxing**:
  * **Khai báo và khởi tạo**: Tạo biến nguyên thủy.
  * **Gọi phương thức**: JavaScript tự động “đóng gói” giá trị nguyên thủy thành đối tượng để gọi phương thức.
  * **Kết quả trả về**: Sau khi phương thức được thực hiện, kết quả sẽ được trả về như là một giá trị mới.
* **Sai lầm thường gặp**:
  * **Quên autoboxing không áp dụng cho null và undefined**: Cố gắng gọi phương thức trên các giá trị `null` hoặc `undefined` sẽ gây ra lỗi.
{% endhint %}
