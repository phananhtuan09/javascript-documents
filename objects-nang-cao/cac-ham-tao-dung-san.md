# Các hàm tạo dựng sẵn

Mục lục

* [Các hàm tạo dựng sẵn là gì](cac-ham-tao-dung-san.md#cac-ham-tao-dung-san-la-gi)?
* [Hàm tạo trả về đối tượng khi sử dụng từ khóa new](cac-ham-tao-dung-san.md#ham-tao-tra-ve-doi-tuong-khi-su-dung-tu-khoa-new)
  * [String](cac-ham-tao-dung-san.md#string)
  * [Number](cac-ham-tao-dung-san.md#number)
  * [Boolean](cac-ham-tao-dung-san.md#boolean)
  * [Array](cac-ham-tao-dung-san.md#array)
  * [Object](cac-ham-tao-dung-san.md#object)
  * [Function](cac-ham-tao-dung-san.md#function)
* [Các sai lầm thường gặp](cac-ham-tao-dung-san.md#cac-sai-lam-thuong-gap)
  * [Sử dụng hàm tạo khi không cần thiết](cac-ham-tao-dung-san.md#su-dung-ham-tao-khi-khong-can-thiet)

### Các hàm tạo dựng sẵn là gì?

Các hàm tạo dựng sẵn (_built-in function constructor_) trong JavaScript là những hàm được cung cấp sẵn bởi ngôn ngữ lập trình để tạo ra các kiểu dữ liệu cơ bản hoặc phức tạp một cách nhanh chóng và tiện lợi. Các hàm tạo này bao gồm: `String`, `Number`, `Array`, `Object`, `Function`, v.v.

* **String**: Tạo chuỗi mới.
* **Number**: Tạo số mới.
* **Boolean**: Tạo true hoặc false mới.
* **Array**: Tạo mảng mới.
* **Object**: Tạo đối tượng mới.
* **Function**: Tạo hàm mới.

Cú pháp sử dụng:

```javascript
let str = new String("Hello");
let num = new Number(123);
let arr = new Array(1, 2, 3);
let obj = new Object();
let func = new Function("x", "y", "return x + y")
```

Trong thực tế, chúng ta thường sử dụng các hàm tạo này (_sử dụng như một hàm thông thường - không sử dụng từ khóa `new`_) với mục đích chuyển đổi kiểu dữ liệu (_ép kiểu_), ít khi sử dụng nó để tạo ra các đối tượng.

***

### Hàm tạo trả về đối tượng khi sử dụng từ khóa new

Khi sử dụng từ khóa `new` với các hàm tạo như `String`, `Number`, `Boolean`, `Array`, `Object`, và `Function` các hàm tạo này sẽ trả về một đối tượng.

#### String

Tương tự, `new Number()` tạo một đối tượng Number mới, không giống như sử dụng một _số literal_ như `123` (_không phải một đối tượng_).

```javascript
let numObj = new Number(123);
console.log(typeof numObj); // object
```

#### Number

Tương tự, `new Number()` tạo một đối tượng Number mới, không giống như sử dụng một _số literal_ như `123` (_không phải một đối tượng_).

```javascript
let numObj = new Number(123);
console.log(typeof numObj); // object
```

#### Boolean

`new Boolean()` tạo một đối tượng Boolean mới. Điều này cũng khác với việc sử dụng giá trị _boolean literal_ như `true` hoặc `false`.

```javascript
let boolObj = new Boolean(true);
console.log(typeof boolObj); // object
```

#### &#x20;Array

`new Array()` tạo một đối tượng Array mới. Điều này không khác biệt nhiều so với việc sử dụng cú pháp _literal_ như `[]` vì cả hai đều tạo ra đối tượng Array.

```javascript
let arrObj = new Array(1, 2, 3);
console.log(typeof arrObj); // object
```

#### Object

`new Object()` hoặc cú pháp _literal_ `{}` đều tạo ra một đối tượng mới.

```javascript
let obj = new Object();
console.log(typeof obj); // object
```

#### Function

`new Function()` tạo một đối tượng Function mới, cho phép bạn định nghĩa hàm động.

```javascript
let funcObj = new Function("a", "b", "return a + b");
console.log(typeof funcObj); // function
```

Sử dụng từ khóa `new` với các kiểu dữ liệu này tạo ra các đối tượng _wrapper_ tương ứng, cho phép bạn truy cập vào các phương thức và thuộc tính của đối tượng. Tuy nhiên, trong nhiều trường hợp, việc sử dụng kiểu dữ liệu _primitive_ (ví dụ: chuỗi literal, số, và giá trị boolean) là đủ và được ưu tiên vì tính đơn giản và hiệu suất tốt hơn.

***

### Các sai lầm thường gặp

#### &#x20;Sử dụng hàm tạo khi không cần thiết

Việc sử dụng hàm tạo cho một số kiểu dữ liệu đơn giản như `String` hay `Number` có thể không cần thiết và làm tăng kích thước của code.

**Cách giải quyết**: Sử dụng các cách đơn giản, truyền thống đã học ở các chương trước.

Ví dụ:

```js
// Sử dụng
let str = "Hello";

// Thay vì
let str = new String("Hello");
```

Hoặc:

```js
// Sử dụng
function sum(a, b) {
  return a + b;
}

// Thay vì
let sum = new Function("a", "b", "return a + b");
```

{% hint style="info" %}
Tóm tắt

* **Các hàm tạo dựng sẵn và từ khóa new**: Khi sử dụng từ khóa `new` với các hàm tạo dựng sẵn, JavaScript tạo ra các đối tượng cho phép truy cập vào các phương thức và thuộc tính đặc biệt.
  * **String**: Trả về một đối tượng chuỗi.
  * **Number**: Trả về một đối tượng số.
  * **Boolean**: Trả về một đối tượng boolean.
  * **Array**: Trả về một đối tượng mảng.
  * **Object**: Trả về một đối tượng.
  * **Function**: Trả về một đối tượng hàm.
* **Các sai lầm thường gặp và giải pháp**:
  * **Sử dụng hàm tạo khi không cần thiết**: Để tránh làm tăng kích thước của code, nên sử dụng cách đơn giản, truyền thống cho việc tạo kiểu dữ liệu cơ bản như chuỗi literal hoặc số, thay vì sử dụng các hàm tạo dựng sẵn.
{% endhint %}

