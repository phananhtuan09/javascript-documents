# Phương thức map()

Mục lục

* [Phương thức map](phuong-thuc-map.md#phuong-thuc-map)
  * [Phương thức map là gì?](phuong-thuc-map.md#phuong-thuc-map-la-gi)
* [Các cách làm việc với map](phuong-thuc-map.md#cac-cach-lam-viec-voi-map)
* [Chuyển đổi một mảng số thành một mảng chuỗi](phuong-thuc-map.md#chuyen-doi-mot-mang-so-thanh-mot-mang-chuoi)
  * [Tính giá sau thuế cho mỗi mặt hàng](phuong-thuc-map.md#tinh-gia-sau-thue-cho-moi-mat-hang)
  * [Tạo các phần tử HTML từ một mảng dữ liệu](phuong-thuc-map.md#tao-cac-phan-tu-html-tu-mot-mang-du-lieu)
  * [Tạo ra một mảng chứa tên các người dùng](phuong-thuc-map.md#tao-ra-mot-mang-chua-ten-cac-nguoi-dung)
* [Các sai lầm thường gặp](phuong-thuc-map.md#cac-sai-lam-thuong-gap)
  * [Không trả về giá trị trong hàm callback](phuong-thuc-map.md#khong-tra-ve-gia-tri-trong-ham-callback)
  * [Sử dụng map thay cho forEach](phuong-thuc-map.md#su-dung-map-thay-cho-foreach)

### Phương thức map

#### Phương thức map là gì?

Phương thức `map` trả về một mảng mới từ mảng hiện tại bằng cách áp dụng một hàm cho mỗi phần tử của mảng ban đầu, mỗi phần tử tương ứng trong mảng mới được trả về bởi _callback_. Phương thức này không thay đổi mảng hiện tại mà trả về một mảng mới.

Cú pháp:

```js
let newArray = array.map(callbackFunction(element, index, array) {
    // Trả về giá trị mới cho mỗi phần tử trong mảng mới
}, thisValue);
```

* `callbackFunction`: Hàm kiểm tra được gọi cho mỗi phần tử trong mảng.
  * `element`: Phần tử hiện tại đang được xử lý.
  * `index` (tùy chọn): Chỉ mục của phần tử hiện tại.
  * `array` (tùy chọn): Mảng đang được sử dụng.
* `thisValue` (tùy chọn): Giá trị để sử dụng làm `this` khi thực hiện `callbackFunction`.

Ví dụ:

```javascript
const numbers = [1, 2, 3, 4];

// Tạo ra mảng mới chứa các phần tử mảng cũ x 2
const result = numbers.map(num => num * 2);

console.log(result); // (4) [2, 4, 6, 8]
```

Phương thức `map` được sử dụng khi bạn muốn chuyển đổi các giá trị trong một mảng mà không làm thay đổi mảng gốc.

**Lưu ý**: Phương thức `map` không lặp qua các phần tử trống và vẫn có trường hợp phương thức map thay đổi đối tượng ban đầu

Ví dụ:&#x20;

```javascript
const obj = { id: 1, name: "John" };

const arr = [obj, { id: 2 }, , , , { id: 3 }, { id: 1 }];

const newArray = arr.map((item) => {
  console.log(item);
  item.id += 1;
  return item;
});

console.log(newArray);
console.log(obj);
// main.js:6 {id: 1, name: 'John'}
// main.js:6 {id: 2}
// main.js:6 {id: 3}
// main.js:6 {id: 1}
// main.js:11 (7) [{…}, {…}, empty × 3, {…}, {…}]
// main.js:12 {id: 2, name: 'John'}
```

***

### Các cách làm việc với map

#### Chuyển đổi một mảng số thành một mảng chuỗi

```javascript
const numbers = [1, 2, 3];

const result = numbers.map(String);

console.log(result); // (3) ["1", "2", "3"]
```

#### Tính giá sau thuế cho mỗi mặt hàng

```javascript
const prices = [100, 150, 200];
const taxRate = 0.1; // 10%

const result = prices.map(price => price + price * taxRate);

console.log(result); // (3) [110, 165, 220]
```

#### Tạo các phần tử HTML từ một mảng dữ liệu

```javascript
const items = ['Apple', 'Banana', 'Orange'];

const result = items.map(item => `<li>${item}</li>`);
const html = `<ul>${result.join('')}</ul>`;

console.log(html); // <ul><li>Apple</li><li>Banana</li><li>Orange</li></ul>
```

#### &#x20;Tạo ra một mảng chứa tên các người dùng

```javascript
const users = [
  { name: "Alice", age: 22 },
  { name: "Bob", age: 24 },
  { name: "John", age: 26 }
];

const names = users.map(user => user.name);

console.log(names); // (3) ["Alice", "Bob", "John"]
```

***

### Các sai lầm thường gặp

#### Không trả về giá trị trong hàm callback

Nếu bạn không trả về giá trị trong hàm callback của `map`, mảng mới sẽ chứa các phần tử `undefined`.

```javascript
const numbers = [1, 2, 3];

const result = numbers.map(num => {
    num * num;
});

console.log(result); // (3) [undefined, undefined, undefined]
```

**Cách giải quyết:** Luôn trả về giá trị trong hàm callback.

```javascript
const numbers = [1, 2, 3];

const result = numbers.map(num => {
    return num * num;
});

console.log(result); // (3) [1, 4, 9]
```

#### &#x20;Sử dụng map thay cho forEach

Đôi khi có những lập trình viên sử dụng `map` thay thế cho `forEach` khi không cần tạo mảng mới. Điều này không hiệu quả và có thể gây nhầm lẫn.

```javascript
const numbers = [1, 2, 3];

numbers.map(num => {
    console.log(num);
});
// 1
// 2
// 3
```

**Cách giải quyết:** Sử dụng `forEach` nếu chỉ muốn thực hiện hành động mà không cần tạo mảng mới.

<pre class="language-javascript"><code class="lang-javascript">const numbers = [1, 2, 3];

numbers.forEach(num => {
    console.log(num);
});
<strong>// 1
</strong><strong>// 2
</strong><strong>// 3
</strong></code></pre>

{% hint style="info" %}
Tóm tắt

* **Định nghĩa và cú pháp**: `map` là một phương thức dùng để tạo một mảng mới từ mảng ban đầu bằng cách áp dụng hàm callback cho từng phần tử. Phương thức này không thay đổi mảng gốc mà trả về một mảng mới với các giá trị được xử lý và trả về bởi hàm callback.
  * **Cú pháp**: `let newArray = array.map(callbackFunction(element, index, array), thisValue);`
* **Các sai lầm thường gặp**:
  * **Không trả về giá trị trong hàm callback**: Nếu hàm callback không trả về giá trị, các phần tử trong mảng mới sẽ là `undefined`. Luôn đảm bảo rằng hàm callback trả về giá trị cho mỗi lần lặp.
  * **Sử dụng map thay cho forEach**: `map` nên được sử dụng khi bạn cần tạo một mảng mới từ một mảng hiện có thông qua các phép biến đổi. Sử dụng `forEach` nếu chỉ muốn thực hiện hành động trên từng phần tử mà không cần tạo mảng mới.
{% endhint %}
