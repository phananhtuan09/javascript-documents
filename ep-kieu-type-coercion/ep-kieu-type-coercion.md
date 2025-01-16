# Ép kiểu (Type coercion)

Mục lục

* [Ép kiểu là gì?](ep-kieu-type-coercion.md#ep-kieu-la-gi)
* [Ép kiểu rõ ràng và ép kiểu ngầm](ep-kieu-type-coercion.md#ep-kieu-ro-rang-va-ep-kieu-ngam)
  * [Ép kiểu rõ ràng](ep-kieu-type-coercion.md#ep-kieu-ro-rang)
  * [Ép kiểu ngầm](ep-kieu-type-coercion.md#ep-kieu-ngam)
* [Các trường hợp ép kiểu phổ biến](ep-kieu-type-coercion.md#cac-truong-hop-ep-kieu-pho-bien)
  * [Ép kiểu sang chuỗi](ep-kieu-type-coercion.md#ep-kieu-sang-chuoi)
  * [Ép kiểu sang số](ep-kieu-type-coercion.md#ep-kieu-sang-so)
  * [Ép kiểu sang Boolean](ep-kieu-type-coercion.md#ep-kieu-sang-boolean)
  * [Tại sao ít khi chuyển kiểu dữ liệu khác sang Object?](ep-kieu-type-coercion.md#tai-sao-it-khi-chuyen-kieu-du-lieu-khac-sang-object)
* [Quy tắc ép kiểu ngầm](ep-kieu-type-coercion.md#quy-tac-ep-kieu-ngam)
  * [Ép kiểu ngầm với toán tử so sánh ==](ep-kieu-type-coercion.md#ep-kieu-ngam-voi-toan-tu-so-sanh)
  * [Ép kiểu ngầm với toán tử số học](ep-kieu-type-coercion.md#ep-kieu-ngam-voi-toan-tu-so-hoc)
  * [Ép kiểu ngầm với toán tử logic](ep-kieu-type-coercion.md#ep-kieu-ngam-voi-toan-tu-logic)
  * [Ép kiểu ngầm với đối tượng](ep-kieu-type-coercion.md#ep-kieu-ngam-voi-doi-tuong)
* [Bảng chuyển đổi kiểu dữ liệu](ep-kieu-type-coercion.md#bang-chuyen-doi-kieu-du-lieu)
* [Tóm tắt logic ép kiểu ngầm](ep-kieu-type-coercion.md#tom-tat-logic-ep-kieu-ngam)
  * [Ép kiểu thành boolean](ep-kieu-type-coercion.md#ep-kieu-thanh-boolean)
  * [Ép kiểu thành string](ep-kieu-type-coercion.md#ep-kieu-thanh-string)
  * [Ép kiểu thành number](ep-kieu-type-coercion.md#ep-kieu-thanh-number)
  * [Ngoại lệ](ep-kieu-type-coercion.md#ngoai-le)
  * [Ép kiểu với đối tượng](ep-kieu-type-coercion.md#ep-kieu-voi-doi-tuong)
* [Lưu ý quan trọng](ep-kieu-type-coercion.md#luu-y-quan-trong)

### Ép kiểu là gì?

Ép kiểu (_Type coercion_) trong JavaScript là quá trình chuyển đổi giá trị từ một kiểu dữ liệu này sang một kiểu khác. Điều này thường xảy ra tự động, chẳng hạn khi sử dụng toán tử so sánh `==` hoặc các toán tử số học như `+`, `-`, v.v.

Ví dụ:

```js
"3" + 2; // "32"
```

Ở đây, JavaScript đã tự động chuyển số `2` thành chuỗi và kết hợp nó với chuỗi `"3"`, tạo ra kết quả là `"32"`, không phải là `5`.

***

### Ép kiểu rõ ràng và ép kiểu ngầm

#### &#x20;Ép kiểu rõ ràng

Ép kiểu rõ ràng là khi bạn chủ động chuyển đổi kiểu dữ liệu bằng cách sử dụng các hàm như `Number()`, `String()`, `Boolean()`, v.v.

Ví dụ:

```js
Number("123"); // 123
```

Trong JavaScript, mỗi kiểu dữ liệu cơ bản đều có các hàm chuyển đổi tương ứng để thực hiện chuyển đổi giữa các kiểu.

* **Kiểu số (number)**: Có hàm `Number()` để chuyển đổi giá trị sang kiểu số.
* **Kiểu chuỗi (string)**: Có hàm `String()` để chuyển đổi giá trị sang kiểu chuỗi.
* **Kiểu boolean (boolean)**: Có hàm `Boolean()` để chuyển đổi giá trị sang kiểu boolean.
* **Đối tượng (object)**: Có hàm `Object()` để tạo hoặc chuyển đổi giá trị thành đối tượng.
* **Mảng (array)**: Có hàm `Array()` để tạo mảng mới hoặc chuyển đổi giá trị thành mảng.
* **Hàm (function)**: Có hàm `Function()` để tạo hàm mới.
* **null và undefined**: Không có hàm chuyển đổi kiểu dữ liệu tương ứng.

#### Ép kiểu ngầm

Ép kiểu ngầm xảy ra khi JavaScript tự động quyết định kiểu dữ liệu, thường là trong các phép toán và so sánh.

Ví dụ:

```js
5 + ""; // "5"
```

> _Hiểu rõ về ép kiểu trong JavaScript rất quan trọng để tránh những lỗi không mong muốn trong quá trình lập trình. Đặc biệt, nên chú ý đến những tình huống ép kiểu ngầm, vì chúng có thể dẫn đến hiểu nhầm._

***

### Các trường hợp ép kiểu phổ biến

#### Ép kiểu sang chuỗi

Bất kỳ kiểu dữ liệu nào trong JavaScript cũng có thể được chuyển đổi thành chuỗi. Dưới đây là 3 phương pháp phổ biến và ví dụ minh họa:

Cách 1: Sử dụng hàm `String()`.

```js
String(123); // "123"
```

Cách 2: Sử dụng phương thức `toString()`.

```js
(123).toString(); // "123"
// Lưu ý: không áp dụng được cho `null` và `undefined`
```

Cách 3: Nối chuỗi hoặc Template literals.

```js
`${123}`; // "123"
// hoặc
123 + ""; // "123"
```

**✅ BẢNG SO SÁNH CÁC CÁCH ÉP KIỂU SANG CHUỖI**

Bảng dưới đây cung cấp cái nhìn trực quan về điểm giống và khác nhau cho các cách ép kiểu sang chuỗi như `String()`, `.toString()`, toán tử `+` và Template literals.

| Phương thức                      | Mô tả                                                             | Lưu ý                                      | Ví dụ                         |
| -------------------------------- | ----------------------------------------------------------------- | ------------------------------------------ | ----------------------------- |
| `String(value)`                  | Chuyển đổi `value` sang chuỗi.                                    | Hoạt động với mọi kiểu dữ liệu.            | `String(123)` -> `"123"`      |
| `value.toString()`               | Chuyển đổi `value` sang chuỗi.                                    | Không hoạt động với `null` và `undefined`. | `(123).toString()` -> `"123"` |
| Template literals hoặc nối chuỗi | Chuyển đổi value sang chuỗi. Ví dụ: `${value}` hoặc `value + ""`. | Hoạt động với mọi kiểu dữ liệu.            | `123 + ""` -> `"123"`         |

#### &#x20;Ép kiểu sang số

Dưới đây là một số cách chuyển đổi giá trị sang kiểu số trong JavaScript, cùng với ví dụ minh họa:

Cách 1: Sử dụng hàm `Number()`.

```js
Number("456"); // 456
Number(true); // 1
Number(null); // 0
```

Cách 2: Sử dụng toán tử cộng `+`.

```js
+"456"; // 456
+true; // 1
+null; // 0
```

**Lưu ý**: Các giá trị `""` (chuỗi rỗng), `"0"` (chuỗi chứa số 0), `"000"`, `0`, `-0`, `null`, `false`, `[]` và `new Date(0)` khi ép kiểu sang Number sẽ trả về `0`.

Các giá trị là chuỗi không phải là số (`"abc"`), `undefined`, và `NaN` không chuyển đổi thành `0` khi sử dụng `Number()` hoặc `+`. Thay vào đó, chúng sẽ trả về [_NaN_](https://javascript.fullstack.edu.vn/?id=df97c0df-f598-4842-a0c5-82154316b67f) (_Not-a-Number_).

Ví dụ:

```js
Number("abc"); // NaN
Number(undefined); // NaN
```

Cách 3: Sử dụng `parseInt()` và `parseFloat()`.

```js
parseInt("123", 10); // 123
parseFloat("123.45"); // 123.45
```

**Lưu ý**: Cách hoạt động của `parseInt()` và `parseFloat()` khác với các cách ép kiểu sang Number ở trên. Cụ thể, nó hoạt động như sau:

* **Khi đầu vào là một chuỗi**: `parseInt()` và `parseFloat()` sẽ phân tích chuỗi đó để tìm số đầu tiên và chuyển số đó sang kiểu Number. Nếu không tìm thấy số nào, kết quả sẽ là `NaN`.
* **Khi đầu vào không phải chuỗi**: `parseInt()` và `parseFloat()` trước tiên sẽ chuyển giá trị đó thành chuỗi. Sau đó, thực hiện quá trình phân tích như bước trên.

**✅ BẢNG SO SÁNH CÁC CÁCH ÉP KIỂU SANG SỐ**

Bảng này cung cấp một cái nhìn nhanh về sự khác biệt và giống nhau giữa `Number(value)`, `+value`, và `parseFloat/parseInt(value)` khi chuyển đổi các loại giá trị khác nhau sang số trong JavaScript.

| Tính năng/Phương thức | `Number(value)` / `+value` | `parseFloat(value)` / `parseInt(value)`                    |
| --------------------- | -------------------------- | ---------------------------------------------------------- |
| Xử lý chuỗi           | Chặt chẽ                   | Linh hoạt                                                  |
| VD chuỗi phức tạp     | `"123abc" -> NaN`          | `parseFloat("123abc") -> 123`, `parseInt("123abc") -> 123` |
| Xử lý số thực         | Chính xác                  | `parseFloat` giữ nguyên, `parseInt` làm tròn xuống         |
| Xử lý boolean         | `true -> 1`, `false -> 0`  | `NaN`                                                      |
| Xử lý `null`          | `0`                        | `NaN`                                                      |
| Xử lý `undefined`     | `NaN`                      | `NaN`                                                      |

#### Ép kiểu sang Boolean

Có hai cách chính để chuyển đổi giá trị sang kiểu boolean:

Cách 1: Sử dụng hàm `Boolean()`.

```js
Boolean(1); // true
Boolean(0); // false
Boolean("hello"); // true
Boolean(""); // false
```

Cách 2: Sử dụng toán tử NOT hai lần `!!`

```js
!!0; // false
!!1; // true
```

Chỉ có 6 giá trị sau đây khi ép kiểu sang boolean sẽ trả về `false`: `false`, `0`, `""` (chuỗi rỗng), `null`, `undefined`, và `NaN`. Mọi giá trị khác khi ép sang boolean đều trở thành `true`.

#### Tại sao ít khi chuyển kiểu dữ liệu khác sang Object?

Trong JavaScript, việc chuyển đổi từ các kiểu dữ liệu đơn giản sang Object không phổ biến do cấu trúc dữ liệu và mức độ phức tạp khác nhau. Ví dụ, chuyển một số hoặc chuỗi thành Object có thể không mang lại giá trị thực tế và làm tăng độ phức tạp của code.

***

### Quy tắc ép kiểu ngầm

#### Ép kiểu ngầm với toán tử so sánh ==

Trong JavaScript, khi so sánh hai giá trị `x` và `y` với nhau bằng cách sử dụng `x == y`, kết quả sẽ trả về `true` hoặc `false`. Quá trình so sánh này được thực hiện như sau:

* Nếu `x` và `y` cùng kiểu dữ liệu:
  * Nếu cả hai là `undefined` hoặc `null`, trả về `true`.
  * Nếu là số:
    * Nếu một trong hai là `NaN`, trả về `false`.
    * Nếu cả hai số giống hệt nhau, trả về `true`.
  * Nếu là chuỗi, so sánh từng ký tự (_cùng độ dài và giống nhau từng ký tự theo vị trí_) để xác định chúng có giống hệt nhau không.
  * Nếu là boolean, trả về `true` nếu cả hai cùng `true` hoặc cùng `false`.
* Nếu `x` là `null` và `y` là `undefined`, hoặc ngược lại, trả về `true`.
* Nếu một trong hai là số và cái kia là chuỗi, chuyển đổi chuỗi thành số rồi so sánh.
* Nếu một trong hai là boolean, chuyển đổi boolean thành số rồi so sánh.
* Nếu một trong hai là đối tượng và cái kia là chuỗi hoặc số, chuyển đổi đối tượng thành giá trị nguyên thủy rồi so sánh.
* Nếu không thỏa mãn các trường hợp trên, trả về `false`.

> _Trong trường hợp “Nếu `x` là `null` và `y` là `undefined`, hoặc ngược lại, trả về `true`,” không có sự ép kiểu ngầm định giữa `null` và `undefined`. Đây là một quy tắc đặc biệt trong JavaScript khi sử dụng toán tử so sánh bằng lỏng lẻo (`==`). Theo quy tắc này, `null` và `undefined` được coi là bằng nhau mà không cần chuyển đổi kiểu dữ liệu của chúng. Điều này có nghĩa là không có sự chuyển đổi kiểu dữ liệu nào xảy ra; JavaScript đơn giản chỉ coi chúng là giống nhau trong trường hợp cụ thể này (so sánh `==`)._

> **NaN** không bằng bất cứ thứ gì kể cả chính nó

#### Ép kiểu ngầm với toán tử số học

**Toán tử cộng (+)**

Trong JavaScript, toán tử cộng (`+`) có thể thực hiện cả phép cộng số học và nối chuỗi. Cách hoạt động của nó được xác định như sau:

* Xem xét giá trị của biểu thức bên trái và bên phải của toán tử.
* Chuyển đổi giá trị này sang kiểu nguyên thủy (ToPrimitive).
* Nếu một trong hai giá trị sau khi chuyển đổi là chuỗi, thực hiện nối chuỗi.
* Nếu không, chuyển đổi cả hai giá trị sang số (ToNumber) và thực hiện phép cộng.

> Tóm lại một trong các toán hạng là chuỗi thì thực hiện cộng chuỗi, ngược lại chuyển đổi sang số để thực hiện phép cộng

Ví dụ:

* `"5" + 2` sẽ có kết quả là `"52"` (nối chuỗi).
* `5 + "2"` cũng sẽ trở thành `"52"`.
* `5 + 2` sẽ có kết quả là `7` (phép cộng số).

**Toán tử trừ (-)**

Toán tử trừ (`-`) chỉ thực hiện phép trừ số học. Trong quá trình này, toán tử trừ chuyển đổi cả hai giá trị sang số rồi mới thực hiện phép trừ.

* `5 - "2"` sẽ trả về `3` (chuyển `"2"` thành số).
* `"10" - "2"` sẽ trả về `8` (chuyển `"10"` và `"2"` thành số).

> _Tham khảo thêm:_ [_https://262.ecma-international.org/5.1/#sec-11.9.3_](https://262.ecma-international.org/5.1/#sec-11.9.3)

Ngoài toán tử  (-) còn có nhiều toán tử khác sẽ ép kiểu ngầm  sang số ví dụ:

* Toán tử so sánh (`>`, `<`, `<=`,`>=`)
* Toán tử bitwise ( `|` `&` `^` `~`)
* Toán tử số học (`*` `/` `%` )

Khi chuyển đổi một chuỗi thành một số, trước tiên, javascript sẽ cắt bớt khoảng trắng ở đầu và cuối, \n, \t ký tự, trả về **NaN** nếu chuỗi đã cắt không biểu thị một số hợp lệ. Nếu chuỗi rỗng, nó sẽ trả về 0.

**null** và **undefined** được xử lý khác nhau: null trở thành 0, trong khi undefined trở thành NaN.

#### Ép kiểu ngầm với toán tử logic

Ép kiểu ngầm sang boolean  xảy ra trong ngữ cảnh logic hoặc được kích hoạt bởi các toán tử logic ( `||` `&&`  `!`) .

```javascript
if (2) { ... }      // implicit due to logical context
!!2                 // implicit due to logical operator
2 || 'hello'        // implicit due to logical operator
```

&#x20;Lưu ý: các toán tử logic như || và && thực hiện chuyển đổi boolean nội bộ, nhưng thực tế trả về giá trị của toán hạng gốc, ngay cả khi chúng không phải là boolean.

```javascript
// returns number 123, instead of returning true
// 'hello' and 123 are still coerced to boolean internally to calculate the expression
let x = 'hello' && 123;   // x === 123
```

#### Ép kiểu ngầm với đối tượng

Khi dùng toán tử so sánh(==) hoặc toán tử cộng(+) mà một trong toán hạng là kiểu đối tượng thì javascript sẽ chuyển đổi kiểu đối tượng về kiểu nguyên thủy(primitive)

Trong trường hợp cần ép kiểu từ đối tượng sang boolean thì bất kỳ giá trị không nguyên thủy nào cũng luôn bị ép thành true, bất kể đối tượng hoặc mảng có rỗng hay không.

Trong trường hợp cần ép kiểu từ đối tượng sang string hoặc number thì thuật toán xử lý như sau:

* Nếu input đã là một kiểu dữ liệu nguyên thủy, không làm gì cả và trả về nó.
* Gọi input.toString(), nếu kết quả là kiểu dữ liệu nguyên thủy, trả về nó.
* Gọi input.valueOf(), nếu kết quả là kiểu dữ liệu nguyên thủy, trả về nó.
* Nếu cả input.toString() và input.valueOf() đều không trả về kiểu dữ liệu nguyên thủy, hãy throw TypeError.

***

### Bảng chuyển đổi kiểu dữ liệu

Bảng dưới đây cung cấp một cái nhìn tổng quan về cách các giá trị khác nhau trong JavaScript được chuyển đổi sang các kiểu dữ liệu `Number`, `String` và `Boolean`.

| **Giá trị gốc**    | **Chuyển thành số**                     | **Chuyển thành chuỗi** | **Chuyển thành boolean**                 |
| ------------------ | --------------------------------------- | ---------------------- | ---------------------------------------- |
| false              | 0                                       | “false”                | false                                    |
| true               | 1                                       | “true”                 | true                                     |
| 0                  | 0                                       | “0”                    | false                                    |
| 1                  | 1                                       | “1”                    | true                                     |
| “0”                | 0                                       | “0”                    | <mark style="color:red;">**true**</mark> |
| “000”              | 0                                       | “000”                  | <mark style="color:red;">**true**</mark> |
| “1”                | 1                                       | “1”                    | true                                     |
| NaN                | NaN                                     | “NaN”                  | false                                    |
| Infinity           | Infinity                                | “Infinity”             | true                                     |
| -Infinity          | -Infinity                               | “-Infinity”            | true                                     |
| “”                 | 0                                       | “”                     | false                                    |
| “20”               | 20                                      | “20”                   | true                                     |
| “twenty”           | NaN                                     | “twenty”               | true                                     |
| \[]                | 0                                       | “”                     | <mark style="color:red;">**true**</mark> |
| \[20]              | 20                                      | “20”                   | true                                     |
| \[10, 20]          | NaN                                     | “10,20”                | true                                     |
| \[“twenty”]        | NaN                                     | “twenty”               | true                                     |
| \[“ten”, “twenty”] | NaN                                     | “ten,twenty”           | true                                     |
| function sum() {}  | NaN                                     | “function sum() {}”    | true                                     |
| {}                 | NaN                                     | “\[object Object]”     | <mark style="color:red;">**true**</mark> |
| null               | 0                                       | “null”                 | false                                    |
| undefined          | <mark style="color:red;">**NaN**</mark> | “undefined”            | false                                    |

_<mark style="color:red;">**Giá trị màu đỏ**</mark> chỉ các giá trị mà một số lập trình viên có thể không mong đợi._

> _Tham khảo thêm:_ [_https://www.w3schools.com/js/js\_type\_conversion.asp_](https://www.w3schools.com/js/js_type_conversion.asp)
>
> _Tham khảo thêm dạng ma trận nếu bạn thích hack não:_ [_https://dorey.github.io/JavaScript-Equality-Table/_](https://dorey.github.io/JavaScript-Equality-Table/)

***

### Tóm tắt logic ép kiểu ngầm

JavaScript thực hiện **ép kiểu ngầm** để chuyển đổi giữa các kiểu dữ liệu khác nhau một cách tự động khi cần thiết. Kết quả của quá trình này thường rơi vào một trong ba dạng: **string**, **number**, hoặc **boolean**.

#### Ép kiểu thành boolean

Xảy khi sử dụng toán tử logic ( `||` `&&` `!`) hoặc trong ngữ cảnh logic(`if`, vòng lặp, điều kiện `?:`)

Khi ép kiểu sang boolean thì các giá trị falsy: `false`, `""`, `0`, `NaN`, `null`, `undefined`, `-0`, `0n`  sẽ được ép thành `false`  còn cách giá trị còn lại sẽ chuyển thành `true`.

#### Ép kiểu thành string

Xảy ra khi sử dụng toán tử `+`  mà một trong các toán hạng có kiểu chuỗi.

#### Ép kiểu thành number

Xảy ra khi sử dụng toán tử so sánh (`>`, `<`, `<=`,`>=`), toán tử bitwise ( `|` `&` `^` `~`), toán tử số học (`-` `+` `*` `/` `%` ), Sử dụng dấu `+` trước giá trị (`+value`) để ép kiểu sang số.

> Toán tử `+` không ép kiểu sang số khi có toán hạng là chuỗi.
>
> Toán tử `==` và `!=` không ép kiểu khi cả hai toán hạng đều là chuỗi.
>
> Chuỗi không phải số (e.g., `"abc"`) sẽ chuyển thành `NaN`.
>
> Giá trị `null` chuyển thành `0`, còn `undefined` chuyển thành `NaN`.

#### Ngoại lệ

`null` và `undefined` sẽ không được ép kiểu khi sử dụng toán tử so sánh không nghêm ngặt (`==`, `!=`  )  , khi đó null == undefined trả về `true`

`NaN` không bằng bất kì giá trị nào kể cả chính nó

#### Ép kiểu với đối tượng

Khi ép kiểu cho đối tượng nếu:

* Khi ép đối tượng thành `boolean`, kết quả **luôn là `true`**, bao gồm cả mảng rỗng (`[]`) và object rỗng (`{}`).
* Khi ép thành `string` hoặc `number`, JavaScript sẽ gọi:
  * `toString()`: Ưu tiên trả về chuỗi mô tả.
  * `valueOf()`: Ưu tiên trả về giá trị gốc.

> Tài liệu tham khảo: [https://www.freecodecamp.org/news/js-type-coercion-explained-27ba3d9a2839/](https://www.freecodecamp.org/news/js-type-coercion-explained-27ba3d9a2839/)

### Lưu ý quan trọng

* **Nên sử dụng toán tử so sánh nghiêm ngặt**: Để tránh những hành vi không mong muốn từ ép kiểu ngầm, nên sử dụng toán tử `===`. Toán tử này chỉ trả về `true` khi cả hai giá trị có cùng kiểu dữ liệu và giá trị.
* **Tư duy nghiêm ngặt với kiểu dữ liệu**: Khi lập trình, hãy chú ý đến việc sử dụng cùng kiểu dữ liệu trong so sánh và các phép tính toán. Điều này giúp tránh những lỗi logic không mong muốn.

Ví dụ:

```js
3 === "3"; // false, vì một là số và một là chuỗi
3 === 3;   // true, cùng kiểu và giá trị
```

Nắm vững các quy tắc và kỹ thuật ép kiểu trong JavaScript sẽ giúp bạn viết code chính xác hơn, tránh được những lỗi phổ biến, và hiểu rõ hơn về cách ngôn ngữ này xử lý dữ liệu.

{% hint style="info" %}
Tóm tắt

* **Định nghĩa ép kiểu**: Ép kiểu trong JavaScript là quá trình chuyển đổi giá trị từ một kiểu dữ liệu này sang một kiểu khác, thường xảy ra tự động trong các toán tử so sánh hoặc số học.
* **Ép kiểu rõ ràng và ngầm**:
  * **Rõ ràng**: Chủ động sử dụng các hàm như `Number()`, `String()`, `Boolean()`, v.v để chuyển đổi.
  * **Ngầm**: Tự động xảy ra, ví dụ khi sử dụng toán tử `+` hoặc `==`.
* **Các trường hợp ép kiểu phổ biến**:
  * **Sang chuỗi**: Dùng `String()`, `.toString()`, nối chuỗi, hoặc Template literals.
  * **Sang số**: Dùng `Number()`, toán tử `+`, `parseInt()`, `parseFloat()`.
  * **Sang boolean**: Dùng `Boolean()` hoặc `!!`.
* **Quy tắc ép kiểu ngầm**:
  * **Với toán tử `==`**: So sánh giá trị sau khi chuyển đổi kiểu.
  * **Với toán tử `+`**: Nếu một trong hai giá trị là chuỗi, thực hiện nối chuỗi; nếu không, thực hiện cộng số.
  * **Với toán tử `-`**: Chuyển đổi cả hai giá trị sang số rồi thực hiện trừ.
* **Lưu ý khi sử dụng ép kiểu**:
  * Sử dụng toán tử so sánh nghiêm ngặt `===` để tránh hành vi không mong muốn từ ép kiểu ngầm.
  * Chú ý sử dụng cùng kiểu dữ liệu trong so sánh và tính toán.
{% endhint %}

