# Chuyển đổi kiểu chữ

Mục lục

* [toLowerCase() là gì?](chuyen-doi-kieu-chu.md#tolowercase-la-gi)
* [toUpperCase() là gì?](chuyen-doi-kieu-chu.md#touppercase-la-gi)
* [Tại sao cần sử dụng chuyển đổi kiểu chữ?](chuyen-doi-kieu-chu.md#tai-sao-can-su-dung-chuyen-doi-kieu-chu)

### toLowerCase() là gì?

`toLowerCase()` là một phương thức được sử dụng để chuyển đổi tất cả các ký tự trong chuỗi thành chữ thường.

**Cú pháp:**

```js
let newLowerCaseStr = str.toLowerCase();
```

**Ví dụ:**

```js
let str = "HELLO WORLD";
let lowerStr = str.toLowerCase();

console.log(lowerStr); // "hello world"
```

***

### toUpperCase() là gì?

`toUpperCase()` là một phương thức được sử dụng để chuyển đổi tất cả các ký tự trong chuỗi thành chữ hoa.

**Cú pháp:**

```js
let newUpperCaseStr = str.toUpperCase();
```

**Ví dụ:**

```js
let str = "hello world";
let upperStr = str.toUpperCase();

console.log(upperStr); // "HELLO WORLD"
```

### Tại sao cần sử dụng chuyển đổi kiểu chữ?

Chuyển đổi kiểu chữ hữu ích khi bạn cần chuẩn hóa dữ liệu đầu vào hoặc so sánh chuỗi mà không phân biệt chữ hoa và chữ thường.

**Ưu điểm khi dùng:**

* Dễ dàng so sánh chuỗi không phân biệt chữ hoa và chữ thường.
* Chuẩn hóa dữ liệu đầu vào từ người dùng.

**Bài toán và ví dụ:**

So sánh hai chuỗi không phân biệt chữ hoa và chữ thường.

```javascript
let str1 = "Hello";
let str2 = "hello";

if (str1.toLowerCase() === str2.toLowerCase()) {
  console.log("Chuỗi giống nhau");
} else {
  console.log("Chuỗi khác nhau");
}
// Chuỗi giống nhau
```

Chuẩn hóa dữ liệu đầu vào từ người dùng.

```javascript
let userInput = "NguyenVanA@Gmail.com";
let normalizedInput = userInput.toLowerCase();

console.log(normalizedInput);
// nguyenvana@gmail.com
```

{% hint style="info" %}
Tóm tắt

* **toLowerCase() là gì**: Phương thức chuyển đổi tất cả các ký tự trong chuỗi thành chữ thường.
* **toUpperCase() là gì**: Phương thức chuyển đổi tất cả các ký tự trong chuỗi thành chữ hoa.
* **Tại sao cần sử dụng chuyển đổi kiểu chữ**:
  * **Lý do sử dụng**: Hữu ích khi cần chuẩn hóa dữ liệu đầu vào hoặc so sánh chuỗi mà không phân biệt chữ hoa và chữ thường.
  * **Ưu điểm**:
    * Dễ dàng so sánh chuỗi không phân biệt chữ hoa và chữ thường.
    * Chuẩn hóa dữ liệu đầu vào từ người dùng.
  * **Ví dụ**:
    *   So sánh hai chuỗi không phân biệt chữ hoa và chữ thường:

        ```js
        let str1 = "Hello";
        let str2 = "hello";

        if (str1.toLowerCase() === str2.toLowerCase()) {
          console.log("Chuỗi giống nhau");
        } else {
          console.log("Chuỗi khác nhau");
        }
        ```
    *   Chuẩn hóa dữ liệu đầu vào từ người dùng:

        ```js
        let userInput = "NguyenVanA@Gmail.com";
        let normalizedInput = userInput.toLowerCase();

        console.log(normalizedInput);
        ```
{% endhint %}
