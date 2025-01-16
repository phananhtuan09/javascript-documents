# Phương thức concat() và flat()

Mục lục

* [Phương thức concat()](phuong-thuc-concat-va-flat.md#phuong-thuc-concat)
  * [concat() là gì?](phuong-thuc-concat-va-flat.md#concat-la-gi)
  * [Cách làm việc với concat()](phuong-thuc-concat-va-flat.md#cach-lam-viec-voi-concat)
* [Phương thức flat()](phuong-thuc-concat-va-flat.md#phuong-thuc-flat)
  * [flat() là gì?](phuong-thuc-concat-va-flat.md#flat-la-gi)
  * [Cách làm việc với flat()](phuong-thuc-concat-va-flat.md#cach-lam-viec-voi-flat)
  * [Làm phẳng tối đa mảng](phuong-thuc-concat-va-flat.md#lam-phang-toi-da-mang)
* [Sai lầm thường gặp](phuong-thuc-concat-va-flat.md#sai-lam-thuong-gap)
  * [Quên rằng concat() và flat() không thay đổi mảng gốc](phuong-thuc-concat-va-flat.md#quen-rang-concat-va-flat-khong-thay-doi-mang-goc)

### Phương thức concat()

<figure><img src="../.gitbook/assets/6614ba2705afb.png" alt=""><figcaption></figcaption></figure>

#### concat() là gì?

Phương thức `concat()` được sử dụng để nối hai hoặc nhiều mảng lại với nhau và trả về một mảng mới mà không làm thay đổi các mảng ban đầu.

Cú pháp:

```js
let newArray = array1.concat(array2, array3, ..., arrayX);
```

Ví dụ:

```javascript
let fruits = ['apple', 'banana'];
let vegetables = ['carrot', 'pea'];

let combined = fruits.concat(vegetables);

console.log(combined); // (4) ["apple", "banana", "carrot", "pea"]
```

Phương thức `concat()` hữu ích khi bạn cần tạo ra một mảng mới từ các mảng hiện có mà không muốn thay đổi mảng gốc.

Ưu điểm:

* Dễ dàng hợp nhất nhiều mảng.
* Bảo toàn mảng gốc không bị thay đổi.

#### Cách làm việc với concat()

**Hợp nhất nhiều mảng**

Bạn có thể hợp nhất nhiều hơn hai mảng cùng một lúc.

```javascript
let a = [1, 2];
let b = [3, 4];
let c = [5, 6];

let d = a.concat(b, c);

console.log(d); //(6) [1, 2, 3, 4, 5, 6]
```

***

### Phương thức flat()

<figure><img src="../.gitbook/assets/6614ba3dc743f.png" alt=""><figcaption></figcaption></figure>

#### &#x20;flat() là gì?

Phương thức `flat()` được sử dụng để làm phẳng mảng lồng nhau thành một mảng duy nhất. Bạn có thể chỉ định mức độ làm phẳng bằng cách cung cấp một tham số cho phương thức này.

Cú pháp:

```js
let newArray = oldArray.flat(depth);
```

`depth` là mức độ làm phẳng, mặc định là `1`. Để làm phẳng tối đa mảng, sử dụng giá trị `Infinity`.

Ví dụ:

```javascript
let arr = [1, 2, [3, 4, [5, 6]]];

let flatArray = arr.flat(2);

console.log(flatArray); // (6) [1, 2, 3, 4, 5, 6]
```

Phương thức `flat()` là công cụ hữu ích khi bạn làm việc với các mảng đa chiều và cần chuyển chúng về dạng mảng một chiều để dễ dàng xử lý hơn.

Ưu điểm:

* Giảm phức tạp khi xử lý dữ liệu lồng nhau.
* Hỗ trợ tốt trong các thao tác xử lý dữ liệu như tìm kiếm, sắp xếp, và biến đổi.

#### Cách làm việc với flat()

**Làm phẳng mảng với mức độ cụ thể**

Để làm phẳng mảng với mức độ cụ thể, hãy truyền tham số là kiểu Number, tương ứng với mức độ muốn được làm phẳng.

```javascript
// Làm phẳng mảng với độ sâu 1
const arr1 = [1, 2, [3, 4]];
const newArr1 = arr1.flat();
// hoặc: const newArr1 = arr1.flat(1);

console.log(newArr1); // (4) [1, 2, 3, 4]

// Làm phẳng mảng với độ sâu 2
const arr2 = [1, 2, [3, 4, [5, 6]]];
const newArr2 = arr2.flat(2);

console.log(newArr2); // (6) [1, 2, 3, 4, 5, 6]
```

#### Làm phẳng tối đa mảng

Sử dụng `Infinity` để làm phẳng toàn bộ các mảng con.

```javascript
let deeplyNested = [1, [2, [3, [4, [5]]]]];
let completelyFlat = deeplyNested.flat(Infinity);

console.log(completelyFlat); // (5) [1, 2, 3, 4, 5]
```

***

### Sai lầm thường gặp

#### Quên rằng concat() và flat() không thay đổi mảng gốc

Nhiều người mới học thường quên mất concat không làm thay đổi các mảng gốc.

Ví dụ: Với `concat()`.

```javascript
let original = [1, 2];
let newItems = [3, 4];

original.concat(newItems);

console.log(original); // Không thay đổi (2) [1, 2]
```

Với `flat()`:

```javascript
let original = [[1, 2], [3, 4]];

original.flat();

console.log(original); // Không thay đổi (2) [Array(2), Array(2)]
```

**Cách giải quyết**: `concat()` và `flat()` trả về một mảng mới, luôn nhận giá trị được trả về để sử dụng.

Với `concat()`:

```javascript
let original = [1, 2];
let newItems = [3, 4];

let merged = original.concat(newItems);

console.log(merged); // (4) [1, 2, 3, 4]
```

Với `flat()`:

```javascript
let original = [[1, 2], [3, 4]];
let flattened = original.flat();

console.log(flattened); // (4) [1, 2, 3, 4]
```

{% hint style="info" %}
Tóm tắt

* **Phương thức concat()**:
  * `concat()` dùng để nối hai hoặc nhiều mảng lại với nhau mà không làm thay đổi mảng ban đầu. Kết quả là một mảng mới chứa tất cả các phần tử từ các mảng được nối.
  * **Sử dụng**: Gọi `concat()` với các mảng là đối số để tạo mảng mới chứa các phần tử của tất cả mảng.
* **Phương thức flat()**:
  * `flat()` dùng để làm phẳng mảng lồng nhau thành một mảng duy nhất. Mức độ làm phẳng có thể được chỉ định qua tham số `depth`.
  * **Sử dụng**: Gọi `flat(depth)` với `depth` là độ sâu cần làm phẳng. Sử dụng `Infinity` để làm phẳng mọi mảng con.
{% endhint %}
