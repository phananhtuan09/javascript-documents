# Phương thức của Object

Mục lục

* [Object.keys(obj)](phuong-thuc-cua-object.md#object.keys-obj)
* [Object.values(obj)](phuong-thuc-cua-object.md#object.values-obj)
* [Object.entries(obj)](phuong-thuc-cua-object.md#object.entries-obj)
* [Object.assign(target, …sources)](phuong-thuc-cua-object.md#object.assign-target-...sources)
* [Object.freeze(obj)](phuong-thuc-cua-object.md#object.freeze-obj)
* [Object.seal(obj)](phuong-thuc-cua-object.md#object.seal-obj)

JavaScript cung cấp nhiều phương thức hữu ích để làm việc với object. Dưới đây là một số phương thức quan trọng và phổ biến nhất:

### Object.keys(obj)

Phương thức `Object.keys` trả về một mảng chứa tất cả các _keys_ (tức là tên của các thuộc tính) từ một đối tượng.

> _Điều này rất hữu ích khi bạn cần duyệt qua tất cả các thuộc tính của một đối tượng, hoặc khi bạn muốn kiểm tra đối tượng có những thuộc tính nào._

Ví dụ:

```javascript
// Định nghĩa một đối tượng với ba thuộc tính
const obj = { a: 1, b: 2, c: 3 };

// Sử dụng Object.keys để lấy ra tất cả keys của đối tượng
console.log(Object.keys(obj));
// (3) ["a", "b", "c"]
```

Trong ví dụ trên, `Object.keys(obj)` trả về một mảng gồm các chuỗi `"a"`, `"b"`, và `"c"`, tương ứng với các _keys_ của đối tượng `obj`. Điều này cho phép chúng ta biết được đối tượng `obj` chứa ba thuộc tính và tên của chúng.

**Ứng dụng:**

`Object.keys` có thể được sử dụng trong nhiều tình huống, chẳng hạn:

* **Duyệt qua các thuộc tính của đối tượng**: Bạn có thể sử dụng mảng trả về từ `Object.keys` để duyệt qua các thuộc tính của đối tượng và xử lý từng cặp key-value một cách linh hoạt.
* **Kiểm tra đối tượng rỗng**: Bằng cách kiểm tra độ dài của mảng trả về từ `Object.keys(obj)`, bạn có thể xác định nhanh chóng một đối tượng có chứa bất kỳ thuộc tính nào không.

***

### Object.values(obj)

Phương thức `Object.values` trả về một mảng chứa tất cả các giá trị của các thuộc tính từ một đối tượng.

> _Điều này giúp bạn dễ dàng truy cập và xử lý các giá trị của đối tượng mà không cần quan tâm đến các keys của chúng._

Ví dụ:

```javascript
// Định nghĩa một đối tượng với ba thuộc tính
const obj = { a: 1, b: 2, c: 3 };

// Sử dụng Object.values để lấy ra tất cả values của đối tượng
console.log(Object.values(obj)); // [1, 2, 3]
```

Trong ví dụ này, `Object.values(obj)` trả về một mảng gồm các số `1`, `2`, và `3`, tương ứng với các giá trị của các thuộc tính trong đối tượng `obj`. Cách này cho phép chúng ta dễ dàng truy cập vào các giá trị của đối tượng mà không cần phải biết tên cụ thể của các thuộc tính.

**Ứng dụng:**

Phương thức `Object.values` có thể được sử dụng trong nhiều trường hợp, bao gồm:

* **Tính toán trên các giá trị của đối tượng**: Bạn có thể dễ dàng thực hiện các phép toán hoặc xử lý các giá trị, chẳng hạn như tìm giá trị lớn nhất, nhỏ nhất, hoặc tổng của các giá trị.
* **Xác định đối tượng có giá trị nào không**: Giống như `Object.keys`, bạn có thể sử dụng `Object.values` để kiểm tra xem một đối tượng có chứa bất kỳ giá trị nào không bằng cách kiểm tra độ dài của mảng trả về.

***

### Object.entries(obj)

Phương thức `Object.entries` trả về một mảng chứa các cặp `[key, value]` cho mỗi thuộc tính trong đối tượng. Mỗi cặp `[key, value]` là một mảng gồm hai phần tử, với phần tử đầu tiên là tên của thuộc tính (key) và phần tử thứ hai là giá trị tương ứng của thuộc tính đó (value). Điều này giúp bạn có thể trực tiếp duyệt qua và xử lý dữ liệu đối tượng một cách linh hoạt.

Ví dụ:

```javascript
// Định nghĩa một đối tượng với ba thuộc tính
const obj = { a: 1, b: 2, c: 3 };

// Sử dụng Object.entries để lấy ra các cặp [key, value]
console.log(Object.entries(obj)); // [["a", 1], ["b", 2], ["c", 3]]
```

Trong ví dụ trên, `Object.entries(obj)` trả về một mảng gồm các mảng con, mỗi mảng con chứa một cặp `[key, value]`. Cách này cho phép bạn dễ dàng truy cập và xử lý từng cặp key-value một.

**Ứng dụng:**

`Object.entries` rất hữu ích trong nhiều tình huống, bao gồm:

* **Duyệt qua đối tượng**: Bạn có thể sử dụng `Object.entries` kết hợp với các vòng lặp như `for...of` để duyệt qua và xử lý từng cặp key-value của đối tượng.
* **Chuyển đổi đối tượng thành đối tượng đặc biệt khác**: _Sẽ học trong các chương nâng cao hơn_.

***

### Object.assign(target, …sources)

Phương thức `Object.assign` cho phép bạn sao chép các thuộc tính từ một hoặc nhiều đối tượng nguồn (`source objects`) vào một đối tượng đích (`target object`).

> _Nó rất hữu ích trong các tình huống bạn muốn kết hợp các thuộc tính từ nhiều đối tượng vào một đối tượng duy nhất, hoặc khi bạn cần tạo một bản sao của đối tượng với một số thay đổi nhỏ._

Phương thức này nhận đối tượng đích làm tham số đầu tiên, tiếp theo là một hoặc nhiều đối tượng nguồn. Các thuộc tính từ các đối tượng nguồn sẽ được sao chép vào đối tượng đích. Nếu có các thuộc tính trùng lặp, giá trị từ các đối tượng nguồn sẽ ghi đè lên giá trị trong đối tượng đích.

Ví dụ:

```javascript
// Định nghĩa đối tượng đích và đối tượng nguồn
const target = { a: 1, b: 2 };
const source = { b: 4, c: 5 };

// Sử dụng Object.assign để sao chép thuộc tính từ source sang target
const returnedTarget = Object.assign(target, source);

// Hiển thị kết quả
console.log(target); // { a: 1, b: 4, c: 5 }
console.log(returnedTarget); // { a: 1, b: 4, c: 5 }
```

Trong ví dụ trên, `Object.assign` được sử dụng để sao chép thuộc tính từ `source` sang `target`. Lưu ý rằng thuộc tính `b` trong `target` ban đầu có giá trị là `2`, nhưng sau khi áp dụng `Object.assign`, nó được ghi đè bởi giá trị `4` từ `source`. Cả `target` và `returnedTarget` đều trỏ tới cùng một đối tượng sau khi sao chép, cho thấy phương thức này thực sự thay đổi đối tượng đích và cũng trả về nó.

***

### Object.freeze(obj)

Sử dụng phương thức `Object.freeze` để “đóng băng” một đối tượng, làm cho tất cả các thuộc tính của đối tượng đó trở nên không thể thay đổi. Một khi đối tượng đã bị đóng băng, bạn sẽ không thể:

* Thêm thuộc tính mới vào đối tượng
* Sửa đổi giá trị của các thuộc tính hiện có
* Xóa các thuộc tính từ đối tượng

Ví dụ:

```javascript
const frozenObj = Object.freeze({ a: 1 });

frozenObj.a = 2; // Cố gắng thay đổi giá trị của 'a' không có hiệu lực
frozenObj.b = 3; // Cố gắng thêm thuộc tính mới 'b' không thành công

console.log(frozenObj.a); // 1
console.log(frozenObj.b); // undefined
```

Trong ví dụ trên, mặc dù có cố gắng thay đổi giá trị của thuộc tính a và thêm một thuộc tính mới `b`, nhưng `frozenObj` vẫn giữ nguyên giá trị ban đầu của `a` và không chấp nhận thuộc tính mới, chứng minh rằng đối tượng đã được “đóng băng” thành công.

**Ứng dụng:**

`Object.freeze` thường được sử dụng khi bạn muốn:

* Bảo vệ tính toàn vẹn của dữ liệu trong một đối tượng, ngăn chặn sự thay đổi không mong muốn.
* Tạo các “hằng số đối tượng” trong chương trình, nơi bạn không muốn bất kỳ thuộc tính nào của đối tượng bị thay đổi sau khi nó được tạo.

**Lưu ý:** Mặc dù `Object.freeze` ngăn chặn sự thay đổi của đối tượng ở cấp độ ngoài cùng, nó không áp dụng cho các đối tượng con. Điều này có nghĩa là nếu một thuộc tính của đối tượng “đóng băng” là một đối tượng khác, bạn vẫn có thể thay đổi thuộc tính của đối tượng con đó.

***

### Object.seal(obj)

Sử dụng `Object.seal` để ngăn chặn việc thêm hoặc xóa các thuộc tính từ một đối tượng, trong khi vẫn cho phép sửa đổi giá trị của các thuộc tính hiện tại. Điều này hữu ích khi bạn muốn cố định cấu trúc của một đối tượng nhưng không muốn hạn chế khả năng cập nhật giá trị của các thuộc tính.

Ví dụ:

```javascript
const sealedObj = Object.seal({ a: 1 });

sealedObj.a = 2; // Thay đổi giá trị của thuộc tính 'a' thành công
sealedObj.b = 3; // Cố gắng thêm thuộc tính mới 'b' không thành công

console.log(sealedObj.a); // 2
console.log(sealedObj.b); // undefined
```

Trong ví dụ trên, mặc dù chúng ta có thể thay đổi giá trị của thuộc tính `a` từ `1` sang `2`, nhưng không thể thêm thuộc tính mới `b` vào đối tượng. Điều này chứng minh đối tượng đã được “niêm phong” thành công.

**Ứng dụng:**

* `Object.seal` thường được sử dụng khi bạn muốn cố định cấu trúc của đối tượng để ngăn chặn thêm hoặc xóa thuộc tính, nhưng vẫn muốn cho phép thay đổi giá trị của các thuộc tính hiện có.
* Điều này giúp đảm bảo tính toàn vẹn của đối tượng trong quá trình thực thi chương trình, ngăn chặn các thay đổi không mong muốn đến cấu trúc đối tượng mà vẫn giữ được sự linh hoạt.

**Lưu ý:** Giống như `Object.freeze`, `Object.seal` cũng chỉ áp dụng cho cấp độ ngoài cùng của đối tượng. Những đối tượng con sẽ không bị ảnh hưởng bởi `Object.seal` và có thể được thêm hoặc xóa thuộc tính bình thường.

{% hint style="info" %}
Tóm tắt

* **Phương thức Object.keys**: Trả về một mảng chứa tất cả các keys từ một đối tượng. Hữu ích khi cần duyệt qua tất cả thuộc tính của đối tượng hoặc kiểm tra đối tượng có những thuộc tính nào.
  * **Ứng dụng**: Duyệt qua thuộc tính, kiểm tra đối tượng rỗng.
* **Phương thức Object.values**: Trả về một mảng chứa tất cả giá trị của các thuộc tính từ một đối tượng. Giúp dễ dàng truy cập và xử lý các giá trị của đối tượng.
  * **Ứng dụng**: Tính toán trên giá trị đối tượng, xác định đối tượng có giá trị nào không.
* **Phương thức Object.entries**: Trả về một mảng chứa các cặp `[key, value]` cho mỗi thuộc tính trong đối tượng, giúp dễ dàng duyệt qua và xử lý dữ liệu.
  * **Ứng dụng**: Duyệt qua đối tượng, chuyển đổi đối tượng.
* **Phương thức Object.assign**: Sao chép các thuộc tính từ một hoặc nhiều đối tượng nguồn vào một đối tượng đích. Rất hữu ích khi cần kết hợp thuộc tính từ nhiều đối tượng hoặc tạo bản sao đối tượng với thay đổi nhỏ.
* **Phương thức Object.freeze**: “Đóng băng” một đối tượng làm cho tất cả thuộc tính trở nên không thể thay đổi. Hữu ích để bảo vệ dữ liệu, tạo "hằng
  * **Lưu ý**: Chỉ áp dụng cho cấp độ ngoài cùng của đối tượng không đóng băng được đối tượng con bên trong.
* **Phương thức Object.seal**: Ngăn chặn việc thêm hoặc xóa các thuộc tính từ một đối tượng, nhưng cho phép sửa đổi giá trị của các thuộc tính hiện tại.
  * **Ứng dụng**: Cố định cấu trúc đối tượng, ngăn chặn thay đổi không mong muốn đến cấu trúc đối tượng.
  * **Lưu ý**: Chỉ áp dụng cho cấp độ ngoài cùng của đối tượng.
{% endhint %}

