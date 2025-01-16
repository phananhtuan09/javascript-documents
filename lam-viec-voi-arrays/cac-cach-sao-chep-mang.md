# Các cách sao chép mảng

Mục lục

* [Tại sao cần sao chép mảng](cac-cach-sao-chep-mang.md#tai-sao-can-sao-chep-mang)
* [Các cách sao chép mảng](cac-cach-sao-chep-mang.md#cac-cach-sao-chep-mang)
  * [Sử dụng phương thức slice()](cac-cach-sao-chep-mang.md#su-dung-phuong-thuc-slice)
  * [Sử dụng phương thức Object.assign()](cac-cach-sao-chep-mang.md#su-dung-phuong-thuc-object.assign)
  * [Sử dụng phương thức concat()](cac-cach-sao-chep-mang.md#su-dung-phuong-thuc-concat)
  * [Sử dụng phương thức Array.from()](cac-cach-sao-chep-mang.md#su-dung-phuong-thuc-array.from)
* [Sao chép nông và sâu](cac-cach-sao-chep-mang.md#sao-chep-nong-va-sau)
  * [Sao chép nông](cac-cach-sao-chep-mang.md#sao-chep-nong)
  * [Sao chép sâu](cac-cach-sao-chep-mang.md#sao-chep-sau)

### Tại sao cần sao chép mảng

Trong JavaScript, mảng là kiểu tham chiếu. Khi bạn gán một mảng cho một biến khác, cả hai biến sẽ tham chiếu đến cùng một địa chỉ bộ nhớ. Điều này có nghĩa là, nếu bạn thay đổi mảng thông qua một biến, mảng được tham chiếu qua biến kia cũng sẽ thay đổi. Để tránh điều này, cần phải sao chép mảng.

Ưu điểm khi sao chép mảng:

* Tránh được tình trạng hai biến tác động lẫn nhau thông qua tham chiếu chung.
* Giúp dễ dàng quản lý và dự đoán kết quả khi làm việc với các hàm, bảo đảm không làm thay đổi mảng gốc.

***

### Các cách sao chép mảng

#### Sử dụng phương thức slice()

Phương thức `slice()` trả về một bản sao nông của mảng, từ index bắt đầu cho đến index kết thúc mà không thay đổi mảng gốc. Nếu không chỉ định index, mặc định sẽ sao chép toàn bộ mảng.

```javascript
let original = [1, 2, 3];

// Copy toàn bộ mảng
let copied = original.slice();

// Thay đổi phần tử đầu tiên của mảng sao chép
copied[0] = 99;

console.log(original); // [1, 2, 3]
console.log(copied); // [99, 2, 3]
```

Mảng `copied` được tạo ra bởi phương thức `slice()` là một bản sao nông của `original`. Khi thay đổi `copied[0]` thành 99, chỉ mảng `copied` thay đổi, trong khi mảng `original` giữ nguyên giá trị ban đầu.

#### Sử dụng phương thức Object.assign()

`Object.assign()` thường được dùng để sao chép các thuộc tính từ một hoặc nhiều đối tượng nguồn vào một đối tượng đích. Khi dùng với mảng, nó tạo một bản sao nông của mảng.

```javascript
let original = [1, 2, 3];

// Sử dụng một mảng rỗng làm đích để sao chép vào
let copied = Object.assign([], original);

// Thay đổi phần tử thứ hai của mảng sao chép
copied[1] = 99;

console.log(original); // [1, 2, 3]
console.log(copied); // [1, 99, 3]
```

`copied` là kết quả của việc sao chép các phần tử của `original` vào một mảng rỗng. Khi thay đổi giá trị trong `copied`, mảng `original` không bị ảnh hưởng vì đây là một bản sao nông.

#### Sử dụng phương thức concat()

Phương thức `concat()` được sử dụng để nối các mảng lại với nhau. Khi được gọi mà không có đối số, nó trả về một bản sao nông của mảng gốc.

```javascript
let original = [1, 2, 3];

// Tạo bản sao của mảng original
let copied = original.concat();
// let copied = original.concat([]);
// let copied = [].concat(original);

// Thay đổi phần tử thứ ba của mảng sao chép
copied[2] = 99;

console.log(original); // [1, 2, 3]
console.log(copied); // [1, 2, 99]
```

Tạo `copied` bằng cách nối `original` vào một mảng rỗng. Thay đổi trên `copied` không ảnh hưởng đến `original` do đây là sao chép nông.

#### Sử dụng phương thức Array.from()

`Array.from()` tạo một bản sao nông mới từ một đối tượng có thể được chuyển đổi thành mảng hoặc một đối tượng giống như mảng (_được giới thiệu trong các chương tiếp theo_).

```javascript
let original = [1, 2, 3];

// Tạo bản sao của mảng
let copied = Array.from(original);

// Thay đổi phần tử đầu tiên của mảng sao chép
copied[0] = 99;

console.log(original); // [1, 2, 3]
console.log(copied); // [99, 2, 3]
```

Mảng `copied` là bản sao nông của `original` tạo ra qua `Array.from()`. Các thay đổi trên `copied` không tác động đến `original`, giúp đảm bảo tính toàn vẹn của mảng gốc.

***

### Sao chép nông và sâu

#### Sao chép nông

Những phương thức trên đều tạo ra các bản sao nông (_shallow copy_), có nghĩa là chúng chỉ sao chép các phần tử ở mức độ đầu tiên của mảng. Nếu các phần tử này là các đối tượng hoặc mảng khác, các thay đổi trên các đối tượng hoặc mảng con này vẫn ảnh hưởng đến mảng gốc.

Ví dụ:

```javascript
let a = [1, 2, 3, [5, 6, 7]];
let b = a.slice();

// Sửa phần tử đầu tiên trong mảng con
b[3][0] = 55;

// Ảnh hưởng với mảng gốc
console.log(a); // (4) [1, 2, 3, Array(3)]
```

#### Sao chép sâu

`structuredClone()` tạo một bản sao độc lập hoàn toàn của một đối tượng hoặc mảng gốc.

Ví dụ:

```javascript
let a = [1, 2, 3, [5, 6, 7]];
let b = structuredClone(a);

// Sửa phần tử đầu tiên trong mảng con
b[3][0] = 55;

// Không ảnh hưởng với mảng gốc
console.log(a); // (4) [1, 2, 3, Array(3)]
```

{% hint style="info" %}
Tóm tắt

* **Tại sao cần sao chép mảng**: Đảm bảo rằng các thay đổi trong một biến không ảnh hưởng đến biến khác, giúp giữ toàn vẹn mảng ban đầu.
  * **Phương thức slice()**: Tạo bản sao nông của mảng mà không ảnh hưởng đến mảng gốc.
  * **Phương thức Object.assign()**: Sao chép các phần tử của một mảng vào một mảng mới.
  * **Phương thức concat()**: Sử dụng để nối mảng nhưng cũng có thể tạo bản sao nông khi không truyền đối số, hoặc nối một mảng rỗng với mảng gốc.
  * **Phương thức Array.from()**: Tạo bản sao mới của mảng từ một đối tượng có thể chuyển đổi thành mảng.
* **Sao chép nông và sâu**: Sao chép nông, chỉ sao chép các phần tử ở mức độ đầu tiên. Sao chép sâu, sao chép độc lập toàn bộ cấu trúc của mảng bao gồm cả các đối tượng và mảng con.
  * **Ví dụ về sao chép nông**: Thay đổi trong bản sao ảnh hưởng đến mảng gốc nếu phần tử là mảng con hoặc đối tượng.
  * **Ví dụ về sao chép sâu**: Sao chép sâu, tạo bản sao độc lập hoàn toàn không liên kết với mảng gốc. Thay đổi trong bản sao không ảnh hưởng tới mảng gốc. Có thể sử dụng `structuredClone()` để sao chép sâu.
{% endhint %}
