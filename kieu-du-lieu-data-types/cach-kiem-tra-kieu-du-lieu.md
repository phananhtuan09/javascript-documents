# Cách kiểm tra kiểu dữ liệu

Mục lục

* [String](cach-kiem-tra-kieu-du-lieu.md#string)
* [Number](cach-kiem-tra-kieu-du-lieu.md#number)
* [BigInt](cach-kiem-tra-kieu-du-lieu.md#bigint)
* [Boolean](cach-kiem-tra-kieu-du-lieu.md#boolean)
* [Null](cach-kiem-tra-kieu-du-lieu.md#null)
* [Undefined](cach-kiem-tra-kieu-du-lieu.md#undefined)
* [Symbol](cach-kiem-tra-kieu-du-lieu.md#symbol)
* [Object](cach-kiem-tra-kieu-du-lieu.md#object)
* [Array](cach-kiem-tra-kieu-du-lieu.md#array)
* [Function](cach-kiem-tra-kieu-du-lieu.md#function)

### String

Kiểu dữ liệu String biểu diễn chuỗi ký tự.

Ví dụ:

```javascript
let greeting = "Hello, world!";
console.log(typeof greeting === "string"); // true
```

`typeof greeting` trả về `"string"` và so sánh với `"string"` sẽ là `true`, xác nhận `greeting` là kiểu String.

***

### Number

Kiểu Number biểu diễn số.

```javascript
let value = 30; // Thử thay đổi thành NaN để kiểm tra
console.log(typeof value === "number" && !isNaN(value)); // true
```

[_NaN_](https://javascript.fullstack.edu.vn/?id=ca230aab-100d-43fa-83c7-485e269f6477) _được sử dụng để biểu thị kết quả của một phép toán số học không hợp lệ, và `typeof NaN` cũng trả về `"number"`, điều này có thể gây nhầm lẫn khi cần xác định một biến có phải là số hợp lệ hay không. Do đó, cần kiểm tra thêm điều kiện để loại trừ `NaN`._

> _Trong JavaScript, kiểu `Number` có thể biểu diễn số nguyên và số thực. Tuy nhiên, nó có giới hạn ở mức khoảng ±(2^53 - 1) do sử dụng định dạng số IEEE 754. Điều này dẫn đến việc `BigInt` trở nên quan trọng trong trường hợp xử lý số lớn vượt quá giới hạn của `Number`._

***

### &#x20;BigInt

BigInt cho số nguyên lớn.

```javascript
let largeNumber = 9007199254740991n;
console.log(typeof largeNumber === "bigint"); // true
```

`typeof largeNumber` trả về `"bigint"` và so sánh với `"bigint"` cho ra `true`, xác nhận là BigInt.

> _Đây là kiểu dữ liệu mới được giới thiệu để xử lý các số nguyên lớn hơn giới hạn của `Number`. Ví dụ: `9007199254740992` có thể được biểu diễn chính xác với `BigInt("9007199254740992")` hoặc `9007199254740992n`._

***

### Boolean

Boolean có giá trị `true` hoặc `false`.

Ví dụ:

```javascript
let isStudent = true;
console.log(typeof isStudent === "boolean"); // true
```

`typeof isStudent` trả về `"boolean"` và so sánh với `"boolean"` cho ra `true`.

***

### Null

Null biểu diễn giá trị “không có gì”.

Ví dụ:

```javascript
let emptyValue = null;
console.log(emptyValue === null); // true
```

So sánh `emptyValue` với `null` cho ra `true`, xác nhận giá trị là Null.

_Trong JavaScript, khi sử dụng `typeof` với một biến có giá trị `null`, nó sẽ trả về `"object"` chứ không phải `"null"`. Để xác định một giá trị là `null`, chúng ta phải sử dụng so sánh trực tiếp `emptyValue === null`._

***

### Undefined

Undefined biểu thị cho biến chưa được gán giá trị.

Ví dụ:

```javascript
let notAssigned;
console.log(typeof notAssigned === "undefined"); // true
```

`typeof notAssigned` trả về `"undefined"` và so sánh với `"undefined"` cho ra `true`.

***

### Symbol

Symbol tạo định danh duy nhất.

Ví dụ:

```javascript
let sym = Symbol("unique");
console.log(typeof sym === "symbol"); // true
```

`typeof sym` trả về `"symbol"` và so sánh với `"symbol"` cho ra `true`.

***

### Object

Object chứa cặp khóa và giá trị.

Ví dụ:

```javascript
let person = { name: "John", age: 30 };
console.log(typeof person === "object" && person !== null && !Array.isArray(person)); // true
```

Kiểm tra `typeof person` là `"object"` và không phải `null`.

_Như đã giải thích ở trên, `typeof null` và `typeof []` đều trả về `"object"`, nên chỉ kiểm tra `typeof person === "object"` không đủ để xác nhận biến đó thực sự là một đối tượng. Do đó, cần thêm điều kiện `person !== null` và `!Array.isArray(person)` để đảm bảo rằng biến đó không phải là `null` và không phải là Array._

***

### Array

Mảng chứa danh sách các giá trị.

Ví dụ:

```javascript
let fruits = ["apple", "banana", "cherry"];
console.log(Array.isArray(fruits)); // true
// hoặc
console.log(fruits instanceof Array); // true
```

`Array.isArray(fruits)` trả về `true`, xác nhận `fruits` là mảng.

_Khi sử dụng `typeof` với mảng sẽ trả về `"object"` chứ không phải `"array"`. Điều này là do mảng cũng là đối tượng (đối tượng đặc biệt). Vì vậy chỉ dùng `typeof fruits === "object"` sẽ bị sai nếu giá trị biến là object hoặc null. Trường hợp này chúng ta sử dụng `Array.isArray()`, nó sẽ trả về `true` nếu biến là một mảng, và `false` nếu không phải mảng._

***

### Function

Function thực hiện tác vụ và giúp tái sử dụng code.

Ví dụ:

```javascript
function greet() {
  return "Hello, world!";
}
console.log(typeof greet === "function"); // true
```

`typeof greet` trả về `"function"` và so sánh với `"function"` cho ra `true`, xác nhận `greet` là Function.

{% hint style="info" %}
Tóm tắt

* **Mô tả vấn đề**: Trong JavaScript, `typeof` cho `null`, `object`, và `array` đều trả về `"object"`; và `typeof` cho `number` và `NaN` đều trả về `"number"` gây khó khăn trong việc phân biệt chúng.
* Các kiểu dữ liệu:
  * **String**: Chuỗi ký tự, kiểm tra bằng `typeof`.
  * **Number**: Số, kiểm tra bằng `typeof`, cần loại trừ `NaN`.
  * **BigInt**: Số nguyên lớn, kiểm tra bằng `typeof`.
  * **Boolean**: Giá trị `true` hoặc `false`, kiểm tra bằng `typeof`.
  * **Null**: “Không có gì”, phải so sánh trực tiếp với `null` do `typeof` trả về `"object"`.
  * **Undefined**: Biến chưa được gán giá trị, kiểm tra bằng `typeof`.
  * **Symbol**: Định danh duy nhất, xác nhận bằng `typeof`.
  * **Object**: Cặp khóa và giá trị, cần kiểm tra không phải `null` và không phải `Array`.
  * **Array**: Danh sách giá trị, dùng `Array.isArray()` hoặc `instanceof Array` để kiểm tra.
  * **Function**: Thực hiện tác vụ và giúp tái sử dụng code, kiểm tra bằng `typeof`.
* **4 trường hợp cần ghi nhớ cách kiểm tra**:
  * **Number**: Cần loại trừ `NaN`.
  * **Null**: So sánh trực tiếp với `null`.
  * **Object**: Nhớ loại trừ `Array` và `Null`.
  * **Array**: Sử dụng `Array.isArray()` hoặc `instanceof Array`.
{% endhint %}

