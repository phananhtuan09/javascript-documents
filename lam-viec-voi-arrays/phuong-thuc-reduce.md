# Phương thức reduce()

Mục lục

* [Phương thức reduce() là gì?](phuong-thuc-reduce.md#phuong-thuc-reduce-la-gi)
* [Các cách làm việc với reduce()](phuong-thuc-reduce.md#cac-cach-lam-viec-voi-reduce)
  * [Tính tổng giá các sản phẩm](phuong-thuc-reduce.md#tinh-tong-gia-cac-san-pham)
  * [Tính tổng giá trị đơn hàng](phuong-thuc-reduce.md#tinh-tong-gia-tri-don-hang)
  * [Tạo một object với các giá trị ban đầu và số lần xuất hiện](phuong-thuc-reduce.md#tao-mot-object-voi-cac-gia-tri-ban-dau-va-so-lan-xuat-hien)
* [Các sai lầm thường gặp](phuong-thuc-reduce.md#cac-sai-lam-thuong-gap)
  * [Bỏ qua giá trị khởi tạo](phuong-thuc-reduce.md#bo-qua-gia-tri-khoi-tao)
  * [Sử dụng reduce() không hiệu quả](phuong-thuc-reduce.md#su-dung-reduce-khong-hieu-qua)

### Phương thức reduce() là gì?

`reduce()` là một phương thức của mảng trong JavaScript, dùng để thực hiện một hàm lên từng phần tử của mảng (từ trái sang phải) để rút ra một giá trị duy nhất. Nó thường được dùng để tính tổng, tính tích hoặc kết hợp các phần tử của mảng theo cách thức tùy ý.

Cú pháp:

```js
const result = array.reduce(callbackFunction(accumulator, currentValue, currentIndex, array) {
  // Trả về giá trị tích lũy
}, initialValue);
```

* `callbackFunction`: Hàm được gọi lại khi duyệt qua mỗi phần tử, gồm các tham số:
  * `accumulator`: Giá trị tích lũy được trả lại từ lần gọi hàm trước. Trong lần gọi đầu tiên, nếu `initialValue` được cung cấp, `accumulator` sẽ bằng `initialValue`, nếu không sẽ bằng phần tử đầu tiên của mảng.
  * `currentValue`: Giá trị của phần tử hiện tại đang được xử lý trong mảng.
  * `currentIndex` (tùy chọn): Index của phần tử hiện tại đang được xử lý. Nếu `initialValue` được cung cấp, duyệt từ index 0; nếu không, duyệt từ index 1.
  * `array` (tùy chọn): Mảng mà `reduce()` đang được áp dụng.
* `initialValue` (tùy chọn): Giá trị khởi tạo ban đầu cho `accumulator`. Nếu không cung cấp, `accumulator` sẽ nhận giá trị của phần tử đầu tiên trong mảng, và duyệt mảng bắt đầu từ phần tử thứ hai (index 1).

Ví dụ:

```javascript
const numbers = [1, 2, 3, 4];
const sum = numbers.reduce((total, number, index, arr) => {
    console.log(`Index ${index}: total = ${total}, number = ${number}`);
    return total + number;
}, 0); // initialValue là 0

console.log(sum); // Kết quả: 10
```

Trong ví dụ trên, `reduce()` tính tổng các số trong mảng `numbers`. Với mỗi lần lặp, hàm được gọi và giá trị của `total` và `number` được in ra. Giá trị khởi tạo `0` cho `total` được sử dụng trong lần gọi đầu tiên của hàm.

Sử dụng `reduce()` không chỉ giúp bạn tính toán các kết quả từ một mảng, mà còn cho phép bạn thực hiện các xử lý phức tạp hơn như chuyển đổi cấu trúc dữ liệu, tổng hợp thông tin, và hơn thế nữa.

***

### Các cách làm việc với reduce()

#### Tính tổng giá các sản phẩm

```javascript
const products = [
  { name: "iPhone", price: 100 },
  { name: "iPad", price: 200 },
  { name: "Macbook", price: 300 }
];

const total = products.reduce((sum, product) => {
  return sum + product.price;
}, 0);

console.log(total); // 600
```

#### Tính tổng giá trị đơn hàng

```javascript
const order = {
  code: "#DH001",
  products: [
    { name: "iPhone", price: 100, quantity: 1 },
    { name: "iPad", price: 200, quantity: 3 },
    { name: "Macbook", price: 300, quantity: 2 }
  ]
};

const total = order.products.reduce((sum, product) => {
  return sum + product.price * product.quantity;
}, 0);

console.log(total); // 1300
```

#### &#x20;Tạo một object với các giá trị ban đầu và số lần xuất hiện

```javascript
const items = ['apple', 'banana', 'apple', 'orange', 'banana', 'apple'];

const count = items.reduce((acc, item) => {
  acc[item] = (acc[item] || 0) + 1;
  return acc;
}, {});

console.log(count); // {apple: 3, banana: 2, orange: 1}
```

***

### Các sai lầm thường gặp

#### Bỏ qua giá trị khởi tạo

Nếu không cung cấp giá trị khởi tạo cho `reduce()`, phương thức sẽ lấy phần tử đầu tiên của mảng làm giá trị khởi tạo ban đầu, vì vậy có thể dẫn đến lỗi nếu mảng rỗng.

```javascript
const numbers = []; // Mảng rỗng

const total = numbers.reduce((sum, number) => {
  return sum + number;
}); // Không cung cấp giá trị khởi tạo
// Uncaught TypeError: Reduce of empty array with no initial value

console.log(total);
```

**Cách giải quyết:** Luôn cung cấp giá trị khởi tạo khi sử dụng `reduce()`.

```javascript
const numbers = []; // Mảng rỗng

const total = numbers.reduce((sum, number) => {
  return sum + number;
}, 0); // Thêm giá trị khởi tạo là 0

console.log(total); // 0
```

#### Sử dụng reduce() không hiệu quả

Dùng `reduce()` để thực hiện các tác vụ có thể xử lý đơn giản hơn bằng các phương thức khác như `forEach()`, `map()`, v.v.

```javascript
const numbers = [1, 2, 3];

const doubled = numbers.reduce((result, number) => {
  result.push(number * 2);
  return result;
}, []);

console.log(doubled); // (3) [2, 4, 6]
```

**Cách giải quyết:**

Xác định rõ ràng mục đích sử dụng của `reduce()` và lựa chọn phương thức phù hợp nhất cho nhu cầu xử lý.

```javascript
const numbers = [1, 2, 3];

const doubled = numbers.map(number => number * 2);

console.log(doubled); // (3) [2, 4, 6]
```

{% hint style="info" %}
Tóm tắt

* **Định nghĩa**: `reduce()` là một phương thức dùng để áp dụng một hàm lên từng phần tử của mảng và trả về một giá trị duy nhất. Nó thường được sử dụng để tính toán tổng, sản phẩm hoặc biến đổi dữ liệu của mảng.
* **Cú pháp**:
  * **callbackFunction**: Hàm xử lý cho mỗi phần tử, nhận các tham số là `accumulator` (giá trị tích lũy), `currentValue` (giá trị phần tử hiện tại), `currentIndex` (chỉ số phần tử hiện tại), và `array` (mảng đang được xử lý).
  * **initialValue**: Giá trị khởi tạo cho `accumulator`; nếu không được cung cấp, `accumulator` sẽ là phần tử đầu tiên của mảng, và duyệt mảng sẽ bắt đầu từ phần tử thứ hai (index 1).
* **Lưu ý**:
  * **Cần cung cấp initialValue**: Việc bỏ qua initialValue có thể dẫn đến lỗi nếu mảng là mảng rỗng.
  * **Chọn phương thức xử lý phù hợp**: `reduce()` có thể không phải là lựa chọn hiệu quả nhất cho mọi tình huống, đôi khi `map()` hoặc `forEach()` có thể phù hợp hơn (_ưu tiên sự đơn giản, hiệu quả bạn nhé_).
{% endhint %}
