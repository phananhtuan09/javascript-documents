# Xóa khoảng trắng thừa trong chuỗi

Mục lục

* [Xóa khoảng trắng thừa là gì?](xoa-khoang-trang-thua-trong-chuoi.md#xoa-khoang-trang-thua-la-gi)
* [Tại sao cần sử dụng xử lý khoảng trắng](xoa-khoang-trang-thua-trong-chuoi.md#tai-sao-can-su-dung-xu-ly-khoang-trang)
* [Bài toán và ví dụ](xoa-khoang-trang-thua-trong-chuoi.md#bai-toan-va-vi-du)
* [Các sai lầm thường gặp](xoa-khoang-trang-thua-trong-chuoi.md#cac-sai-lam-thuong-gap)
  * [Quên loại bỏ khoảng trắng trước khi so sánh chuỗi](xoa-khoang-trang-thua-trong-chuoi.md#quen-loai-bo-khoang-trang-truoc-khi-so-sanh-chuoi)
  * [Quên loại bỏ khoảng trắng khi lưu dữ liệu](xoa-khoang-trang-thua-trong-chuoi.md#quen-loai-bo-khoang-trang-khi-luu-du-lieu)

### Xóa khoảng trắng thừa là gì?

Xóa khoảng trắng thừa là việc loại bỏ các ký tự khoảng trắng không mong muốn ở đầu và cuối chuỗi ký tự.

* **`trim()`**: Loại bỏ khoảng trắng ở cả hai đầu chuỗi.
* **`trimStart()`**: Loại bỏ khoảng trắng ở đầu chuỗi.
* **`trimEnd()`**: Loại bỏ khoảng trắng ở cuối chuỗi.

***

### Tại sao cần sử dụng xử lý khoảng trắng

Khi làm việc với dữ liệu văn bản, việc loại bỏ khoảng trắng không mong muốn giúp đảm bảo dữ liệu được xử lý đúng cách, tránh lỗi logic trong chương trình.

**Ưu điểm khi dùng:**

Giúp làm sạch dữ liệu, tránh lỗi khi so sánh hoặc lưu trữ chuỗi.

**Bài toán 1:**

Loại bỏ khoảng trắng trong tên người dùng nhập vào để lưu trữ chính xác.

**Ví dụ:**

```js
let userName = "  John Doe  ";
let cleanedName = userName.trim();

console.log(cleanedName); // "John Doe"
```

***

### Bài toán và ví dụ

Loại bỏ khoảng trắng ở cả hai đầu của chuỗi:

```js
let str = "  Hello World  ";
let result = str.trim();

console.log(result); // "Hello World"
```

Loại bỏ khoảng trắng ở đầu chuỗi:

```js
let str = "  Hello World  ";
let result = str.trimStart();

console.log(result); // "Hello World  "
```

Loại bỏ khoảng trắng ở cuối chuỗi:

```js
let str = "  Hello World  ";
let result = str.trimEnd();

console.log(result); // "  Hello World"
```

***

### Các sai lầm thường gặp

#### Quên loại bỏ khoảng trắng trước khi so sánh chuỗi

Khi so sánh hai chuỗi mà không loại bỏ khoảng trắng, kết quả so sánh có thể sai.

**Cách giải quyết tốt:** Dùng `trim()` trước khi so sánh các chuỗi do người dùng nhập vào khi cần thiết.

```js
let str1 = "Hello";
let str2 = " Hello ";

console.log(str1 === str2); // false
console.log(str1 === str2.trim()); // true
```

#### Quên loại bỏ khoảng trắng khi lưu dữ liệu

Lưu trữ chuỗi có khoảng trắng không mong muốn có thể dẫn đến dữ liệu không nhất quán.

**Cách giải quyết tốt:** Dùng `trim()` trước khi lưu dữ liệu khi không thực sự cần lưu cả các khoảng trắng trước và cuối chuỗi.

```js
let userInput = "  Jane Doe  ";
let cleanedInput = userInput.trim();
// Lưu cleanedInput thay vì userInput
```

{% hint style="info" %}
Tóm tắt

* **Xóa khoảng trắng thừa**:
  * **`trim()`**: Loại bỏ khoảng trắng ở cả hai đầu chuỗi.
  * **`trimStart()`**: Loại bỏ khoảng trắng ở đầu chuỗi.
  * **`trimEnd()`**: Loại bỏ khoảng trắng ở cuối chuỗi.
* **Tại sao cần xử lý khoảng trắng**: Đảm bảo dữ liệu được xử lý đúng cách, tránh lỗi logic trong chương trình.
  * **Ưu điểm**: Giúp làm sạch dữ liệu, tránh lỗi khi so sánh hoặc lưu trữ chuỗi.
* **Các sai lầm thường gặp**:
  * **Quên loại bỏ khoảng trắng trước khi so sánh chuỗi**: Kết quả so sánh có thể sai.
    * **Giải pháp**: Dùng `trim()` trước khi so sánh các chuỗi khi cần thiết.
  * **Quên loại bỏ khoảng trắng khi lưu dữ liệu**: Dữ liệu không nhất quán.
    * **Giải pháp**: Dùng `trim()` trước khi lưu dữ liệu nếu không cần lưu cả khoảng trắng trước và cuối chuỗi.
{% endhint %}
