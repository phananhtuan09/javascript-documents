# Kiểm tra và tìm kiếm trong chuỗi

Mục lục

* [includes() là gì?](kiem-tra-va-tim-kiem-trong-chuoi.md#includes-la-gi)
* [indexOf() là gì?](kiem-tra-va-tim-kiem-trong-chuoi.md#indexof-la-gi)
* [lastIndexOf() là gì?](kiem-tra-va-tim-kiem-trong-chuoi.md#lastindexof-la-gi)
* [startsWith() là gì?](kiem-tra-va-tim-kiem-trong-chuoi.md#startswith-la-gi)
* [endsWith() là gì?](kiem-tra-va-tim-kiem-trong-chuoi.md#endswith-la-gi)
* [Các sai lầm thường gặp](kiem-tra-va-tim-kiem-trong-chuoi.md#cac-sai-lam-thuong-gap)
  * [Không phân biệt chữ hoa và chữ thường](kiem-tra-va-tim-kiem-trong-chuoi.md#khong-phan-biet-chu-hoa-va-chu-thuong)
  * [Không kiểm tra giá trị -1 từ indexOf()](kiem-tra-va-tim-kiem-trong-chuoi.md#khong-kiem-tra-gia-tri-1-tu-indexof)

### includes() là gì?

`includes()` là một phương thức sử dụng để kiểm tra xem một chuỗi con có tồn tại trong chuỗi gốc hay không.

**Cú pháp:**

```js
let bool = string.includes(searchString, position);
```

**Ví dụ:**

```js
const str = "Hello, world!";

console.log(str.includes("world")); // true
console.log(str.includes("World")); // false
console.log(str.includes("world", 8)); // false
```

`includes()` giúp kiểm tra nhanh chóng sự tồn tại của một chuỗi con trong chuỗi chính mà không cần phải viết nhiều code phức tạp.

**Bài toán và ví dụ:**

Kiểm tra xem một email có chứa ký tự ‘@’ không.

```javascript
const email = "example@domain.com";

console.log(email.includes("@")); // true
```

Kiểm tra xem một câu có chứa từ khóa “JavaScript” không.

```javascript
const sentence = "I love JavaScript programming.";

console.log(sentence.includes("JavaScript")); // true
```

***

### indexOf() là gì?

`indexOf()` là một phương thức được sử dụng để tìm vị trí (chỉ mục) đầu tiên của một chuỗi con trong chuỗi gốc. Phương thức này trả về vị trí của chuỗi con hoặc `-1` nếu không tìm thấy.

**Cú pháp:**

```js
let index = string.indexOf(searchValue, fromIndex);
```

**Ví dụ:**

```js
const str = "Hello, world!";

console.log(str.indexOf("world")); // 7
console.log(str.indexOf("World")); // -1
console.log(str.indexOf("o", 5)); // 8
```

`indexOf()` giúp xác định vị trí của một chuỗi con trong chuỗi chính, hữu ích khi cần biết vị trí bắt đầu của chuỗi con.

**Bài toán và ví dụ:**

Tìm vị trí đầu tiên của chữ “a” trong chuỗi.

```javascript
const str = "banana";

console.log(str.indexOf("a")); // 1
```

Kiểm tra xem một từ có xuất hiện trong câu không và in ra vị trí của nó.

```javascript
const sentence = "The quick brown fox jumps over the lazy dog.";

console.log(sentence.indexOf("fox")); // 16
```

***

### lastIndexOf() là gì?

`lastIndexOf()` là một phương thức được sử dụng để tìm vị trí xuất hiện cuối cùng của một chuỗi con trong chuỗi gốc.

**Cú pháp:**

```js
let bool = string.lastIndexOf(searchValue, fromIndex);
```

**Ví dụ:**

```js
const str = "Hello, world! Hello again!";

console.log(str.lastIndexOf("Hello")); // 13
console.log(str.lastIndexOf("World")); // -1
console.log(str.lastIndexOf("o", 5)); // 4
```

`lastIndexOf()` giúp xác định vị trí cuối cùng của một chuỗi con trong chuỗi chính, hữu ích khi cần biết vị trí xuất hiện cuối cùng của chuỗi con.

**Bài toán và ví dụ:**

Tìm vị trí xuất hiện cuối cùng của chữ “a” trong chuỗi.

```javascript
const str = "banana";

console.log(str.lastIndexOf("a")); // 5
```

Tìm vị trí của một từ trong câu.

```javascript
const sentence = "The quick brown fox jumps over the lazy dog. The dog is lazy.";

console.log(sentence.lastIndexOf("dog")); // 49
```

***

### startsWith() là gì?

`startsWith()` là một phương thức được sử dụng để kiểm tra xem chuỗi có bắt đầu bằng chuỗi hay không.

**Cú pháp:**

```js
let bool = string.startsWith(searchString, position);
```

**Ví dụ:**

```javascript
const str = "Hello, world!";

console.log(str.startsWith("Hello")); // true
console.log(str.startsWith("world")); // false
console.log(str.startsWith("world", 7)); // true
```

`startsWith()` giúp kiểm tra nhanh chóng và hiệu quả xem một chuỗi có bắt đầu bằng một chuỗi con cụ thể không.

**Bài toán và ví dụ:**

Kiểm tra xem URL có bắt đầu bằng “https://” không.

```javascript
const url = "https://example.com";

console.log(url.startsWith("https://")); // true
```

Kiểm tra xem tên tập tin có bắt đầu bằng “report\_” không.

```javascript
const fileName = "report_2023.pdf";

console.log(fileName.startsWith("report_")); // true
```

***

### endsWith() là gì?

`endsWith()` là một phương thức được sử dụng để kiểm tra xem chuỗi có kết thúc bằng chuỗi hay không.

**Cú pháp:**

```js
let bool = string.endsWith(searchString, length);
```

**Ví dụ:**

```js
const str = "Hello, world!";

console.log(str.endsWith("world!")); // true
console.log(str.endsWith("world")); // false
console.log(str.endsWith("Hello", 5)); // true
```

`endsWith()` giúp kiểm tra nhanh chóng và hiệu quả xem một chuỗi có kết thúc bằng một chuỗi con cụ thể không.

**Bài toán và ví dụ:**

Kiểm tra xem một tên miền có kết thúc bằng “.com” không.

```javascript
const domain = "example.com";

console.log(domain.endsWith(".com")); // true
```

Kiểm tra xem một file có kết thúc bằng “.jpg” không.

```javascript
const fileName = "picture.jpg";

console.log(fileName.endsWith(".jpg")); // true
```

***

### Các sai lầm thường gặp

#### &#x20;Không phân biệt chữ hoa và chữ thường

**Sai lầm:** `includes()`, `indexOf()`, `startsWith()`, và `endsWith()` đều phân biệt chữ hoa và chữ thường, dẫn đến kết quả không mong muốn.

```js
const str = "Hello, world!";

console.log(str.includes("World")); // false
```

**Cách giải quyết:** Sử dụng phương thức `toLowerCase()` hoặc `toUpperCase()` để chuẩn hóa chuỗi trước khi kiểm tra.

```js
const str = "Hello, world!".toLowerCase();

console.log(str.includes("World".toLowerCase())); // true
```

#### Không kiểm tra giá trị -1 từ indexOf()

**Sai lầm:** Không kiểm tra giá trị trả về từ `indexOf()`, dẫn đến lỗi logic trong chương trình.

**Cách giải quyết:** Luôn kiểm tra giá trị trả về từ `indexOf()`.

{% hint style="info" %}
Tóm tắt

* **Phương thức includes()**: `includes()` được sử dụng để kiểm tra xem một chuỗi con có tồn tại trong chuỗi gốc hay không. Trả về `true` nếu có, `false` nếu không.
  * **Ví dụ**:
    * `str.includes("world")` trả về `true` nếu chuỗi `str` chứa “world”.
    * `str.includes("world", 8)` kiểm tra từ vị trí 8 của chuỗi `str`.
* **Phương thức indexOf()**: `indexOf()` tìm vị trí đầu tiên của một chuỗi con trong chuỗi gốc. Trả về vị trí của chuỗi con hoặc `-1` nếu không tìm thấy.
  * **Ví dụ**:
    * `str.indexOf("world")` trả về `7` nếu “world” bắt đầu từ vị trí 7 trong `str`.
    * `str.indexOf("o", 5)` tìm “o” từ vị trí 5 trở đi.
* **Phương thức startsWith()**: `startsWith()` kiểm tra xem chuỗi có bắt đầu bằng chuỗi con cụ thể hay không. Trả về `true` hoặc `false`.
  * **Ví dụ**:
    * `str.startsWith("Hello")` trả về `true` nếu `str` bắt đầu bằng “Hello”.
    * `str.startsWith("world", 7)` kiểm tra từ vị trí 7 trong `str`.
* **Phương thức endsWith()**: `endsWith()` kiểm tra xem chuỗi có kết thúc bằng chuỗi con cụ thể hay không. Trả về `true` hoặc `false`.
  * **Ví dụ**:
    * `str.endsWith("world!")` trả về `true` nếu `str` kết thúc bằng “world!”.
    * `str.endsWith("Hello", 5)` kiểm tra chuỗi con “Hello” có kết thúc ở vị trí 5 của `str`.
{% endhint %}
