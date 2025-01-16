# Phương thức find() và findIndex()

Mục lục

* [Phương thức find](phuong-thuc-find-va-findindex.md#phuong-thuc-find)
  * [Phương thức find là gì?](phuong-thuc-find-va-findindex.md#phuong-thuc-find-la-gi)
  * [Ví dụ sử dụng find()](phuong-thuc-find-va-findindex.md#vi-du-su-dung-find)
* [Phương thức findLast](phuong-thuc-find-va-findindex.md#phuong-thuc-findlast)
  * [Phương thức findLast là gì?](phuong-thuc-find-va-findindex.md#phuong-thuc-findlast-la-gi)
  * [Ví dụ sử dụng findLast()](phuong-thuc-find-va-findindex.md#vi-du-su-dung-findlast)
* [Phương thức findIndex](phuong-thuc-find-va-findindex.md#phuong-thuc-findindex)
  * [Phương thức findIndex là gì?](phuong-thuc-find-va-findindex.md#phuong-thuc-findindex-la-gi)
  * [Ví dụ sử dụng findIndex()](phuong-thuc-find-va-findindex.md#vi-du-su-dung-findindex)
* [Phương thức findLastIndex](phuong-thuc-find-va-findindex.md#phuong-thuc-findlastindex)
  * [Phương thức findLastIndex là gì?](phuong-thuc-find-va-findindex.md#phuong-thuc-findlastindex-la-gi)
  * [Ví dụ sử dụng findLastIndex()](phuong-thuc-find-va-findindex.md#vi-du-su-dung-findlastindex)
* [Các sai lầm thường gặp](phuong-thuc-find-va-findindex.md#cac-sai-lam-thuong-gap)
  * [Sử dụng find, findLast, findIndex, findLastIndex không có return](phuong-thuc-find-va-findindex.md#su-dung-find-findlast-findindex-findlastindex-khong-co-return)

### Phương thức find

#### Phương thức find là gì?

Phương thức `find()` được sử dụng để tìm phần tử đầu tiên trong một mảng thỏa mãn một hàm kiểm tra nhất định. Nếu không có phần tử nào thỏa mãn, phương thức này trả về `undefined`.

**Khi nào sử dụng:** Hữu ích khi bạn cần tìm một phần tử duy nhất trong mảng thỏa mãn một điều kiện nhất định, ví dụ tìm người dùng có tuổi trên 18 trong danh sách người dùng.

Cú pháp:

```js
const foundElement = array.find(callbackFunction, thisValue);
```

* `callbackFunction`: Hàm kiểm tra được gọi cho mỗi phần tử trong mảng.
  * `element`: Phần tử hiện tại đang được xử lý.
  * `index` (tùy chọn): Chỉ mục của phần tử hiện tại.
  * `array` (tùy chọn): Mảng đang được sử dụng.
* `thisValue` (tùy chọn): Giá trị để sử dụng làm `this` khi thực hiện `callbackFunction`.

Ví dụ:

```javascript
const numbers = [4, 10, 18, 5, 24, 78];
const result = numbers.find(num => num > 10);

console.log(result); // 18
```

Giải thích:

* Phương thức `find()` được gọi trên mảng `numbers`. Phương thức này sẽ duyệt qua mỗi phần tử của mảng và áp dụng hàm kiểm tra (_callback function_) lên mỗi phần tử đó.
* Hàm kiểm tra ở đây là một arrow function: `num => num > 10`. Hàm này sẽ kiểm tra xem phần tử hiện tại (`num`) có lớn hơn 10 hay không.
* Phương thức `find()` bắt đầu với phần tử đầu tiên của mảng là `4` và kiểm tra điều kiện (`4 > 10`), điều kiện này không đúng nên nó tiếp tục với phần tử tiếp theo là `10`, điều kiện vẫn không đúng.
* Khi đến phần tử `18`, điều kiện `18 > 10` là đúng. Do đó, `find()` dừng việc tìm kiếm và trả về phần tử này.

#### &#x20;Ví dụ sử dụng find()

**Tìm người dùng đầu tiên có tuổi trên 21**

```javascript
const users = [
  { name: "Alice", age: 20 },
  { name: "Bob", age: 22 },
  { name: "Carol", age: 19 }
];
const result = users.find(user => user.age > 21);

console.log(result); // {name: "Bob", age: 22}
```

Phương thức `find()` được gọi trên mảng `users`. Mỗi phần tử trong mảng (đại diện cho một người dùng) được truyền qua một hàm kiểm tra, ở đây là kiểm tra `age > 21`. Phương thức này trả về người dùng đầu tiên mà tuổi của họ lớn hơn 21.

**Tìm sản phẩm đầu tiên có giá dưới 50$**

```javascript
const products = [
  { name: "Toaster", price: 100 },
  { name: "Blender", price: 45 },
  { name: "Kettle", price: 60 }
];
const result = products.find(product => product.price < 50);

console.log(result); // {name: "Blender", price: 45}
```

Phương thức `find()` duyệt qua mảng `products` và áp dụng hàm kiểm tra `price < 50` cho mỗi sản phẩm. Khi nó tìm thấy sản phẩm đầu tiên có giá dưới 50$, phương thức này ngay lập tức trả về sản phẩm đó.

***

### Phương thức findLast

#### Phương thức findLast là gì?

Phương thức `findLast()` tìm phần tử đầu tiên tính từ cuối mảng thỏa mãn hàm kiểm tra đã cho. Nếu không tìm thấy phần tử nào, nó trả về `undefined`.

**Khi nào sử dụng:** Sử dụng khi bạn cần tìm phần tử thỏa mãn điều kiện nhưng lại muốn lấy cái cuối cùng trong danh sách, chẳng hạn như sản phẩm được thêm vào cuối cùng có giá trên 100$.

Cú pháp:

```js
const foundLastElement = array.findLast(callbackFunction, thisValue);
```

* `callbackFunction`: Hàm kiểm tra được gọi cho mỗi phần tử trong mảng.
  * `element`: Phần tử hiện tại đang được xử lý.
  * `index` (tùy chọn): Chỉ mục của phần tử hiện tại.
  * `array` (tùy chọn): Mảng đang được sử dụng.
* `thisValue` (tùy chọn): Giá trị để sử dụng làm `this` khi thực hiện `callbackFunction`.

Ví dụ:

```javascript
const numbers = [4, 10, 18, 5, 24, 78];
const result = numbers.findLast(num => num > 10);

console.log(result); // 78
```

`findLast()` hoạt động tương tự như `find()`, điểm khác biệt duy nhất là tìm kiếm bắt đầu từ cuối mảng trở về đầu mảng. Trong ví dụ này, phần tử đầu tiên từ cuối mảng lớn hơn 10 là 78, do đó nó được trả về ngay khi được tìm thấy.

#### Ví dụ sử dụng findLast()

**Tìm bài viết cuối cùng được viết bởi tác giả “John Doe”**

```javascript
const articles = [
  { title: "Summer Vacations", author: "Jane Doe" },
  { title: "Winter Festivals", author: "John Doe" },
  { title: "Autumn Recipes", author: "John Doe" }
];
const result = articles.findLast(article => article.author === "John Doe");

console.log(result); // {title: "Autumn Recipes", author: "John Doe"}
```

`findLast()` làm việc giống như `find()`, nhưng bắt đầu tìm kiếm từ cuối mảng. Phương thức này trả về bài viết cuối cùng trong mảng mà được viết bởi “John Doe”.

**Tìm giao dịch tài chính cuối cùng lớn hơn 1000$**

```javascript
const transactions = [
  { amount: 750 },
  { amount: 1200 },
  { amount: 300 },
  { amount: 1500 }
];
const result = transactions.findLast(transaction => transaction.amount > 1000);

console.log(result); // {amount: 1500}
```

Phương thức này tìm phần tử cuối cùng trong mảng `transactions` mà số tiền (`amount`) lớn hơn 1000$. Khi tìm thấy, nó trả về giao dịch đó.

***

### Phương thức findIndex

#### Phương thức findIndex là gì?

Phương thức `findIndex()` trả về chỉ mục của phần tử đầu tiên trong mảng thỏa mãn hàm kiểm tra cung cấp. Nếu không có phần tử nào thỏa mãn, nó trả về `-1`.

**Khi nào sử dụng:** Cực kỳ hữu ích khi bạn cần biết vị trí của một phần tử thỏa mãn điều kiện nhất định trong mảng để có thể sử dụng vị trí đó cho các mục đích khác, như xóa hoặc thay thế phần tử.

Cú pháp:

```js
const foundIndex = array.findIndex(callbackFunction, thisValue);
```

* `callbackFunction`: Hàm kiểm tra được gọi cho mỗi phần tử trong mảng.
  * `element`: Phần tử hiện tại đang được xử lý.
  * `index` (tùy chọn): Chỉ mục của phần tử hiện tại.
  * `array` (tùy chọn): Mảng đang được sử dụng.
* `thisValue` (tùy chọn): Giá trị để sử dụng làm `this` khi thực hiện `callbackFunction`.

Ví dụ:

```javascript
const numbers = [4, 10, 18, 5, 24, 78];
const result = numbers.findIndex(num => num > 10);

console.log(result); // 2
```

Tương tự như `find()`, điểm khác biệt là thay vì trả về phần tử tìm thấy thì `findIndex()` trả về chỉ mục của phần tử tìm thấy. Trong ví dụ này, 18 là số đầu tiên trong mảng lớn hơn 10, vì vậy chỉ mục của nó là 2, được `findIndex()` trả về.

#### &#x20;Ví dụ sử dụng findIndex()

**Tìm chỉ mục của sản phẩm đầu tiên có tồn kho dưới 10 đơn vị**

```javascript
const inventories = [
  { product: "Pen", stock: 15 },
  { product: "Notebook", stock: 8 },
  { product: "Eraser", stock: 20 }
];
const result = inventories.findIndex(item => item.stock < 10);

console.log(result); // 1
```

`findIndex()` tìm chỉ mục của phần tử đầu tiên thỏa mãn điều kiện trong hàm kiểm tra, ở đây là tồn kho dưới 10. Nó trả về chỉ mục của sản phẩm đó trong mảng `inventories`.

**Tìm chỉ mục của sinh viên đầu tiên dưới 50 điểm**

```javascript
const students = [
  { name: "Liam", score: 85 },
  { name: "Olivia", score: 45 },
  { name: "Noah", score: 75 }
];
const result = students.findIndex(student => student.score < 50);

console.log(result); // 1
```

Phương thức này tìm chỉ mục của sinh viên đầu tiên trong mảng `students` có điểm số dưới 50. Khi tìm thấy, nó trả về chỉ mục của sinh viên đó.

***

### Phương thức findLastIndex

#### &#x20;Phương thức findLastIndex là gì?

`findLastIndex()` là phương thức tìm chỉ mục của phần tử đầu tiên tính từ cuối mảng thỏa mãn một hàm kiểm tra. Giống như `findIndex`, nếu không tìm thấy phần tử nào, phương thức này trả về `-1`.

**Khi nào sử dụng:** Thích hợp khi bạn cần xác định vị trí cuối cùng của phần tử thỏa mãn điều kiện, để có thể sử dụng vị trí đó cho các mục đích khác, như xóa hoặc thay thế phần tử.

Cú pháp:

```js
const foundLastIndex = array.findLastIndex(callbackFunction, thisValue);
```

* `callbackFunction`: Hàm kiểm tra được gọi cho mỗi phần tử trong mảng.
  * `element`: Phần tử hiện tại đang được xử lý.
  * `index` (tùy chọn): Chỉ mục của phần tử hiện tại.
  * `array` (tùy chọn): Mảng đang được sử dụng.
* `thisValue` (tùy chọn): Giá trị để sử dụng làm `this` khi thực hiện `callbackFunction`.

Ví dụ:

```javascript
const numbers = [4, 10, 18, 5, 24, 78];
const result = numbers.findLastIndex(num => num > 10);

console.log(result); // 5
```

Tương tự như `findLast()`, điểm khác biệt là thay vì trả về phần tử tìm thấy thì `findLastIndex()` trả về chỉ mục của phần tử tìm thấy. Trong ví dụ này, 78 là số cuối cùng trong mảng lớn hơn 10, vì vậy chỉ mục của nó trong mảng là 5, và đây là giá trị được trả về.

#### Ví dụ sử dụng findLastIndex()

**Tìm chỉ mục cuối cùng của mặt hàng “TV” với giá cao hơn 100$**

```javascript
const sales = [
  { item: "TV", price: 299 },
  { item: "Radio", price: 99 },
  { item: "TV", price: 350 },
  { item: "Radio", price: 30 }
];
const result = sales.findLastIndex(sale => sale.item === "TV" && sale.price > 100);

console.log(result); // 2
```

`findLastIndex()` tìm chỉ mục của phần tử cuối cùng thỏa mãn cả hai điều kiện: là một chiếc TV và có giá trên 100$. Phương thức này trả về chỉ mục cuối cùng thỏa mãn cả hai điều kiện đó.

**Tìm chỉ mục của bài đánh giá cuối cùng có đánh giá dưới 3 sao**

```javascript
const reviews = [
  { stars: 5 },
  { stars: 2 },
  { stars: 4 },
  { stars: 1 }
];
const result = reviews.findLastIndex(review => review.stars < 3);

console.log(result); // 3
```

Phương thức này tìm chỉ mục của bài đánh giá cuối cùng có số sao dưới 3. Đây là chỉ mục của bài đánh giá cuối cùng thỏa mãn điều kiện đó trong mảng `reviews`.

***

### Các sai lầm thường gặp

#### Sử dụng find, findLast, findIndex, findLastIndex không có return

Sai lầm phổ biến khi sử dụng các phương thức trên là quên `return` trong hàm callback. Nếu không có `return`, kết quả trả về luôn là `undefined` hoặc `-1` vì không có phần điều kiện nào thỏa mãn.

**Cách giải quyết**:

Đảm bảo rằng hàm callback của bạn có lệnh `return` đúng giá trị _truthy_ cần thiết.

```javascript
let numbers = [1, 2, 3, 4, 5];
let filteredNumbers = numbers.filter(function(item) {
  return item > 3;
});

console.log(filteredNumbers); // (2) [4, 5]
```

**Lưu ý**: Phương thức `find`, `findIndex`, `findLast`, và`findLastIndex` vẫn lặp qua các phần tử trống

```javascript
const arr = [0, 1, , , , 2, 3, 4, 5];

console.log(
  arr.find((item) => {
    console.log(item);
    return item === 10;
  })
);

// main.js:5 0
// main.js:5 1
// main.js:5 undefined
// main.js:5 undefined
// main.js:5 undefined
// main.js:5 2
// main.js:5 3
// main.js:5 4
// main.js:5 5
// main.js:3 undefined
```

{% hint style="info" %}
Tóm tắt

* **Phương thức find**: Tìm phần tử đầu tiên trong mảng thỏa mãn điều kiện nhất định.
  * **Cú pháp**: `const foundElement = array.find(callbackFunction, thisValue);`
  * **Ví dụ**: Tìm số đầu tiên lớn hơn 10 trong mảng `[4, 10, 18, 5, 24, 78]` trả về `18`.
* **Phương thức findLast**: Tìm phần tử cuối cùng từ phía cuối mảng thỏa mãn điều kiện.
  * **Cú pháp**: `const foundLastElement = array.findLast(callbackFunction, thisValue);`
  * **Ví dụ**: Tìm số cuối cùng lớn hơn 10 trong mảng `[4, 10, 18, 5, 24, 78]` trả về `78`.
* **Phương thức findIndex**: Trả về chỉ mục của phần tử đầu tiên trong mảng thỏa mãn điều kiện.
  * **Cú pháp**: `const foundIndex = array.findIndex(callbackFunction, thisValue);`
  * **Ví dụ**: Tìm chỉ mục của số đầu tiên lớn hơn 10 trong mảng `[4, 10, 18, 5, 24, 78]` trả về `2`.
* **Phương thức findLastIndex**: Tìm chỉ mục của phần tử cuối cùng từ cuối mảng thỏa mãn điều kiện.
  * **Cú pháp**: `const foundLastIndex = array.findLastIndex(callbackFunction, thisValue);`
  * **Ví dụ**: Tìm chỉ mục của số cuối cùng lớn hơn 10 trong mảng `[4, 10, 18, 5, 24, 78]` trả về `5`.
* **Sai lầm thường gặp**: Quên `return` trong hàm callback dẫn đến kết quả là `undefined` hoặc `-1`. Luôn đảm bảo hàm callback trả về giá trị `truthy` khi điều kiện đúng.
{% endhint %}
