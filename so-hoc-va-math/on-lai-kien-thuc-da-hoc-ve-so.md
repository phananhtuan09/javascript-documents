# Ôn lại kiến thức đã học về số

### Cách viết số rút gọn

Ví dụ để biểu diễn sô `500000000` ta có thể dùng cách sau:

```javascript
console.log(500000000);
console.log(5*10**8);
console.log(5e8);
```

***

### NaN trong Javascript

**NaN** (Not-A-Number) là giá trị biểu thị rằng một giá trị không phải là một số hợp lệ. Dưới đây là các trường hợp và hành vi liên quan đến `NaN` trong JavaScript.

&#x20;**Các phép toán trả về NaN**

Có năm loại phép toán khác nhau dẫn đến kết quả là NaN:

* **Chuyển đổi sang số thất bại:**
  * Ví dụ: `parseInt("blabla")`, `Number(undefined)`, hoặc `Math.abs(undefined)`.
* **Phép toán toán học có kết quả không phải là số thật:**
  * Ví dụ: `Math.sqrt(-1)`.
* **Dạng không xác định:**
  * Ví dụ: `0 * Infinity`, `1 ** Infinity`, `Infinity / Infinity`, `Infinity - Infinity`.
* **Toán hạng là NaN hoặc bị ép kiểu thành NaN:**
  * Ví dụ: `7 ** NaN`, `7 * "blabla"`.
* **Biểu diễn giá trị không hợp lệ dưới dạng số:**
  * Ví dụ: `new Date("blabla").getTime()`, hoặc `"".charCodeAt(1)`.

**Các hành vi của NaN**

NaN và các hành vi của nó được quy định bởi chuẩn **IEEE 754** và không phải do JavaScript tự phát minh. Các đặc điểm quan trọng của NaN bao gồm:

* **Lan truyền qua các phép toán:**
  * Nếu NaN xuất hiện trong một phép toán toán học (ngoại trừ các phép toán bitwise), kết quả thường cũng là NaN.
* **Không xác định trong so sánh quan hệ:**
  * Khi NaN là một trong các toán hạng của phép so sánh (`>`, `<`, `>=`, `<=`), kết quả luôn là `false`.
* **Không bằng bất kỳ giá trị nào, kể cả chính nó:**
  * Ví dụ: `NaN === NaN // false`.
* **Là một giá trị "falsy":**
  * NaN được coi là "falsy" khi ép kiểu sang boolean.

**Kiểm tra giá trị là NaN**

Để kiểm tra xem một giá trị có phải là NaN hay không, bạn có thể sử dụng:

**`Number.isNaN()` hoặc `isNaN()`:**

* `Number.isNaN()` chỉ trả về `true` nếu giá trị hiện tại là NaN.
* `isNaN()` trả về `true` nếu giá trị hiện tại là NaN hoặc sẽ trở thành NaN sau khi được ép kiểu sang số.

Ví dụ:

```javascript
isNaN("hello world"); // true
Number.isNaN("hello world"); // false
```

Khi sử dụng `isNaN()` với `BigInt`, sẽ có lỗi:

```javascript
isNaN(1n); // TypeError
Number.isNaN(1n); // false
```

Một số phương thức mảng không thể tìm thấy NaN, nhưng một số khác thì có thể:

**Không thể tìm thấy NaN:**

*   Các phương thức tìm chỉ mục như `indexOf()` và `lastIndexOf()`:

    ```javascript
    const arr = [2, 4, NaN, 12];
    arr.indexOf(NaN); // -1
    ```

**Có thể tìm thấy NaN:**

*   Các phương thức tìm giá trị như `includes()`:

    ```javascript
    arr.includes(NaN); // true
    ```

**Sử dụng predicate để tìm NaN:**

*   Các phương thức chấp nhận hàm kiểm tra:

    ```javascript
    arr.findIndex((n) => Number.isNaN(n)); // 2
    ```

NaN thường lan truyền qua các phép toán, nhưng có một trường hợp ngoại lệ là phép lũy thừa với số mũ bằng 0. Kết quả sẽ luôn là `1`, bất kể cơ số là gì:

```javascript
NaN ** 0 === 1; // true
```

***

### Number.prototype.toFixed

Phương thức `toFixed()` trả về một chuỗi biểu diễn số đó với phần thập phân được chỉ định.

**Cú pháp**

```javascript
toFixed()
toFixed(digits)
```

**Tham số:**

* **`digits`** _(Không bắt buộc)_: Số chữ số xuất hiện sau dấu thập phân; phải nằm trong khoảng từ 0 đến 100 Nếu không chỉ định tham số này, mặc định là 0.

**Giá trị trả về:** Một chuỗi biểu diễn số với phần thập phân được chỉ định.&#x20;

**Ngoại lệ:**

* **`RangeError`**: Ném ra nếu `digits` không nằm trong khoảng từ 0 đến 100.
* **`TypeError`**: Ném ra nếu phương thức này được gọi trên một đối tượng không phải là số.

**Mô tả**

Phương thức **toFixed()** trả về chuỗi biểu diễn của một số có chính xác `digits` chữ số sau dấu thập phân.

* Số sẽ được làm tròn nếu cần thiết.
* Phần thập phân được thêm số 0 nếu cần để đạt độ dài chỉ định.

Nếu giá trị tuyệt đối của số lớn hơn hoặc bằng 10^21 , phương thức này sử dụng cùng một thuật toán như `Number.prototype.toString()` và trả về chuỗi theo ký hiệu khoa học. Nếu số không phải là hữu hạn, phương thức sẽ trả về "Infinity", "NaN", hoặc "-Infinity".

Đầu ra của `toFixed()` có thể chính xác hơn `toString()` đối với một số giá trị, vì `toString()` chỉ in đủ chữ số có nghĩa để phân biệt số đó với các giá trị liền kề.

Ví dụ:

```javascript
(1000000000000000128).toString(); // '1000000000000000100'
(1000000000000000128).toFixed(0); // '1000000000000000128'
```

Tuy nhiên, việc chọn độ chính xác chữ số thập phân quá cao có thể trả về kết quả không mong muốn, do số thập phân không thể được biểu diễn chính xác trong dấu chấm động.

Ví dụ:

```javascript
(0.3).toFixed(50); // '0.29999999999999998889776975374843459576368331909180'
```

**Ví dụ sử dụng**

**Sử dụng `toFixed()`:**

```javascript
const numObj = 12345.6789;

numObj.toFixed();      // '12346'; làm tròn, không có phần thập phân
numObj.toFixed(1);     // '12345.7'; làm tròn lên
numObj.toFixed(6);     // '12345.678900'; thêm số 0
(1.23e20).toFixed(2);  // '123000000000000000000.00'
(1.23e-10).toFixed(2); // '0.00'
(2.34).toFixed(1);     // '2.3'
(2.35).toFixed(1);     // '2.4'; làm tròn lên
(2.55).toFixed(1);     // '2.5'; làm tròn xuống do giới hạn dấu chấm động
(2.449999999999999999).toFixed(1); // '2.5'; làm tròn lên
(6.02 * 10 ** 23).toFixed(50);     // '6.019999999999999e+23'; số lớn vẫn dùng ký hiệu khoa học
```

**Sử dụng `toFixed()` với số âm:** Do toán tử trừ có độ ưu tiên cao hơn so với truy cập thuộc tính, bạn cần nhóm biểu thức số âm để nhận về chuỗi:

```javascript
-2.34.toFixed(1);  // -2.3, kết quả là số
(-2.34).toFixed(1); // '-2.3', kết quả là chuỗi
```
