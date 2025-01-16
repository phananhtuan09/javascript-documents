# Phương thức sort()

Mục lục

* [Phương thức sort()?](phuong-thuc-sort.md#phuong-thuc-sort)
* [Các cách làm việc với sort()](phuong-thuc-sort.md#cac-cach-lam-viec-voi-sort)
  * [Sắp xếp sản phẩm theo tên](phuong-thuc-sort.md#sap-xep-san-pham-theo-ten)
  * [Sắp xếp các số từ nhỏ đến lớn](phuong-thuc-sort.md#sap-xep-cac-so-tu-nho-den-lon)
  * [Sắp xếp danh sách sinh viên theo tên](phuong-thuc-sort.md#sap-xep-danh-sach-sinh-vien-theo-ten)
  * [Sắp xếp danh sách sinh viên theo điểm số](phuong-thuc-sort.md#sap-xep-danh-sach-sinh-vien-theo-diem-so)
* [Các sai lầm thường gặp](phuong-thuc-sort.md#cac-sai-lam-thuong-gap)
  * [Không cung cấp hàm so sánh khi cần thiết](phuong-thuc-sort.md#khong-cung-cap-ham-so-sanh-khi-can-thiet)
  * [Sử dụng sort() cho mảng có kiểu phức tạp](phuong-thuc-sort.md#su-dung-sort-cho-mang-co-kieu-phuc-tap)
  * [Quên rằng sort() thay đổi mảng ban đầu](phuong-thuc-sort.md#quen-rang-sort-thay-doi-mang-ban-dau)

### Phương thức sort()?

Phương thức `sort()` được dùng để sắp xếp các phần tử của một mảng theo một thứ tự xác định. Mặc định, các phần tử được sắp xếp theo thứ tự từ điển (_Unicode code points_).

Cú pháp:

```js
array.sort(compareFunction(a, b) {
  // return a negative, zero, or positive value
});
```

Tham số:

* `a`: Phần tử đầu tiên để so sánh.
* `b`: Phần tử thứ hai để so sánh.

Giá trị trả về:

* Trả về số âm để `a` được sắp xếp trước `b`.
* Trả về số dương để `a` được sắp xếp sau `b`.
* Trả về `0` để giữ nguyên vị trí của `a` và `b` .

`compareFunction` là một tham số không bắt buộc, bạn có thể cung cấp cho phương thức `sort()` để xác định cách các phần tử trong mảng được sắp xếp. Nếu không cung cấp `compareFunction`, mảng sẽ được sắp xếp dựa trên chuyển đổi các phần tử thành chuỗi và so sánh theo từng ký tự, từ trái sang phải.

Đây là cách mà phương thức này hoạt động (khi không cung cấp `compareFunction`):

1. **Chuyển đổi các phần tử thành chuỗi**: Mặc định, `sort()` sẽ chuyển đổi tất cả các phần tử của mảng thành chuỗi để so sánh.
2. **So sánh chuỗi**: Sau khi chuyển đổi, các chuỗi sẽ được so sánh theo từng ký tự, từ trái sang phải.
3. **Sắp xếp mảng**: Dựa trên kết quả của việc so sánh chuỗi, mảng sẽ được sắp xếp lại.

**Ví dụ 1:** Sắp xếp chuỗi

```javascript
let words = ["cherry", "banana",  "apple"];

words.sort();

console.log(words); // (3) ["apple", "banana", "cherry"]
```

**Ví dụ 2:** Sắp xếp số

```javascript
let numbers = [21, 2, 10, 3];

numbers.sort();

console.log(numbers); // (4) [10, 2, 21, 3]
```

> _Khi không cung cấp hàm so sánh, JavaScript chuyển đổi tất cả các phần tử thành chuỗi và sắp xếp chúng theo thứ tự từ điển của chuỗi Unicode, điều này có thể dẫn đến những kết quả không mong muốn khi sắp xếp các số._

**Ví dụ 3:** Sử dụng `compareFunction`

`compareFunction` cung cấp sự linh hoạt để sắp xếp mảng theo nhiều tiêu chí khác nhau, không chỉ giới hạn ở bảng chữ cái và không phụ thuộc vào loại dữ liệu.

```javascript
let numbers = [21, 2, 10, 3];

numbers.sort((a, b) => a - b);

console.log(numbers); // (4) [2, 3, 10, 21]
```

Phương thức `sort()` giúp dễ dàng sắp xếp dữ liệu, thường được sử dụng trong các tác vụ liên quan đến việc tổ chức, thống kê và hiển thị dữ liệu theo một trật tự nhất định.

***

### &#x20;Các cách làm việc với sort()

#### Sắp xếp sản phẩm theo tên

```javascript
let products = ["Orange", "apple", "Banana"];

products.sort((a, b) => a.localeCompare(b));

console.log(products); // (3) ["apple", "Banana", "Orange"]
```

#### &#x20;Sắp xếp các số từ nhỏ đến lớn

```javascript
let numbers = [10, 5, 40, 25, 1000, 1];

numbers.sort((a, b) => a - b);

console.log(numbers); // (6) [1, 5, 10, 25, 40, 1000]
```

#### Sắp xếp danh sách sinh viên theo tên

```javascript
let students = [
  { name: "John", score: 90 },
  { name: "Bob", score: 78 },
  { name: "Alice", score: 82 }
];

students.sort((a, b) => a.name.localeCompare(b.name));

console.log(students); // (3) [Object, Object, Object]
```

#### Sắp xếp danh sách sinh viên theo điểm số

```javascript
let students = [
  { name: "John", score: 90 },
  { name: "Bob", score: 78 },
  { name: "Alice", score: 82 }
];

students.sort((a, b) => b.score - a.score);

console.log(students); // (3) [Object, Object, Object]
```

***

### Các sai lầm thường gặp

#### Không cung cấp hàm so sánh khi cần thiết

Không sử dụng hàm so sánh cho các kiểu dữ liệu không phải chuỗi, dẫn đến kết quả không chính xác.

**Cách giải quyết:** Luôn cung cấp hàm so sánh phù hợp với kiểu dữ liệu của các phần tử trong mảng.

#### Sử dụng sort() cho mảng có kiểu phức tạp

“Tưởng” rằng `sort()` có thể xử lý mọi kiểu dữ liệu mà không cần hàm so sánh phức tạp.

**Cách giải quyết:** Phát triển hàm so sánh phức tạp và thử nghiệm kỹ càng để đảm bảo độ chính xác khi sắp xếp các kiểu phức tạp hơn như đối tượng hoặc mảng của mảng.

#### Quên rằng sort() thay đổi mảng ban đầu

Phương thức `sort()` thực sự sắp xếp và thay đổi mảng gốc, không tạo ra một bản sao mới.

**Cách giải quyết:** Nếu muốn giữ nguyên mảng gốc, hãy tạo bản sao của mảng trước khi sắp xếp.

{% hint style="info" %}
Tóm tắt

* **Giới thiệu Phương thức sort()**: Phương thức `sort()` là công cụ sắp xếp các phần tử của một mảng theo trật tự xác định. Thứ tự mặc định là sắp xếp theo từ điển dựa trên Unicode code points của chuỗi.
  * **Cú pháp chính**: `array.sort(compareFunction)`, trong đó `compareFunction` là hàm tùy chọn để xác định cách thức sắp xếp các phần tử.
* **Cơ chế hoạt động**: Không cung cấp `compareFunction`, `sort()` sẽ tự động chuyển đổi các phần tử của mảng thành chuỗi và sắp xếp chúng theo từng ký tự. Khi cung cấp `compareFunction`, người dùng có thể tùy chỉnh quy tắc sắp xếp, phù hợp với loại dữ liệu cụ thể của mảng.
  * **Ví dụ minh họa**: Sắp xếp các chuỗi và số mặc định; sử dụng `compareFunction` để sắp xếp số theo thứ tự tăng dần hoặc các đối tượng theo thuộc tính cụ thể.
* **Lưu ý và sai lầm thường gặp**:
  * **Sai lầm về kiểu dữ liệu**: Không sử dụng `compareFunction` khi sắp xếp các số có thể dẫn đến kết quả không như mong đợi do sự chênh lệch về giá trị Unicode của chữ số.
  * **Thay đổi mảng gốc**: `sort()` sắp xếp trực tiếp và thay đổi mảng gốc, điều này có thể không mong muốn trong một số trường hợp.
    * **Cách giải quyết**: Nếu muốn giữ nguyên mảng gốc, hãy tạo bản sao của mảng trước khi sắp xếp.
{% endhint %}
