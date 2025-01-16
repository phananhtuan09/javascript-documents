# Các loại hàm trong JavaScript

Mục lục

* [3 loại hàm trong JavaScript?](cac-loai-ham-trong-javascript.md#id-3-loai-ham-trong-javascript)
  * [Hàm khai báo là gì?](cac-loai-ham-trong-javascript.md#ham-khai-bao-la-gi)
  * [Hàm biểu thức là gì?](cac-loai-ham-trong-javascript.md#ham-bieu-thuc-la-gi)
  * [Hàm mũi tên là gì?](cac-loai-ham-trong-javascript.md#ham-mui-ten-la-gi)
* [Khi nào thì sử dụng loại hàm nào?](cac-loai-ham-trong-javascript.md#khi-nao-thi-su-dung-loai-ham-nao)

### 3 loại hàm trong JavaScript?

#### Hàm khai báo là gì?

Hàm khai báo (Declaration function) là cách truyền thống để định nghĩa một hàm trong JavaScript. Hàm này có thể được gọi trước khi nó được định nghĩa.

Cú pháp:

```js
function tenHam(thamSo) {
  // Khối lệnh
}
```

Ví dụ thực tế:

```javascript
function tinhTong(a, b) {
  return a + b;
}
console.log(tinhTong(5, 3)); // 8
```

_**Khuyến nghị**: Nên gọi hàm sau khi khai báo giúp code trở nên dễ dàng đọc-hiểu hơn, nhất là khi chúng ta mới học JavaScript._

#### Hàm biểu thức là gì?

Hàm biểu thức (Function expression) là một cách để định nghĩa hàm thông qua việc gán hàm cho một biến. Hàm này chỉ có thể được gọi sau khi nó được định nghĩa.

Cú pháp:

```js
const tenHam = function(thamSo) {
  // Khối lệnh
};
```

Ví dụ thực tế:

```javascript
const tinhHieu = function(a, b) {
  return a - b;
};
console.log(tinhHieu(5, 3)); // 2
```

_**Lưu ý**: Nếu gọi hàm trước khi định nghĩa sẽ xảy ra lỗi: `Uncaught ReferenceError: Cannot access 'tinhHieu' before initialization`._

#### Hàm mũi tên là gì?

Hàm mũi tên (Arrow function) là một cú pháp ngắn gọn được giới thiệu trong ES6, dùng để viết hàm biểu thức một cách ngắn gọn hơn. Hàm mũi tên đặc biệt hữu ích khi làm việc với các hàm vô danh và hàm callback.

Cú pháp:

```js
const tenHam = (thamSo) => {
  // Khối lệnh
};
```

Ví dụ thực tế:

```javascript
const tinhTich = (a, b) => {
  return a * b;
};

console.log(tinhTich(5, 3)); // 15
```

Hoặc `return` luôn sau dấu mũi tên:

```javascript
const tinhTich = (a, b) => a * b;

console.log(tinhTich(5, 3)); // 15
```

Hoặc rút gọn không cần cặp ngoặc đơn:

```javascript
const double = n => n * 2;

console.log(double(2)); // 4
```

_**Lưu ý**: Nếu gọi hàm trước khi định nghĩa sẽ xảy ra lỗi: `Uncaught ReferenceError: Cannot access 'double' before initialization`._

***

### Khi nào thì sử dụng loại hàm nào?

* **Hàm khai báo (Declaration function)**: Khi cần sử dụng được hàm trước khi khai báo, hoặc đơn giản muốn dùng cách truyền thống.
* **Hàm biểu thức (Function expression)**: Khi muốn chỉ gọi được hàm sau khi khai báo, hoặc khi hàm được sử dụng như một giá trị (ví dụ, truyền hàm như một tham số).
* **Hàm mũi tên (Arrow function)**: Khi cần một cú pháp ngắn gọn hoặc khi làm việc với this trong một ngữ cảnh nhất định (vì hàm mũi tên không có this riêng của nó).

{% hint style="info" %}
Tóm tắt

* **Hàm khai báo**: Hàm khai báo cho phép định nghĩa hàm trước hoặc sau khi nó được gọi, là cách truyền thống để tạo hàm.
  *   **Ví dụ**:

      ```js
      function tinhTong(a, b) {
        return a + b;
      }
      console.log(tinhTong(5, 3)); // 8
      ```
* **Hàm biểu thức**: Định nghĩa hàm thông qua việc gán hàm cho một biến, chỉ có thể được gọi sau khi được định nghĩa.
  *   **Ví dụ**:

      ```js
      const tinhHieu = function(a, b) {
        return a - b;
      };
      console.log(tinhHieu(5, 3)); // 2
      ```
* **Hàm mũi tên**: Cú pháp ngắn gọn của hàm biểu thức được giới thiệu trong ES6.
  *   **Ví dụ**:

      ```js
      const tinhTich = (a, b) => {
        return a * b;
      };
      console.log(tinhTich(5, 3)); // 15
      ```

      Hoặc:

      ```js
      const tinhTich = (a, b) => a * b;
      console.log(tinhTich(5, 3)); // 15
      ```
* **Khi nào sử dụng?**: Dùng hàm khai báo khi muốn gọi được hàm trước khi khai báo; dùng hàm biểu thức khi cần chỉ gọi được hàm sau khi khai báo hoặc sử dụng hàm như giá trị (gán vào biến, truyền làm tham số của hàm khác, v.v.); Dùng hàm mũi tên khi muốn có cú pháp ngắn gọn.
{% endhint %}
