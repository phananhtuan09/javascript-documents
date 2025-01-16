# Kiểu dữ liệu trong JavaScript

Mục lục

* [Kiểu dữ liệu trong JavaScript](kieu-du-lieu-trong-javascript.md#kieu-du-lieu-trong-javascript)
  * [String (Chuỗi)](kieu-du-lieu-trong-javascript.md#string-chuoi)
  * [Number (Số)](kieu-du-lieu-trong-javascript.md#number-so)
  * [BigInt (Số lớn)](kieu-du-lieu-trong-javascript.md#bigint-so-lon)
  * [Boolean (Đúng/Sai)](kieu-du-lieu-trong-javascript.md#boolean-dung-sai)
  * [Undefined (Không xác định/Chưa được khởi tạo)](kieu-du-lieu-trong-javascript.md#undefined-khong-xac-dinh-chua-duoc-khoi-tao)
  * [Null (Chưa có gì/Trống rỗng)](kieu-du-lieu-trong-javascript.md#null-chua-co-gi-trong-rong)
  * [Symbol (Giá trị duy nhất)](kieu-du-lieu-trong-javascript.md#symbol-gia-tri-duy-nhat)
  * [Object (Đối tượng)](kieu-du-lieu-trong-javascript.md#object-doi-tuong)
* [Dạng đặc biệt của Object](kieu-du-lieu-trong-javascript.md#dang-dac-biet-cua-object)
  * [Array (Mảng)](kieu-du-lieu-trong-javascript.md#array-mang)
  * [Function (Hàm)](kieu-du-lieu-trong-javascript.md#function-ham)
* [Những tình huống giá trị “undefined” xuất hiện?](kieu-du-lieu-trong-javascript.md#nhung-tinh-huong-gia-tri-undefined-xuat-hien)
  * [Biến được khai báo nhưng chưa được gán giá trị](kieu-du-lieu-trong-javascript.md#bien-duoc-khai-bao-nhung-chua-duoc-gan-gia-tri)
  * [Một hàm không trả về giá trị](kieu-du-lieu-trong-javascript.md#mot-ham-khong-tra-ve-gia-tri)
  * [Đối số không được truyền vào hàm](kieu-du-lieu-trong-javascript.md#doi-so-khong-duoc-truyen-vao-ham)
  * [Truy cập một thuộc tính không tồn tại của một đối tượng](kieu-du-lieu-trong-javascript.md#truy-cap-mot-phan-tu-khong-ton-tai-trong-mot-mang)
  * [Truy cập một phần tử không tồn tại trong một mảng](kieu-du-lieu-trong-javascript.md#truy-cap-mot-phan-tu-khong-ton-tai-trong-mot-mang)
* [Sai lầm thường gặp](kieu-du-lieu-trong-javascript.md#sai-lam-thuong-gap)
  * [Nhầm lẫn giữa String và Number](kieu-du-lieu-trong-javascript.md#nham-lan-giua-string-va-number)
  * [Không hiểu rõ sự khác biệt giữa Null và Undefined](kieu-du-lieu-trong-javascript.md#khong-hieu-ro-su-khac-biet-giua-null-va-undefined)
  * [Không kiểm tra kiểu dữ liệu trước khi xử lý](kieu-du-lieu-trong-javascript.md#khong-kiem-tra-kieu-du-lieu-truoc-khi-xu-ly)

### Kiểu dữ liệu trong JavaScript

Trong JavaScript có 8 kiểu dữ liệu bao gồm:

1. String
2. Number
3. Bigint
4. Boolean
5. Undefined
6. Null
7. Symbol
8. Object

Sự khác biệt giữa các kiểu dữ liệu chủ yếu nằm ở mục đích sử dụng, cách chúng lưu trữ và cách thức làm việc với chúng.

#### String (Chuỗi)

Sử dụng khi cần biểu diễn văn bản.

Ví dụ: Lưu tên người dùng.

```javascript
let userName = "Nguyễn Văn A";

console.log(typeof userName); // string
```

> _Sử dụng `typeof` để kiểm tra kiểu dữ liệu của một biến, lệnh này sẽ trả về một chuỗi._

**Quy ước đặt tên**: Không có quy ước cụ thể, đặt tên biến tùy theo ý nghĩa giá trị của biến sẽ lưu trữ.

#### Number (Số)

Sử dụng khi làm việc với toán học và số học.

Ví dụ: Tính tuổi từ ngày sinh.

```javascript
let birthYear = 1990;
let currentYear = 2024;
let age = currentYear - birthYear;

console.log(typeof birthYear); // number
```

**Quy ước đặt tên**: Không có quy ước cụ thể, đặt tên biến tùy theo ý nghĩa giá trị của biến sẽ lưu trữ.

#### BigInt (Số lớn)

Khi bạn cần đại diện cho các số lớn, mà giá trị của chúng vượt quá giới hạn của kiểu `Number` thông thường (`2^53 - 1`, tương đương khoảng `9007199254740991`).

Ví dụ: Tính toán trong lĩnh vực tài chính, khoa học, hoặc kỹ thuật, nơi cần sự chính xác với các con số cực lớn.

Ví dụ: Tính toán với số lượng lớn.

```javascript
let largeNumber = BigInt("9007199254740991");
let bigNumber = 9007199254740991n;

console.log(typeof largeNumber); // bigint
console.log(typeof bigNumber); // bigint
```

**Quy ước đặt tên**: Thường thêm “Big” hoặc “Large” vào tên để phản ánh sự lớn của số.

* Ví dụ: `let largeNumber = BigInt("9007199254740991");`

#### Boolean (Đúng/Sai)

Sử dụng khi cần biểu diễn đúng/sai hoặc có/không.

Ví dụ: Kiểm tra người dùng đã đăng nhập hay chưa.

```javascript
let isLoggedIn = true;

console.log(typeof isLoggedIn); // boolean
```

**Quy ước đặt tên**: Thường bắt đầu với các từ như ‘is’, ‘can’, ‘has’, ‘should’ để phản ánh rõ ràng giá trị đúng/sai.

* Ví dụ: `let isLoggedIn = true;`

#### Undefined (Không xác định/Chưa được khởi tạo)

Sử dụng khi một biến được khai báo nhưng chưa được gán giá trị.

Ví dụ: Khai báo biến mà chưa gán giá trị.

```javascript
let userLocation;

console.log(typeof userLocation); // undefined
```

#### Null (Chưa có gì/Trống rỗng)

Sử dụng khi cần thể hiện rằng một biến chưa có giá trị cụ thể, hoặc không tìm thấy dữ liệu, v.v.

Ví dụ: Thể hiện không tìm thấy đối tượng.

```javascript
let searchResult = null;

console.log(typeof searchResult); // object
```

> _Trong JavaScript, mặc dù `null` không phải là một đối tượng, nhưng do cách JavaScript được thiết kế, `typeof` trả về `"object"` cho `null`. Điều này được biết đến là một “bug” hay sai sót của ngôn ngữ, nhưng nó đã trở thành một phần của tiêu chuẩn và cần phải được nhớ khi kiểm tra kiểu dữ liệu của một biến._

**Quy ước đặt tên**: Không có quy ước cụ thể, đặt tên biến tùy theo ý nghĩa giá trị của biến sẽ lưu trữ.

#### Symbol (Giá trị duy nhất)

Sử dụng khi cần tạo ra một giá trị duy nhất.

Ví dụ: Tạo một ID duy nhất.

```javascript
let uniqueId = Symbol('id');

console.log(typeof uniqueId); // symbol
```

**Quy ước đặt tên**: Không có quy ước cụ thể, đặt tên biến tùy theo ý nghĩa giá trị của biến sẽ lưu trữ.

#### Object (Đối tượng)

Sử dụng khi cần lưu trữ và quản lý dữ liệu theo cấu trúc `key-value` (_khóa & giá trị_).

Ví dụ: Lưu trữ thông tin người dùng.

```javascript
let user = {
  name: "Nguyễn Văn A",
  age: 30
};

console.log(typeof user); // object
```

**Quy ước đặt tên**: Thường là sử dụng danh từ số ít, mô tả cho thực thể mà nó đại diện.

* Ví dụ 1: `let user = {name: "Nguyễn Văn A", age: 30};`.
* Ví dụ 2: `let product = {id: 1, name: "Điện thoại", price: 500};`.

Trong JavaScript, kiểu dữ liệu `BigInt` và `Symbol` là những kiểu ít được sử dụng nhất, so với các kiểu dữ liệu khác như `String`, `Number`, `Boolean`, `Object`, `null`, và `undefined`. Lý do chính cho việc sử dụng ít hơn của `BigInt` và `Symbol` có thể được giải thích như sau:

* **BigInt**: `BigInt` được sử dụng chủ yếu khi làm việc với các số rất lớn mà kiểu `Number` thông thường không thể xử lý chính xác (số lớn hơn `2^53 - 1`). Trong thực tế lập trình hàng ngày, tình huống yêu cầu xử lý các số lớn đến mức này khá hiếm gặp.
* **Symbol**: `Symbol` được thiết kế để tạo các thuộc tính duy nhất cho các đối tượng, nhưng nhu cầu này không phải là phổ biến trong mọi ứng dụng JavaScript. `Symbol` thường được sử dụng trong các trường hợp cần đảm bảo tính duy nhất hoặc tránh xung đột tên thuộc tính.

***

### Dạng đặc biệt của Object

#### &#x20;Array (Mảng)

Sử dụng khi cần lưu trữ một danh sách các mục, chẳng hạn như danh sách tên các sản phẩm.

Ví dụ:

```js
let products = ["iPhone", "Samsung Galaxy", "Google Pixel"];

console.log(typeof products); // object
```

**Quy ước đặt tên**: Số nhiều, thể hiện rằng biến chứa nhiều mục.

* Ví dụ 1: `let fruits = ["Apple", "Banana", "Cherry"];`.
* Ví dụ 2: `let colors = ["Red", "Pink", "Orange"];`.

#### Function (Hàm)

Sử dụng khi cần thực hiện một tác vụ lặp đi lặp lại, ví dụ như tính toán giá sau thuế.

Ví dụ:

```js
function calculateTax(price) {
  const taxRate = 0.1;
  return price * (1 + taxRate);
}

console.log(typeof calculateTax); // function
```

**Quy ước đặt tên**: Thường bắt đầu với một động từ, mô tả hành động của hàm.

* Ví dụ 1: `function calculateArea(width, height) {...}`.
* Ví dụ 2: `function createLink(url, displayName) {...}`.

> _Trong JavaScript còn nhiều dạng Object đặc biệt khác như: `Map`, `Set`, v.v. Chúng ta sẽ cùng tìm hiểu chúng trong các phần nâng cao hơn trong tương lai nhé._

***

### Những tình huống giá trị “undefined” xuất hiện?

Trong JavaScript, có một số tình huống cụ thể mà giá trị `undefined` sẽ xuất hiện. `undefined` thường được sử dụng để biểu thị một trạng thái “không xác định” hoặc “chưa được khởi tạo”. Dưới đây là một số tình huống điển hình:

#### Biến được khai báo nhưng chưa được gán giá trị

Ví dụ:

```javascript
let example;
console.log(example); // undefined
```

#### Một hàm không trả về giá trị

Một hàm mà không có lệnh `return` hoặc có lệnh `return` nhưng không có giá trị trả về sẽ trả về `undefined`.

Ví dụ:

```javascript
function testFunction() {
  let a = 1 + 2; // không có lệnh return
}
let result = testFunction();
console.log(result); // undefined
```

#### Đối số không được truyền vào hàm

Nếu một hàm được gọi mà không cung cấp đủ đối số, các tham số tương ứng sẽ có giá trị `undefined`.

Ví dụ:

```javascript
function greet(name) {
  return "Hello " + name;
}
console.log(greet()); // Hello undefined
```

#### Truy cập một thuộc tính không tồn tại của một đối tượng

Nếu bạn cố gắng truy cập một thuộc tính không tồn tại trên một đối tượng, bạn sẽ nhận được `undefined`.

Ví dụ:

```javascript
let obj = {name: "Nguyễn Văn A"};
console.log(obj.age); // undefined
```

#### Truy cập một phần tử không tồn tại trong một mảng

Tương tự như với đối tượng, truy cập một chỉ số không tồn tại trong mảng sẽ trả về `undefined`.

Ví dụ:

```javascript
let arr = [1, 2, 3];
console.log(arr[5]); // undefined
```

***

### Sai lầm thường gặp

#### Nhầm lẫn giữa String và Number

Sử dụng chuỗi ký tự như số và ngược lại, dẫn đến lỗi trong phép tính hoặc so sánh. Ví dụ: `'2' + 2` kết quả là `'22'` chứ không phải `4`.

#### Không hiểu rõ sự khác biệt giữa Null và Undefined

Sai lầm thường gặp là xem chúng như là một, trong khi mỗi loại đều có ý nghĩa riêng biệt.

**Sự khác biệt chính**

* **Khác biệt về ý nghĩa**: Sử dụng `undefined` để biểu thị trạng thái “chưa được khởi tạo” hoặc “chưa được định nghĩa”, còn `null` để biểu thị một sự “trống rỗng” hay “không có gì” có chủ đích.
* **Khác biệt về chủ đích sử dụng**: Một biến được gọi là `null` khi nó được gán `null` có chủ đích (_chúng ta tạo biến và chủ động gán `null` cho biến đó_). Ngược lại, một biến là `undefined` khi bạn khai báo nó mà không gán giá trị (_và một số trường hợp khác cũng xuất hiện `undefined`_).

**Ví dụ: Khởi tạo biến cho đối tượng chưa tồn tại**

Trong trường hợp bạn đang lập trình một ứng dụng và bạn muốn khởi tạo một biến để lưu trữ một đối tượng (như đối tượng người dùng, đối tượng sản phẩm, v.v.), nhưng tại thời điểm khởi tạo bạn chưa có đối tượng cụ thể để gán.

```javascript
let currentUser = null;

// Sau đó, khi người dùng đăng nhập thành công
if (isLoggedIn) {
  currentUser = { name: "Nguyễn Văn A", age: 30 }
};
```

**Ví dụ: Trả về null khi không tìm thấy trong bài toán tìm kiếm**

Khi thực hiện tìm kiếm và bạn muốn biểu thị rằng không có kết quả nào được tìm thấy hoặc một quá trình tìm kiếm đã kết thúc mà không có kết quả.

```js
function findItemInArray(arr, itemToFind) {
  for (let i = 0; i < arr.length; i++) {
    if (arr[i] === itemToFind) {
      return i; // Trả về chỉ số nếu tìm thấy
    }
  }
  return null; // Trả về null nếu không tìm thấy
}
```

**Ví dụ: Reset giá trị của biến**

Khi bạn muốn reset giá trị của một biến, biểu thị rằng biến đó hiện tại khôn có giá trị hoặc không cần thiết nữa.

```js
let selectedFile = {
  name: "resume.pdf",
  size: "2MB"
};

// Ví dụ: Sau một hành động người dùng xóa file đã chọn
if (isFileDeleted) {
  selectedFile = null; // Loại bỏ giá trị trước đó của biến
}
```

**Ví dụ: Thể hiện một tham số là không bắt buộc**

Khi một hàm có tham số không bắt buộc, và bạn muốn biểu thị rằng đối số đó không được truyền vào hoặc không cần thiết.

```js
function createProfile(name, age, address = null) {
  //  Logic xử lý của hàm
}

createProfile("Nguyễn Văn A", 30); // Không cần địa chỉ
```

#### Không kiểm tra kiểu dữ liệu trước khi xử lý

Giả sử bạn đang viết một hàm để xử lý thông tin người dùng, trong đó bạn cần tính tuổi từ năm sinh. Nếu năm sinh không phải là một số, hàm này sẽ không hoạt động đúng cách.

Ví dụ:

```js
function calculateAge(currentYear, birthYear) {
  return currentYear - birthYear;
}

// Gọi hàm với chuỗi ký tự
console.log(calculateAge(2024, "ABC")); // NaN
```

Trong ví dụ trên, hàm `calculateAge` được gọi với một chuỗi “ABC” thay vì một số. Điều này dẫn đến kết quả `NaN` (_Not a Number_), vì JavaScript chuyển đổi `"ABC"` thành kiểu số.

Cải thiện lại:

```js
function calculateAge(currentYear, birthYear) {
  if (typeof currentYear !== 'number' || typeof birthYear !== 'number') {
    return 'Invalid input';
  }
  return currentYear - birthYear;
}

// Gọi hàm với chuỗi ký tự
console.log(calculateAge(1990, "ABC")); // "Invalid input"
```

Trong ví dụ cải thiện, hàm `calculateAge` bây giờ kiểm tra xem `birthYear` có phải là kiểu `number` hay không trước khi thực hiện phép tính. Nếu không phải, hàm sẽ trả về một thông báo lỗi thay vì cố gắng tính toán với dữ liệu không hợp lệ. Điều này giúp tránh lỗi và làm cho hàm hoạt động chính xác hơn với các loại dữ liệu khác nhau.

{% hint style="info" %}
Tóm tắt

* **Kiểm tra kiểu dữ liệu**: Sử dụng `typeof` để kiểm tra kiểu dữ liệu của một giá trị. Lệnh này sẽ trả về một chuỗi là tên của kiểu dữ liệu.
* **Kiểu dữ liệu String**: Dùng cho văn bản. Ví dụ: tên người dùng, địa chỉ, email, v.v.
* **Kiểu dữ liệu Number**: Dùng cho toán học và số học. Ví dụ: tính tuổi.
* **Kiểu dữ liệu BigInt**: Dùng cho số rất lớn, vượt quá giới hạn của `Number` là `2^53 - 1` (_ít khi dùng tới_).
* **Kiểu dữ liệu Boolean**: Dùng cho giá trị đúng/sai. Ví dụ: kiểm tra trạng thái đăng nhập.
* **Kiểu dữ liệu Undefined**: Cho biến chưa được gán giá trị.
* **Kiểu dữ liệu Null**: Dùng để đánh dấu biến chưa có giá trị cụ thể / trống rỗng. Lưu ý, `typeof null` trả về `"object"`, một đặc điểm kỹ thuật của JavaScript mà bạn cần ghi nhớ.
* **Kiểu dữ liệu Symbol**: Dùng để tạo giá trị duy nhất không lặp lại (_ít khi dùng tới_).
* **Kiểu dữ liệu Object**: Dùng cho cấu trúc dữ liệu phức tạp như thông tin người dùng, danh sách sản phẩm (_Array_).
* **Undefined xuất hiện khi**: Khi biến được khai báo mà không gán giá trị, hàm không có giá trị trả về, thuộc tính đối tượng hoặc phần tử mảng không tồn tại, tham số hàm bị thiếu.
* **Sai lầm thường gặp**: Nhầm lẫn giữa `String` và `Number`, không hiểu sự khác biệt giữa `Null` và `Undefined`, không kiểm tra kiểu dữ liệu trước khi xử lý.
{% endhint %}

