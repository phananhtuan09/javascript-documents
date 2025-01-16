# Cách viết "switch" bằng Object

Mục lục

* [Cách sử dụng lệnh switch truyền thống](cach-viet-switch-bang-object.md#cach-su-dung-lenh-switch-truyen-thong)
* [Cách sử dụng object mô phỏng “switch”](cach-viet-switch-bang-object.md#cach-su-dung-object-mo-phong-switch)
  * [Ví dụ sử dụng object thay thế cho switch case](cach-viet-switch-bang-object.md#vi-du-su-dung-object-thay-the-cho-switch-case)
  * [Ví dụ sử dụng hàm làm giá trị](cach-viet-switch-bang-object.md#vi-du-su-dung-ham-lam-gia-tri)

Sử dụng object thay thế cho cấu trúc điều khiển `switch` trong JavaScript có thể giúp code trở nên gọn gàng và dễ đọc hơn, đặc biệt khi bạn có một số lượng lớn các trường hợp cần xử lý. Phương pháp này thường được sử dụng trong các trường hợp cần ánh xạ trực tiếp từ một khóa đến một giá trị hoặc một hàm.

### Cách sử dụng lệnh switch truyền thống

Trước tiên, hãy xem xét một ví dụ sử dụng câu lệnh `switch` truyền thống trong JavaScript, thực hiện các hành động khác nhau dựa trên giá trị của biến. Sau đó, chúng ta có thể so sánh với ví dụ sử dụng đối tượng mà tôi đã cung cấp trước đó.

Ví dụ:

<pre class="language-javascript"><code class="lang-javascript">function calculate(operation, a, b) {
  switch (operation) {
    case 'add':
      return a + b;
    case 'subtract':
      return a - b;
    case 'multiply':
      return a * b;
    case 'divide':
      if (b === 0) {
        return 'Cannot divide by zero.';
      }
      return a / b;
    default:
      return 'Operation not recognized. Please use add, subtract, multiply, or divide.';
  }
}

// Testing the function
<strong>console.log(calculate('add', 5, 3)); //8
</strong>console.log(calculate('subtract', 5, 3)); //2
console.log(calculate('multiply', 5, 3)); //15
console.log(calculate('divide', 9, 3)); //3
console.log(calculate('divide', 5, 0)); //Cannot divide by zero.
console.log(calculate('modulus', 5, 3)); //Operation not recognized. Please use add, subtract, multiply, or divide.
</code></pre>

Giải thích:

* `switch` đánh giá biến `operation` để xác định phép toán cần thực hiện.
* Mỗi `case` thực hiện một phép toán cụ thể và in kết quả ra console.
* Trong trường hợp `divide`, có một kiểm tra bổ sung để đảm bảo rằng chúng ta không chia cho 0, vì điều này sẽ dẫn đến lỗi.
* Trường hợp `default` được sử dụng để xử lý bất kỳ đầu vào nào không phải là một trong bốn phép toán được định nghĩa, thông báo cho người dùng biết về việc nhập không hợp lệ.di

***

### Cách sử dụng object mô phỏng “switch”

#### Ví dụ sử dụng object thay thế cho switch case

Thay vì sử dụng `switch`, bạn tạo một object, trong đó mỗi khóa của object tương ứng với một trường hợp (`case`) của cấu trúc `switch`, và giá trị tương ứng là kết quả hoặc hàm bạn muốn thực thi.

Giả sử bạn có một hàm tính toán dựa trên `operation`. Thay vì sử dụng `switch`, bạn có thể sử dụng object như sau:

```javascript
function calculate(operation, a, b) {
  const operations = {
    add: a + b,
    subtract: a - b,
    multiply: a * b,
    divide: b === 0 ? 'Cannot divide by zero.' : a / b
  };

  // Tìm và thực hiện phép toán; nếu không tìm thấy, hiển thị thông báo lỗi
  return operations[operation] ?? 'Operation not recognized. Please use add, subtract, multiply, or divide.';
}

// Testing the function
console.log(calculate('add', 5, 3)); //8
console.log(calculate('subtract', 5, 3)); //2
console.log(calculate('multiply', 5, 3)); //15
console.log(calculate('divide', 9, 3)); //3
console.log(calculate('divide', 5, 0)); //Cannot divide by zero.
console.log(calculate('modulus', 5, 3)); //Operation not recognized. Please use add, subtract, multiply, or divide.
```

Hàm `calculate` được định nghĩa để thực hiện một số phép toán cơ bản (cộng, trừ, nhân, chia) dựa trên các đối số đầu vào. Cụ thể, hàm này nhận vào ba tham số: `operation` (kiểu string, xác định phép toán cần thực hiện), và `a`, `b` (các số học cần thực hiện phép toán). Dưới đây là chi tiết về cách hàm này hoạt động:

* Khởi tạo object `operations`: Object này chứa bốn cặp khóa-giá trị, mỗi khóa tương ứng với một tên phép toán (`add`, `subtract`, `multiply`, `divide`), và giá trị tương ứng là kết quả của phép toán đó. Đối với phép chia, có một điều kiện kiểm tra để tránh việc chia cho 0, nếu `b` bằng 0, kết quả sẽ là chuỗi “Cannot divide by zero.”.
* Tìm và thực hiện phép toán: Hàm sau đó sử dụng toán tử `??` để trả về kết quả của phép toán nếu `operation` tương ứng tồn tại trong object `operations`. Nếu không, nó sẽ trả về chuỗi “Operation not recognized. Please use add, subtract, multiply, or divide.”.

#### Ví dụ sử dụng hàm làm giá trị

Bạn cũng có thể ánh xạ các khóa với hàm để thực hiện các xử lý phức tạp hơn:

```javascript
function calculate(operation, a, b) {
  const operations = {
    add: () => a + b,
    subtract: () => a - b,
    multiply: () => a * b,
    divide: () => b === 0 ? 'Cannot divide by zero.' : a / b
  };

  // Tìm và thực hiện phép toán; nếu không tìm thấy, hiển thị thông báo lỗi
  const action = operations[operation];
  return action ? action() : 'Operation not recognized. Please use add, subtract, multiply, or divide.';
}

// Testing the function
console.log(calculate('add', 5, 3)); //8
console.log(calculate('subtract', 5, 3)); //2
console.log(calculate('multiply', 5, 3)); //15
console.log(calculate('divide', 9, 3)); //3
console.log(calculate('divide', 5, 0)); //Cannot divide by zero.
console.log(calculate('modulus', 5, 3)); //Operation not recognized. Please use add, subtract, multiply, or divide.
```

Có những cách để viết hàm calculate ngắn hơn nhưng khó hiểu hơn như:

```javascript
function calculate(operation, a, b) {
  const operations = {
    add: () => a + b,
    subtract: () => a - b,
    multiply: () => a * b,
    divide: () => (b ? a / b : "Cannot divide by zero."),
  }[operation];
  return (
    operations?.() ??
    "Invalid operation. Use add, subtract, multiply, or divide."
  );
}
```

```javascript
function calculate(operation, a, b) {
  const operations = {
    add: () => a + b,
    subtract: () => a - b,
    multiply: () => a * b,
    divide: () => (b ? a / b : "Cannot divide by zero."),
  };
  return (
    operations[operation] ??
    (() =>
      "Operation not recognized. Please use add, subtract, multiply, or divide.")
  )();
}
```

Trong ví dụ này, mỗi giá trị của object `operations` là một hàm, và bạn gọi hàm này bằng cách thêm `()` sau khi truy cập giá trị từ object.

Phương pháp sử dụng object thay thế cho `switch` giúp tăng tính linh hoạt và khả năng tái sử dụng code.

{% hint style="info" %}
Tóm tắt

* **Cấu trúc điều khiển Switch**: Dùng để xử lý nhiều trường hợp phân nhánh dựa trên giá trị của một biến. Câu lệnh `switch` kiểm tra biến và thực hiện các hành động tương ứng với từng trường hợp (`case`) cụ thể.
* **Sử dụng Object để mô phỏng Switch**: Thay thế cấu trúc `switch` bằng việc sử dụng object, trong đó các khóa của object tương ứng với các trường hợp khác nhau của `switch` và giá trị là các hàm hoặc kết quả cần thực hiện.
  * **Tính linh hoạt và yái sử dụng code**: Cách tiếp cận này giúp code trở nên linh hoạt hơn, dễ đọc và tái sử dụng, đặc biệt hiệu quả khi có nhiều trường hợp cần xử lý.
  * **Ưu điểm của phương pháp sử dụng Object**: Tăng khả năng mở rộng và bảo trì code dễ dàng hơn. Giảm thiểu rủi ro lỗi và tăng tốc độ thực thi so với sử dụng nhiều câu lệnh `switch` lồng nhau.
  * **Không sử dụng được “fallthrough” với Object**: Khi muốn sử dụng [_fallthrough_](https://javascript.fullstack.edu.vn/?id=a3e12c88-049d-4b30-a6a7-7c5c65ac9581\&t=880), hãy sử dụng cú pháp `switch...case` truyền thống.
{% endhint %}
