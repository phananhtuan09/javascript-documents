# Phương thức filter()

Mục lục

* [Phương thức filter](phuong-thuc-filter.md#phuong-thuc-filter)
  * [Phương thức filter là gì?](phuong-thuc-filter.md#phuong-thuc-filter-la-gi)
* [Các cách làm việc với filter()](phuong-thuc-filter.md#cac-cach-lam-viec-voi-filter)
  * [Lọc số nguyên dương](phuong-thuc-filter.md#loc-so-nguyen-duong)
  * [Lọc - lấy ra các phần tử không trùng lặp](phuong-thuc-filter.md#loc-lay-ra-cac-phan-tu-khong-trung-lap)
  * [Lọc ra các đối tượng có tuổi từ 18 trở lên](phuong-thuc-filter.md#loc-ra-cac-doi-tuong-co-tuoi-tu-18-tro-len)
  * [Lọc ra các sản phẩm còn hàng và giá từ 800 trở xuống](phuong-thuc-filter.md#loc-ra-cac-san-pham-con-hang-va-gia-tu-800-tro-xuong)
* [Các sai lầm thường gặp](phuong-thuc-filter.md#cac-sai-lam-thuong-gap)
  * [Sử dụng filter không có return](phuong-thuc-filter.md#su-dung-filter-khong-co-return)

### Phương thức filter

#### Phương thức filter là gì?

Phương thức `filter()` tạo một mảng mới chứa tất cả các phần tử thỏa mãn điều kiện. Phương thức này không thay đổi mảng gốc mà chỉ trả về một mảng mới.

Cú pháp:

```js
let newArray = array.filter(callbackFunction, thisValue);
```

* `callbackFunction`: Hàm kiểm tra được gọi cho mỗi phần tử trong mảng.
  * `element`: Phần tử hiện tại đang được xử lý.
  * `index` (tùy chọn): Chỉ mục của phần tử hiện tại.
  * `array` (tùy chọn): Mảng đang được sử dụng.
* `thisValue` (tùy chọn): Giá trị để sử dụng làm `this` khi thực hiện `callbackFunction`.

Ví dụ:

```javascript
let numbers = [1, 2, 3, 4, 5, 6];

// Lọc tất cả các phần tử chẵn.
let result = numbers.filter(function(item) {
  return item % 2 === 0;
});

console.log(result); // (3) [2, 4, 6]
```

Phương thức `filter()` được sử dụng khi cần lọc các phần tử của mảng theo điều kiện nhất định. Sử dụng phương thức này giúp giảm số lượng code cần thiết (_so với dùng vòng lặp thuần túy_) để xử lý các mảng, làm cho code gọn gàng và dễ đọc hơn.

**Lưu ý**: Phương thức `filter` không lặp qua các phần tử trống và kết quả là một bản sao nông(shallow copy) của mảng ban đầu.

Ví dụ:

```javascript
const obj = { id: 1, name: "John" };

const arr = [obj, { id: 2 }, , , , { id: 3 }, { id: 1 }];

const newArray = arr.filter((item) => {
  console.log(item);
  return item.id === 1;
});

console.log(newArray);
console.log(obj === newArray[0]);
// main.js:6 {id: 1, name: 'John'}
// main.js:6 {id: 2}
// main.js:6 {id: 3}
// main.js:6 {id: 1}
// main.js:10 (2) [{…}, {…}]
// main.js:11 true
```

***

### Các cách làm việc với filter()

#### Lọc số nguyên dương

```javascript
let numbers = [-2, 5, 8, -10, 0, 20];
let result = numbers.filter(n => n > 0);

console.log(result); // (3) [5, 8, 20]
```

#### Lọc - lấy ra các phần tử không trùng lặp

```javascript
let items = [
  "apple",
  "banana",
  "apple",
  "orange",
  "banana",
  "orange"
];
let result = items.filter((item, index, array) => {
  return array.indexOf(item) === index;
});

console.log(result); // (3) ["apple", "banana", "orange"]
```

#### Lọc ra các đối tượng có tuổi từ 18 trở lên

Bạn có thể sử dụng `filter()` để lọc các đối tượng trong mảng dựa vào thuộc tính của chúng.

```javascript
let people = [
  { name: "John", age: 23 },
  { name: "Jane", age: 15 },
  { name: "Jim", age: 30 }
];
let result = people.filter(person => person.age >= 18);

console.log(result); // (2) [Object, Object]
```

#### Lọc ra các sản phẩm còn hàng và giá từ 800 trở xuống

Bạn có thể kết hợp nhiều điều kiện trong một hàm `filter` để làm phức tạp các điều kiện lọc.

```javascript
let products = [
  { name: "laptop", price: 1000, stock: 4 },
  { name: "phone", price: 500, stock: 10 },
  { name: "tablet", price: 700, stock: 0 }
];
let result = products.filter(p => p.price <= 800 && p.stock > 0);

console.log(result); // (1) [Object]
```

***

### Các sai lầm thường gặp

#### &#x20;Sử dụng filter không có return

Sai lầm phổ biến khi sử dụng `filter` là quên `return` trong hàm callback. Nếu không có `return`, mảng mới sẽ trống vì không có phần tử nào được “chọn”.

**Cách giải quyết:**

Đảm bảo rằng hàm callback của bạn có lệnh `return` đúng giá trị _truthy_ cần thiết.

Ví dụ:

```javascript
let numbers = [1, 2, 3, 4, 5];
let result = numbers.filter(item => item > 3);

console.log(result); // (2) [4, 5]
```

{% hint style="info" %}
Tóm tắt

* **Định nghĩa và cú pháp**: `filter()` là phương thức trả về một mảng mới gồm các phần tử thỏa mãn điều kiện từ một hàm kiểm tra. Cú pháp cơ bản: `array.filter(callbackFunction, thisValue)`.
  * **Phần tử trong callback**: Gồm `element` (phần tử hiện tại), `index` (chỉ mục phần tử, tùy chọn), và `array` (mảng đang xử lý, tùy chọn).
* **Ứng dụng của filter()**: Dùng để lọc các phần tử theo điều kiện nhất định, giúp code gọn và dễ đọc hơn so với sử dụng vòng lặp truyền thống.
  * **Ví dụ Thực tế**: Lọc số nguyên dương, loại bỏ trùng lặp, lọc theo độ tuổi hoặc các điều kiện phức hợp trong một mảng, v.v.
* **Sai lầm thường gặp**: Quên `return` trong hàm callback dẫn đến mảng kết quả trống. Luôn đảm bảo hàm callback trả về giá trị `truthy` khi điều kiện đúng.
{% endhint %}
