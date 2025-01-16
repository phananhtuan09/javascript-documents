# Tìm hiểu thuộc tính và phương thức

Mục lục

* [Tìm hiểu về thuộc tính & phương thức](tim-hieu-thuoc-tinh-va-phuong-thuc.md#tim-hieu-ve-thuoc-tinh-and-phuong-thuc)
  * [Thuộc tính (Properties)](tim-hieu-thuoc-tinh-va-phuong-thuc.md#thuoc-tinh-properties)
  * [Phương thức (Methods)](tim-hieu-thuoc-tinh-va-phuong-thuc.md#phuong-thuc-methods)
* [Cách đặt tên thuộc tính & phương thức](tim-hieu-thuoc-tinh-va-phuong-thuc.md#cach-dat-ten-thuoc-tinh-and-phuong-thuc)
  * [Lưu ý chung](tim-hieu-thuoc-tinh-va-phuong-thuc.md#luu-y-chung)
  * [Đối với thuộc tính (Properties)](tim-hieu-thuoc-tinh-va-phuong-thuc.md#doi-voi-thuoc-tinh-properties)
  * [Đối với Phương thức (Methods)](tim-hieu-thuoc-tinh-va-phuong-thuc.md#doi-voi-phuong-thuc-methods)

### Tìm hiểu về thuộc tính & phương thức

Trong JavaScript, một object là một tập hợp các thuộc tính (properties) và phương thức (methods) mà bạn có thể sử dụng để lưu trữ và quản lý dữ liệu, cũng như thực hiện các hành động liên quan đến dữ liệu đó.

#### Thuộc tính (Properties)

Thuộc tính là các giá trị được lưu trữ trong object. Mỗi thuộc tính có một tên (key) và một giá trị (value) tương ứng. Giá trị của thuộc tính có thể là bất kỳ kiểu dữ liệu nào trong JavaScript, kể cả là một object khác.

Ví dụ: Object `dog` đơn giản với một số thuộc tính:

```javascript
const dog = {
  // Thuộc tính
  name: "Scooby Doo",
  age: 5,
};

// Truy cập thuộc tính
console.log(dog.name); // Scooby Doo
console.log(dog.age); // 5
```

Trong ví dụ trên, `name` và `age` là các thuộc tính của object `dog`, với các giá trị là `"Scooby Doo"` và `5` tương ứng.

#### Phương thức (Methods)

Phương thức là các hàm được định nghĩa bên trong object. Các phương thức này có thể thực thi các hành động trên dữ liệu được lưu trữ trong object hoặc thực hiện các chức năng khác liên quan đến object đó.

Ví dụ: Object `dog` được thêm phương thức `speak()`:

```javascript
const dog = {
  // Thuộc tính
  name: 'Scooby Doo',
  age: 5,

  // Phương thức
  speak: function() {
    console.log('Go go...');
  }
};

// Gọi phương thức
dog.speak(); // Go go...
```

Trong ví dụ trên, `speak` là một phương thức của object `dog`. Phương thức này khi được gọi sẽ in ra `"Go go..."`.

***

### Cách đặt tên thuộc tính & phương thức

#### Lưu ý chung

Cách đặt tên thuộc tính và phương thức cũng tương tự như cách đặt tên biến trong JavaScript:

* Sử dụng “Camel case” để đặt tên thuộc tính và phương thức trong object.
* Rõ ràng, cần mô tả được ý nghĩa và mục đích sử dụng.
* Tên thuộc tính có phân biệt HOA-thường, nên `name` và `Name` là hai thuộc tính khác nhau.
* Tránh đặt trùng với các từ khóa riêng của JavaScript.

#### Đối với thuộc tính (Properties)

* **Sử dụng danh từ**: Thuộc tính thường được đặt tên bằng danh từ hoặc cụm danh từ vì chúng thể hiện các đối tượng, đặc điểm, hoặc giá trị. Điều này phản ánh việc thuộc tính chứa dữ liệu hoặc thông tin cụ thể.
* **Ví dụ**:
  * `name`: Chứa tên.
  * `email`: Chứa địa chỉ email.
  * `age`: Chứa tuổi.
  * `isActive`: Biểu thị trạng thái hoạt động của một đối tượng (lưu ý rằng dù có chứa động từ, nhưng đây là một trường hợp ngoại lệ vì nó được sử dụng để thể hiện một thuộc tính có tính chất boolean).

#### Đối với Phương thức (Methods)

* **Sử dụng động từ**: Phương thức thường được đặt tên bắt đầu bằng động từ vì chúng biểu thị hành động, quy trình, hoặc tác vụ được thực hiện. Sử dụng động từ giúp làm rõ chức năng hoặc tác dụng của phương thức đó đối với dữ liệu hoặc đối tượng khác.
* **Ví dụ**:
  * `calculateTotal()`: Tính toán tổng số.
  * `getName()`: Trả về tên.
  * `isValid()`: Kiểm tra tính hợp lệ.
  * `updateProfile()`: Cập nhật hồ sơ người dùng.

Trong việc phát triển phần mềm, việc áp dụng đúng quy ước đặt tên là rất quan trọng không chỉ để làm cho mã nguồn của bạn trở nên “tự giải thích” mà còn giúp đảm bảo rằng các lập trình viên khác (hoặc chính bạn trong tương lai) có thể hiểu và bảo trì mã nguồn một cách dễ dàng. Việc sử dụng động từ và danh từ một cách phù hợp giúp làm nổi bật ý định lập trình và cải thiện tính rõ ràng của mã nguồn.

{% hint style="info" %}
* **Object trong JavaScript**: Object là một tập hợp các thuộc tính và phương thức dùng để lưu trữ và quản lý dữ liệu, cũng như thực hiện các hành động liên quan.
* **Thuộc tính (Properties)**: Là các giá trị được lưu trữ trong object. Mỗi thuộc tính có một tên và một giá trị, có thể là bất kỳ kiểu dữ liệu nào.
  * **Ví dụ về thuộc tính**: Object `dog` có thuộc tính `name` và `age`, truy cập bằng `dog.name` và `dog.age`.
* **Phương thức (Methods)**: Là các hàm được định nghĩa bên trong object, thực thi các hành động trên dữ liệu hoặc thực hiện chức năng liên quan.
  * **Ví dụ về phương thức**: Phương thức `speak` trong object `dog`, được gọi bằng `dog.speak()`.
* **Cách đặt tên thuộc tính và phương thức**: Tuân theo quy ước đặt tên giống như đặt tên biến, sử dụng “Camel case” và phải rõ ràng, mô tả được ý nghĩa.
  * **Thuộc tính**: Sử dụng danh từ hoặc cụm danh từ, ví dụ `name`, `age`, `isActive`.
  * **Phương thức**: Sử dụng động từ hoặc cụm từ bắt đầu bằng động từ, ví dụ `calculateTotal()`, `getName()`, `isValid()`, `updateProfile()`.
{% endhint %}
