# Nối chuỗi và nội suy

Mục lục

* [Tìm hiểu về chuỗi](noi-chuoi-va-noi-suy.md#tim-hieu-ve-chuoi)
  * [Chuỗi là gì?](noi-chuoi-va-noi-suy.md#chuoi-la-gi)
  * [Tạo chuỗi với nháy đơn](noi-chuoi-va-noi-suy.md#tao-chuoi-voi-nhay-don)
  * [Tạo chuỗi với nháy kép](noi-chuoi-va-noi-suy.md#tao-chuoi-voi-nhay-kep)
  * [Tạo chuỗi với backticks](noi-chuoi-va-noi-suy.md#tao-chuoi-voi-backticks)
* [Nối chuỗi](noi-chuoi-va-noi-suy.md#noi-chuoi)
  * [Toán tử nối chuỗi](noi-chuoi-va-noi-suy.md#toan-tu-noi-chuoi)
  * [Ví dụ nối chuỗi](noi-chuoi-va-noi-suy.md#vi-du-noi-chuoi)
  * [Lưu ý khi sử dụng](noi-chuoi-va-noi-suy.md#luu-y-khi-su-dung)
* [Template literals](noi-chuoi-va-noi-suy.md#template-literals)
  * [Template literals là gì?](noi-chuoi-va-noi-suy.md#template-literals-la-gi)
  * [Nội suy chuỗi](noi-chuoi-va-noi-suy.md#noi-suy-chuoi)
  * [Ví dụ nội suy chuỗi](noi-chuoi-va-noi-suy.md#vi-du-noi-suy-chuoi)
* [Lỗi thường gặp](noi-chuoi-va-noi-suy.md#loi-thuong-gap)

### Tìm hiểu về chuỗi

#### Chuỗi là gì?

Chuỗi là một kiểu dữ liệu trong JavaScript, được sử dụng để biểu diễn văn bản. Để tạo chuỗi ta có thể sử dụng dấu nháy đơn `'`, dấu nháy kép `"` hoặc backticks `` ` `` bao quanh văn bản.

Ví dụ:

```js
'This is a string!'; // Tạo chuỗi với nháy đơn
"This is another string"; // Tạo chuỗi với nháy kép
`This is yet another string!`; // Tạo chuỗi với backticks
```

**Lưu ý**: phím `` ` `` nằm bên dưới phím ESC (hoặc bên trên phím TAB).

#### &#x20;Tạo chuỗi với nháy đơn

* **Đặc điểm**: Đây là cách truyền thống nhất để tạo chuỗi.
* **Ứng dụng**: Được sử dụng phổ biến cho các chuỗi đơn giản, không cần xuống dòng. Rất hữu ích khi chuỗi chứa các dấu nháy kép bên trong.
* **Ví dụ**: `'Xin chào, đây là "JavaScript"!'`

#### Tạo chuỗi với nháy kép

* **Đặc điểm**: Tương tự dấu nháy đơn nhưng thường được sử dụng khi chuỗi chứa dấu nháy đơn.
* **Ứng dụng**: Hữu ích khi bạn muốn bao gồm dấu nháy đơn trong chuỗi mà không cần dùng ký tự thoát ([_Escape character_](https://javascript.fullstack.edu.vn/?id=21006420-4d65-4c76-8acf-77fe76f8cc6f)).
* **Ví dụ**: `"Đây là 'JavaScript'!"`

#### Tạo chuỗi với backticks

* **Đặc điểm**: Hỗ trợ nội suy chuỗi (cho phép chèn biến hoặc biểu thức vào chuỗi), và cho phép xuống dòng trực tiếp trong chuỗi.
* **Ứng dụng**: Cực kỳ hữu ích khi cần kết hợp chuỗi với biến hoặc khi cần tạo chuỗi nhiều dòng.
* **Ví dụ**:

```js
let name = "JavaScript";

`Xin chào, đây là ${name}!
Chúng ta có thể xuống dòng trực tiếp.`;
```

Sử dụng `${name}` bên trong backticks được gọi là “Nội suy”, điều này sẽ được nhắc tới ở phía dưới.

> Tạo chuỗi với dấy nháy đơn và nháy kép không hỗ trợ nội suy.

***

### Nối chuỗi

#### Toán tử nối chuỗi

Toán tử nối chuỗi cho phép kết hợp hai hoặc nhiều chuỗi thành một. Điều này đạt được bằng cách sử dụng ký tự `+` để nối các chuỗi lại với nhau.

```js
// Nối chuỗi
let greeting = "Xin chào, " + "tôi là " + "Huy.";

console.log(greeting); // Xin chào, tôi là Huy.
```

> _**Lý do sử dụng**: Nối chuỗi hữu ích trong việc tạo ra kết quả động, ví dụ kết hợp tên người dùng với một thông điệp chào mừng._

#### Ví dụ nối chuỗi

Nối chuỗi với chuỗi:

```js
'Xin' + ' ' + 'chào!'; // 'Xin chào!'
```

Chuỗi lưu vào biến sau đó nối:

```js
let greeting = 'Xin';
let message = greeting + ' chào!';

console.log(message); // Xin chào!
```

Chuỗi chứa nháy đơn:

```js
let message = "Đây là chuỗi chứa dấu nháy đơn: I'm learning JavaScript!";
console.log(message); // Đây là chuỗi chứa dấu nháy đơn: I'm learning JavaScript!
```

Chuỗi chứa nháy kép:

```js
let message = 'Đây là chuỗi chứa dấu nháy kép: "JavaScript is fun!"';
console.log(message); // Đây là chuỗi chứa dấu nháy kép: "JavaScript is fun!"
```

#### Lưu ý khi sử dụng

Khi sử dụng toán tử nối chuỗi (`+`) trong JavaScript, điều quan trọng cần lưu ý là sự khác biệt giữa nối chuỗi và cộng số. Toán tử `+` có thể gây nhầm lẫn vì nó được sử dụng cho cả hai mục đích này.

Theo bạn, đoạn code dưới đây có kết quả là gì?

```js
'2' + 2; // ?
```

Không phải `4`, thực tế nó là `'22'`:

```js
'2' + 2; // '22'
```

JavaScript xác định hành vi của toán tử `+` dựa trên kiểu dữ liệu của các toán hạng. Nếu một trong các toán hạng là chuỗi, `+` sẽ thực hiện nối chuỗi. Nếu cả hai toán hạng đều là số, `+` sẽ thực hiện phép cộng.

**Thứ tự thực hiện của các phép toán**

Thứ tự các toán hạng và toán tử quyết định kết quả của biểu thức. Ví dụ: `3 + 4 + "5"` sẽ trả về `"75"` chứ không phải `"345"` vì phép cộng số được thực hiện trước, sau đó kết quả được nối với chuỗi `"5"`.

**Chuyển đổi kiểu dữ liệu tự động**

JavaScript thực hiện chuyển đổi kiểu dữ liệu tự động trong một số trường hợp. Ví dụ: `"3" + 4 + 5` sẽ trả về `"345"` chứ không phải `12` vì `"3"` là chuỗi, khiến các số tiếp theo được chuyển đổi thành chuỗi và nối lại.

**Làm sao để tránh nhầm lẫn?**

Để tránh nhầm lẫn, nên tránh sử dụng toán tử `+` cho cả nối chuỗi và cộng số trong cùng một biểu thức. Nên sử dụng dấu ngoặc đơn `()` hoặc tách biểu thức thành các biến riêng biệt.

Cách làm sai:

```js
let a = 10;
let b = 20;
let message = 'Tổng của ' + a + ' và ' + b + ' là: ' + a + b;
console.log(message); // Tổng của 10 và 20 là: 1020
```

Cách làm đúng (cách 1):

```js
let a = 10;
let b = 20;
let message = 'Tổng của ' + a + ' và ' + b + ' là: ' + (a + b);

console.log(message); // Tổng của 10 và 20 là: 30
```

Cách làm đúng (cách 2):

```js
let a = 10;
let b = 20;
let total = a + b; // Thực hiện phép cộng trước
let message = 'Tổng của ' + a + ' và ' + b + ' là: ' + total;

console.log(message); // Tổng của 10 và 20 là: 30
```

Cách làm đúng (cách 3 - nên dùng cách này):

```js
let a = 10;
let b = 20;
let total = a + b; // Thực hiện phép cộng trước
let message = `Tổng của ${a} và ${b} là: ${total}`;

console.log(message); // Tổng của 10 và 20 là: 30
```

Cách số 3 nên dùng vì: Việc tách biến `total` và dùng _Template literals_ (hỗ trợ nội suy) giúp code có ý nghĩa và dễ đọc hơn.

***

### Template literals

#### Template literals là gì?

Đây là một tính năng mới được giới thiệu trong ECMAScript 2015 (còn được gọi là ES6). Template Literals sử dụng backticks (`` ` ``) để định nghĩa chuỗi thay vì dấu nháy đơn hoặc nháy kép.

Điểm đặc biệt của Template Literals là khả năng thực hiện nội suy - tức là chèn biến hoặc biểu thức trực tiếp vào trong chuỗi. Điều này được thực hiện thông qua cú pháp `${expression}`.

Ngoài ra, Template Literals còn hỗ trợ việc tạo chuỗi đa dòng mà không cần sử dụng các ký tự xuống dòng như .

> “Template literals” còn được gọi là “Template strings”. Cả hai cách gọi đều nói tới việc sử dụng _backticks_ để tạo chuỗi với đặc điểm là cho phép nội suy - tức là chèn biến hoặc biểu thức trực tiếp vào trong chuỗi.

#### Nội suy chuỗi

Nội suy chuỗi cho phép chèn trực tiếp các biến hoặc biểu thức vào trong một chuỗi. Điều này được thực hiện thông qua cú pháp `` ` ` ``, `$` và `{}`.

```js
// Nội suy chuỗi
let name = "Linh";
let story = `Và đây là câu chuyện của ${name}.`;

console.log(story); // Và đây là câu chuyện của Linh.
```

#### Ví dụ nội suy chuỗi

Nội suy biến vào chuỗi:

```js
let language = "JavaScript";
let message = `Tôi đang học ${language}!`;

console.log(message); // Tôi đang học JavaScript!
```

Chuỗi nhiều dòng:

```js
let message = `Xin chào, đây là JavaScript!
Chúng ta có thể xuống dòng trực tiếp.`;

console.log(message); // Xin chào, đây là JavaScript!
// Chúng ta có thể xuống dòng trực tiếp.
```

Nội suy và nhiều dòng (ví dụ 1):

```js
let name = "JavaScript";

let message = `Xin chào, đây là ${name}!
Chúng ta có thể xuống dòng trực tiếp.`;

console.log(message); // Xin chào, đây là JavaScript!
// Chúng ta có thể xuống dòng trực tiếp.
```

Nội suy và nhiều dòng (ví dụ 2):

```js
let part1 = 'Học lập trình';
let part2 = 'không khó.';
let combined = `${part1}
${part2}`;

console.log(combined); // Học lập trình
// không khó.
```

Chuỗi chứa nháy đơn và nháy kép:

```js
let quote = `She said, "I'm learning JavaScript!"`;

console.log(quote); // She said, "I'm learning JavaScript!"
```

***

### Lỗi thường gặp

* **Sử dụng nhầm ký tự tạo chuỗi**: Trong chuỗi tạo bởi dấu nháy đơn lại chứa dấu nháy đơn mà không sử dụng ký tự thoát, và tương tự với chuỗi tạo bởi dấu nháy kép và backticks.
* **Nhầm lẫn giữa nối chuỗi và cộng số**: `"2" + 2 sẽ trả về "22" chứ không phải 4.`

{% hint style="info" %}
Tóm tắt

* **Chuỗi trong JavaScript**:
  * Chuỗi là kiểu dữ liệu dùng để biểu diễn văn bản.
  * Có thể tạo chuỗi bằng dấu nháy đơn (`' '`), nháy kép (`" "`) hoặc backticks (`` ` `` `` ` ``).
* **Nối chuỗi**:
  * Sử dụng toán tử `+` để nối các chuỗi.
  * Lưu ý sự khác biệt giữa nối chuỗi và cộng số.
* **Template literals**:
  * Sử dụng backticks để tạo chuỗi đa năng hơn.
  * Hỗ trợ nội suy biến và biểu thức (`${expression}`).
  * Cho phép xuống dòng trực tiếp trong chuỗi.
* **Các lưu ý quan trọng**:
  * Chú ý đến loại dấu nháy sử dụng để tránh lỗi.
  * Phân biệt rõ ràng giữa nối chuỗi và cộng số.
  * Tránh sử dụng `+` cho cả nối chuỗi và cộng số trong cùng một biểu thức.
{% endhint %}

