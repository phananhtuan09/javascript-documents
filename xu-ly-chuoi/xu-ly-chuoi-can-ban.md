# Xử lý chuỗi căn bản

Mục lục

* [concat() là gì?](xu-ly-chuoi-can-ban.md#concat-la-gi)
* [slice() là gì?](xu-ly-chuoi-can-ban.md#slice-la-gi)
* [substring() là gì?](xu-ly-chuoi-can-ban.md#substring-la-gi)
  * [Khác biệt so với slice()](xu-ly-chuoi-can-ban.md#khac-biet-so-voi-slice)
  * [Bảng so sánh slice() và substring()](xu-ly-chuoi-can-ban.md#bang-so-sanh-slice-va-substring)
* [split() là gì?](xu-ly-chuoi-can-ban.md#split-la-gi)
* [Các sai lầm thường gặp](xu-ly-chuoi-can-ban.md#cac-sai-lam-thuong-gap)
  * [Sử dụng sai chỉ mục trong slice() và substring()](xu-ly-chuoi-can-ban.md#su-dung-sai-chi-muc-trong-slice-va-substring)
  * [không truyền ký tự phân tách trong split()](xu-ly-chuoi-can-ban.md#khong-truyen-ky-tu-phan-tach-trong-split)

### concat() là gì?

Phương thức `concat()` được sử dụng để nối hai hoặc nhiều chuỗi với nhau.

**Cú pháp:**

```js
let newString = str1.concat(str2, str3, ..., strN);
```

**Ví dụ:**

```javascript
let greeting = "Hello, ";
let name = "Alice";
let fullGreeting = greeting.concat(name);

console.log(fullGreeting); // Hello, Alice
```

Phương thức `concat()` hữu ích khi bạn cần nối nhiều chuỗi lại với nhau mà không cần dùng dấu cộng (`+`).

**Bài toán và ví dụ:**

Nối tên và họ của một người:

```javascript
let firstName = "John";
let lastName = "Doe";
let fullName = firstName.concat(" ", lastName);

console.log(fullName); // John Doe
```

Tạo câu chào mừng cá nhân hóa:

```javascript
let greeting = "Welcome, ";
let userName = "Bob";
let personalized = greeting.concat(userName, "!");

console.log(personalized); // Welcome, Bob!
```

***

### slice() là gì?

Phương thức `slice()` được sử dụng để trích xuất một phần của chuỗi cha và trả về chuỗi con mới.

**Cú pháp:**

```js
let newString = str.slice(startIndex, endIndex);
```

**Ví dụ:**

```javascript
let text = "Hello, world!";
let result = text.slice(0, 5);

console.log(result); // Hello
```

Phương thức `slice()` hữu ích khi bạn cần lấy một phần của chuỗi theo vị trí bắt đầu và kết thúc.

**Bài toán và ví dụ:**

Lấy từ đầu tiên trong câu:

```javascript
let sentence = "JavaScript is fun";
let firstWord = sentence.slice(0, 10);

console.log(firstWord); // JavaScript
```

Lấy từ cuối cùng trong câu:

```javascript
let text = "Hello world";
let tail = text.slice(-5);

console.log(tail); // world
```

***

### substring() là gì?

Phương thức `substring()` được sử dụng để trích xuất các ký tự trong chuỗi giữa hai chỉ mục.

**Cú pháp:**

```js
let newString = str.substring(startIndex, endIndex);
```

**Ví dụ:**

```javascript
let text = "Hello, world!";
let result = text.substring(0, 5);

console.log(result); // Hello
```

Phương thức `substring()` hữu ích khi bạn cần lấy một phần của chuỗi giữa hai chỉ mục.

**Bài toán và ví dụ:**

Lấy từ nằm giữa hai chỉ số:

```javascript
let text = "Hello, world!";
let middle = text.substring(7, 12);

console.log(middle); // world
```

Lấy phần đầu chuỗi:

```javascript
let text = "Hello, world!";
let start = text.substring(0, 5);

console.log(start); // Hello
```

#### Khác biệt so với slice()

Cả `substring` và `slice` đều được sử dụng để lấy một phần của chuỗi. Tuy nhiên, chúng có một số điểm khác nhau quan trọng về cách thức hoạt động và cách chúng xử lý các tham số đầu vào.

**Với substring:**

* Nếu `start` lớn hơn `end`, `substring` sẽ hoán đổi hai tham số.
* Nếu bất kỳ tham số nào là số âm hoặc `NaN`, chúng được xem là `0`.
* Nếu bất kỳ tham số nào lớn hơn độ dài của chuỗi, chúng được xem là độ dài của chuỗi.
* Không hỗ trợ chỉ mục âm.

Ví dụ:

```js
let str = "Hello, World!";

console.log(str.substring(0, 5)); // "Hello"
console.log(str.substring(7)); // "World!"
console.log(str.substring(7, 12)); // "World"
console.log(str.substring(12, 7)); // "World"
console.log(str.substring(-3, 5)); // "Hello"
```

**Với slice:**

* Nếu `start` lớn hơn `end`, `slice` sẽ trả về một chuỗi rỗng.
* `start` và `end` có thể là số âm, được tính từ cuối chuỗi.
* Nếu bất kỳ tham số nào lớn hơn độ dài của chuỗi, chúng được xem là độ dài của chuỗi.

Ví dụ:

```js
let str = "Hello, World!";

console.log(str.slice(0, 5)); // "Hello"
console.log(str.slice(7)); // "World!"
console.log(str.slice(7, 12)); // "World"
console.log(str.slice(12, 7)); // ""
console.log(str.slice(-6, -1)); // "World"
```

#### Bảng so sánh slice() và substring()

Dưới đây là bảng so sánh sự khác biệt giữa hai phương thức này:

| Đặc điểm             | `substring`                                    | `slice`                                |
| -------------------- | ---------------------------------------------- | -------------------------------------- |
| **Hoán đổi tham số** | Nếu `start` > `end`, hoán đổi `start` và `end` | Nếu `start` > `end`, trả về chuỗi rỗng |
| **Chỉ số âm**        | Xem chỉ số âm là 0                             | Chỉ số âm tính từ cuối chuỗi           |
| **Đầu vào NaN**      | Được xem là 0                                  | Được xem là 0                          |

Với các đặc điểm và ví dụ trên, bạn có thể chọn phương thức phù hợp nhất cho trường hợp sử dụng cụ thể của mình.

***

### split() là gì?

Phương thức `split()` được sử dụng để chia một chuỗi thành một mảng các chuỗi con, dựa trên một ký tự phân tách.

**Cú pháp:**

```js
let newArray = str.split(separator, limit);
```

**Ví dụ:**

```javascript
let text = "apple, banana, cherry";

console.log(text.split(", ")); // (3) ['apple', 'banana', 'cherry']
console.log(text.split("")); // (22) ['a', 'p', 'p', 'l', 'e', ',', ' ', 'b', 'a', 'n', 'a', 'n', 'a', ',', ' ', 'c', 'h', 'e', 'r', 'r', 'y']
console.log(text.split()); // (1) ['apple, banana, cherry']
```

Phương thức `split()` hữu ích khi bạn cần tách một chuỗi thành các phần tử mảng dựa trên ký tự phân tách.

**Bài toán và ví dụ:**

Tách chuỗi thành mảng chứa các từ:

```javascript
let sentence = "The quick brown fox";
let words = sentence.split(" ");

console.log(words); // (4) ["The", "quick", "brown", "fox"]
```

Tách chuỗi theo dấu phẩy:

```javascript
let fruits = "apple,banana,cherry";
let fruitList = fruits.split(",");

console.log(fruitList); // (3) ["apple", "banana", "cherry"]
```

***

### Các sai lầm thường gặp

#### Sử dụng sai chỉ mục trong slice() và substring()

Khi sử dụng `slice()` và `substring()`, nếu bạn nhập chỉ số không hợp lý hoặc nhầm lẫn, bạn có thể không lấy được kết quả mong muốn.

#### không truyền ký tự phân tách trong split()

Nếu không truyền ký tự phân tách khi dùng `split()`, chuỗi sẽ không được chia thành các phần tử như mong muốn.

**Lưu ý quan trọng**: Trong JavaScript, các giá trị nguyên thủy là bất biến(immutable) - một khi giá trị nguyên thủy được tạo, nó không thể thay đổi được, mặc dù biến chứa nó có thể được gán lại một giá trị khác. Ngược lại, object  có thể thay đổi(mutable) theo mặc định — các thuộc tính và thành phần của chúng có thể được thay đổi mà không cần gán lại giá trị mới. Thế nên các phương thức làm việc với giá trị nguyên thuỷ đều tạo ra giá trị mới mà không làm thay đổi giá trị gốc.

{% hint style="info" %}
Tóm tắt

* **concat() là gì?**: `concat()` được sử dụng để nối hai hoặc nhiều chuỗi với nhau.
  * **Cú pháp**: `str1.concat(str2, str3, ..., strN);`
  *   **Ví dụ**:

      ```js
      let greeting = "Hello, ";
      let name = "Alice";
      let fullGreeting = greeting.concat(name);
      console.log(fullGreeting); // "Hello, Alice"
      ```

      Copy
* **slice() là gì?**: `slice()` được sử dụng để trích xuất một phần của chuỗi cha và trả về chuỗi con mới.
  * **Cú pháp**: `str.slice(startIndex, endIndex);`
  *   **Ví dụ**:

      ```js
      let text = "Hello, world!";
      let result = text.slice(0, 5);
      console.log(result); // "Hello"
      ```
* **substring() là gì?**: `substring()` được sử dụng để trích xuất các ký tự trong chuỗi giữa hai chỉ mục.
  * **Cú pháp**: `str.substring(startIndex, endIndex);`
  *   **Ví dụ**:

      ```js
      let text = "Hello, world!";
      let result = text.substring(0, 5);
      console.log(result); // "Hello"
      ```
  * **Khác biệt so với slice()**:
    * `substring()` hoán đổi `start` và `end` nếu `start` lớn hơn `end`, không hỗ trợ chỉ mục âm.
    * `slice()` trả về chuỗi rỗng nếu `start` lớn hơn `end`, hỗ trợ chỉ mục âm tính từ cuối chuỗi.
* **split() là gì?**: `split()` được sử dụng để chia một chuỗi thành một mảng các chuỗi con, dựa trên một ký tự phân tách.
  * **Cú pháp**: `str.split(separator, limit);`
  *   **Ví dụ**:

      ```js
      let text = "apple, banana, cherry";
      let result = text.split(", ");
      console.log(result); // ["apple", "banana", "cherry"]
      ```
* **Các sai lầm thường gặp**:
  * **Sử dụng sai chỉ mục trong slice() và substring()**: Nhập chỉ số không hợp lý có thể dẫn đến kết quả không mong muốn.
  * **Không truyền ký tự phân tách trong split()**: Chuỗi sẽ không được chia thành các phần tử như mong muốn nếu thiếu ký tự phân tách.
{% endhint %}
