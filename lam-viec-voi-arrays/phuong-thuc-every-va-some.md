# Phương thức every() và some()

Mục lục

* [Phương thức every](phuong-thuc-every-va-some.md#phuong-thuc-every)
  * [Phương thức every là gì?](phuong-thuc-every-va-some.md#phuong-thuc-every-la-gi)
  * [Ví dụ sử dụng every](phuong-thuc-every-va-some.md#vi-du-su-dung-every)
* [Phương thức some](phuong-thuc-every-va-some.md#phuong-thuc-some)
  * [Phương thức some() là gì?](phuong-thuc-every-va-some.md#phuong-thuc-some-la-gi)
  * [Ví dụ sử dụng some()](phuong-thuc-every-va-some.md#vi-du-su-dung-some)
  * [Kiểm tra xem có sản phẩm nào hết hàng không](phuong-thuc-every-va-some.md#kiem-tra-xem-co-san-pham-nao-het-hang-khong)
* [Các sai lầm thường gặp](phuong-thuc-every-va-some.md#cac-sai-lam-thuong-gap)
  * [Hiểu nhầm về giá trị trả về của every()](phuong-thuc-every-va-some.md#hieu-nham-ve-gia-tri-tra-ve-cua-every)

### Phương thức every

#### &#x20;Phương thức every là gì?

`every` là một phương thức kiểm tra xem tất cả các phần tử của mảng có thỏa mãn điều kiện được cung cấp bởi một hàm kiểm tra hay không. Nếu tất cả phần tử thỏa mãn điều kiện, phương thức trả về `true`; ngược lại, nó trả về `false`.

Cú pháp:

```js
const bool = array.every(callbackFunction(element, index, array) {
  // Điều kiện kiểm tra
}, thisValue);
```

Ví dụ:

```javascript
const ages = [18, 20, 25, 30];

// Kiểm tra toàn bộ phần tử có từ 18 trở lên không
const result = ages.every(age => age >= 18);

console.log(result); // true
```

Phương thức `every` hữu ích khi bạn cần xác định liệu tất cả các phần tử trong một mảng có đáp ứng một tiêu chuẩn nhất định hay không. Nó được dùng để đảm bảo tính nhất quán của dữ liệu trong một tập hợp.

#### &#x20;Ví dụ sử dụng every

**Kiểm tra xem tất cả các sản phẩm trong giỏ hàng có sẵn trong kho không**

```javascript
  { name: "Apple", stock: 10 },
  { name: "Cherry", stock: 5 },
  { name: "Banana", stock: 0 }
];

const result = products.every(product => product.stock > 0);

console.log(result); // false
```

**Đảm bảo rằng tất cả thành viên trong một nhóm đều từ 18 tuổi.**

```javascript
const members = [
  { name: "Bob", age: 10 },
  { name: "John", age: 20 },
  { name: "Alice", age: 18 }
];

const result = members.every(member => member.age >= 18);

console.log(result); // false
```

***

### Phương thức some

#### &#x20;Phương thức some() là gì?

`some()` là một phương thức của mảng trong JavaScript, được sử dụng để kiểm tra xem có ít nhất một phần tử trong mảng có thỏa mãn một điều kiện cụ thể được xác định bởi một hàm callback hay không. Nếu có một phần tử thỏa mãn điều kiện này, phương thức trả về `true`, ngược lại nó trả về `false`.

Cú pháp:

```js
const bool = array.some(callbackFunction(element, index, array) {
  // Điều kiện kiểm tra
}, thisValue);
```

Ví dụ:

```javascript
const numbers = [1, 5, 2, 7, 8, 10];

// Kiểm tra trong mảng có chứa số chẵn không
const result = numbers.some(number => number % 2 === 0);

console.log(result); // true
```

Phương thức `some()` rất hữu ích khi bạn chỉ cần xác định xem trong một mảng có phần tử nào đó thỏa mãn một điều kiện nhất định hay không, mà không cần tất cả phải thỏa mãn điều kiện đó.

#### Ví dụ sử dụng some()

**Kiểm tra xem có bất cứ học sinh nào từ 60 điểm trở lên**

```javascript
const students = [
  { name: 'John', score: 55 },
  { name: 'Bob', score: 80 },
  { name: 'Alice', score: 45 }
];

const result = students.some(student=> student.score >= 60);

console.log(result); // true

```

#### &#x20;Kiểm tra xem có sản phẩm nào hết hàng không

```javascript
const products = [
  { name: 'Tablet', stock: 10 },
  { name: 'Laptop', stock: 0 },
  { name: 'Phone', stock: 5 }
];

const result = products.some(product => product.stock === 0);

console.log(result); // true
```

***

### Các sai lầm thường gặp

#### Hiểu nhầm về giá trị trả về của every()

Nhiều người mới học thường nhầm lẫn rằng `every` sẽ trả về `false` nếu mảng rỗng. Tuy nhiên, theo định nghĩa, `every` sẽ trả về `true` cho mảng rỗng vì không có phần tử nào vi phạm điều kiện.

```javascript
const numbers = [];

const result = numbers.every(num => num > 0);

console.log(result); // true

if (result) {
  console.log('Do something...');
}
```

**Cách giải quyết:** Luôn kiểm tra mảng có phần tử trước khi áp dụng `every`.

```javascript
const numbers = [];

const result = numbers.every(num => num > 0);

if (numbers.length && result) {
  console.log('Do something...');
}
```

Ngược lại phương thức `some` luôn trả về `false` khi mảng rỗng.

**Lưu ý**: Phương thức `every`  và `some` không chạy trên các phương thức trống.

{% hint style="info" %}
Tóm tắt

* **Phương thức every**: `every` là phương thức kiểm tra liệu tất cả các phần tử trong mảng có thỏa mãn điều kiện cho trước hay không. Nếu tất cả phần tử thỏa mãn, trả về `true`; ngược lại trả về `false`.
  * **Ví dụ minh họa**: Kiểm tra xem tất cả thành viên trong nhóm có đủ 18 tuổi trở lên không.
* **Phương thức some**: `some` là phương thức kiểm tra xem có ít nhất một phần tử trong mảng thỏa mãn điều kiện cho trước hay không. Trả về `true` nếu có ít nhất một phần tử thỏa mãn, ngược lại trả về `false`.
  * **Ví dụ minh họa**: Kiểm tra trong mảng có chứa ít nhất một số chẵn không.
* **Hiểu nhầm thường gặp với every**: Một số người mới học nhầm lẫn rằng `every` trả về `false` cho mảng rỗng. Tuy nhiên, `every` thực sự trả về `true` cho mảng rỗng vì không có phần tử nào vi phạm điều kiện.
{% endhint %}
