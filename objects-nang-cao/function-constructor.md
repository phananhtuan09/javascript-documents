# Function constructor

Mục lục

* [Hàm tạo và Instance là gì?](function-constructor.md#ham-tao-va-instance-la-gi)
  * [Hàm tạo là gì?](function-constructor.md#ham-tao-la-gi)
  * [Instance là gì?](function-constructor.md#instance-la-gi)
* [Tại sao cần sử dụng các hàm tạo](function-constructor.md#tai-sao-can-su-dung-cac-ham-tao)
  * [Ưu điểm khi dùng:](function-constructor.md#uu-diem-khi-dung)
  * [Bài toán và ví dụ:](function-constructor.md#bai-toan-va-vi-du)
* [Quy ước đặt tên hàm tạo](function-constructor.md#quy-uoc-dat-ten-ham-tao)
* [Các sai lầm thường gặp](function-constructor.md#cac-sai-lam-thuong-gap)
  * [Quên từ khóa new](function-constructor.md#quen-tu-khoa-new)
  * [Sử dụng hàm tạo cho việc không cần thiết](function-constructor.md#su-dung-ham-tao-cho-viec-khong-can-thiet)
  * [Sử dụng camelCase thay vì PascalCase](function-constructor.md#su-dung-camelcase-thay-vi-pascalcase)
  * [Sử dụng động từ đặt tên hàm tạo](function-constructor.md#su-dung-dong-tu-dat-ten-ham-tao)
  * [Sử dụng danh từ số nhiều đặt tên hàm tạo](function-constructor.md#su-dung-danh-tu-so-nhieu-dat-ten-ham-tao)

### Hàm tạo và Instance là gì?

#### Hàm tạo là gì?

Hàm tạo (_function constructor_) là một hàm đặc biệt được sử dụng để tạo và khởi tạo các đối tượng. Hàm tạo giống như một khuôn mẫu cho các đối tượng, nơi bạn có thể định nghĩa thuộc tính và phương thức ban đầu cho đối tượng mới được tạo ra. Khi bạn tạo một đối tượng mới từ hàm tạo, bạn sử dụng từ khóa `new` để gọi hàm tạo đó.

Cú pháp của một hàm tạo đơn giản như sau:

```js
function ĐốiTượng(tênThamSố1, tênThamSố2) {
  this.tênThuộcTính1 = tênThamSố1;
  this.tênThuộcTính2 = tênThamSố2;
  this.phươngThức = function() {
    // code thực hiện một số hành động
  };
}
```

Ví dụ:

```javascript
function Person(name, age) {
  this.name = name;
  this.age = age;
}

const person = new Person("John", 30);
console.log(person); // Person {name: "John", age: 30}

```

Ví dụ trên tạo ra một hàm tạo `Person`, sau đó sử dụng `new` để tạo một _instance_ mới của `Person`.

#### Instance là gì?

Một instance là một đối tượng cụ thể được tạo từ một hàm tạo. Instance kế thừa tất cả các thuộc tính và phương thức từ hàm tạo mà nó được tạo ra, nhưng giá trị của các thuộc tính có thể khác nhau giữa các instance.

Ví dụ:

```javascript
function Car(make, model) {
  this.make = make;
  this.model = model;
}

const myCar = new Car("Toyota", "Corolla");
console.log(myCar)' // Car {make: "Toyota", model: "Corolla"}
```

Trong ví dụ trên, `myCar` là một _instance_ của hàm tạo `Car`.

Hàm tạo cho phép bạn tạo nhiều đối tượng có cùng cấu trúc thuộc tính và phương thức mà không cần định nghĩa lại chúng mỗi lần.

***

### Tại sao cần sử dụng các hàm tạo

Các hàm tạo cho phép chúng ta tạo nhiều đối tượng có cùng khuôn mẫu mà không cần định nghĩa lại các thuộc tính và phương thức cho mỗi đối tượng.

#### Ưu điểm khi dùng:

* Tái sử dụng code, giảm trùng lặp code.
* Tạo đối tượng theo một khuôn mẫu nhất quán.

#### Bài toán và ví dụ:

* **Quản lý nhân vật**: Tạo các đối tượng Tom & Jerry với thuộc tính và phương thức giống nhau (_ví dụ đã đưa ra trong video bài học_).
* **Quản lý nhân viên**: Dễ dàng tạo và quản lý thông tin của nhiều nhân viên trong một công ty.
* **Quản lý sản phẩm**: Tạo các đối tượng sản phẩm với thông tin và phương thức quản lý giống nhau.

***

### Quy ước đặt tên hàm tạo

Trong JavaScript, khi đặt tên cho hàm tạo, quy ước thông thường là sử dụng _Pascal Case_, tức là viết hoa chữ cái đầu tiên của mỗi từ. Đối với hàm tạo gồm hai từ trở lên, mỗi từ sẽ bắt đầu bằng chữ hoa. Và quan trọng, tên của hàm tạo thường là danh từ số ít vì mỗi hàm tạo đều được thiết kế để tạo ra một _instance_ duy nhất của một loại đối tượng cụ thể tại một thời điểm.

Ví dụ, một hàm tạo cho một đối tượng Person sẽ được đặt tên là `Person`, chứ không phải là `person` hay `PERSON`.

Ví dụ:

```js
// Hàm tạo cho đối tượng Person
function Person(name, age) {
  this.name = name;
  this.age = age;
}

// Ví dụ tên hàm tạo có 2 từ trở lên
function StudentRecord(name, grade) {
  this.name = name;
  this.grade = grade;
}
```

Việc sử dụng danh từ số ít trong tên hàm tạo nhấn mạnh rằng mỗi lần bạn gọi hàm tạo, bạn đang tạo ra một “instance” duy nhất của loại đối tượng đó. Dù có thể tạo ra nhiều instance từ một hàm tạo, nhưng mỗi lần tạo ra chỉ là một đối tượng duy nhất, vì vậy danh từ số ít giúp phản ánh rõ ràng mục đích và cách sử dụng của hàm tạo.

***

### Các sai lầm thường gặp

#### Quên từ khóa new

Khi quên sử dụng từ khóa `new`, `this` trong hàm tạo sẽ không trỏ đến đối tượng mới mà trỏ tới đối tượng `global` (trong trường hợp của browser là `window`), gây ra lỗi.

> _Việc `this` trỏ tới `window` các bạn sẽ được học thêm ở bài “Từ khóa this nâng cao” tại chương sau_.

**Cách giải quyết:** Luôn nhớ sử dụng `new` khi tạo đối tượng từ hàm tạo.

#### Sử dụng hàm tạo cho việc không cần thiết

Sử dụng hàm tạo khi một hàm bình thường có thể đáp ứng được nhu cầu, gây ra sự phức tạp không cần thiết.

**Cách giải quyết:** Xác định rõ ràng nhu cầu trước khi quyết định sử dụng hàm tạo. Trong một số trường hợp, một hàm bình thường hoặc _object literal_ có thể đủ.

#### Sử dụng camelCase thay vì PascalCase

Một sai lầm phổ biến là viết tên hàm tạo bằng camelCase, tức là chỉ viết hoa chữ cái đầu tiên của từ thứ hai trở đi, và viết thường chữ cái đầu của từ đầu tiên. Điều này làm cho hàm tạo trông giống như một hàm bình thường và có thể gây nhầm lẫn.

Ví dụ sai:

```js
function carModel(brand, model) { // Sai: nên là CarModel
  this.brand = brand;
  this.model = model;
}
```

Trong ví dụ sai trên, `carModel` được viết theo _camelCase_, điều này không phù hợp với quy ước đặt tên cho hàm tạo trong JavaScript. Điều này có thể gây khó hiểu cho người đọc code.

#### Sử dụng động từ đặt tên hàm tạo

Đặt tên hàm tạo bắt đầu bằng một động từ (ví dụ: `CreateUser`) là không phù hợp vì hàm tạo nên tập trung vào việc “là gì” hơn là “làm gì”.

#### Sử dụng danh từ số nhiều đặt tên hàm tạo

Đặt tên hàm tạo bằng danh từ số nhiều, ví dụ như `Users`, gây hiểu nhầm rằng hàm tạo sẽ tạo ra nhiều thực thể cùng lúc, trong khi thực tế mỗi lần chỉ tạo ra một đối tượng.

{% hint style="info" %}
Tóm tắt

* **Hàm tạo và Instance**:
  * **Hàm tạo**: Là một hàm đặc biệt trong JavaScript để khởi tạo các đối tượng. Sử dụng từ khóa `new` kèm theo để tạo ra một instance mới. Hàm tạo như một khuôn mẫu, định nghĩa thuộc tính và phương thức cho đối tượng.
  * **Instance**: Là một thể hiện cụ thể của đối tượng được tạo từ hàm tạo. Mỗi instance kế thừa thuộc tính và phương thức từ hàm tạo nhưng giá trị của thuộc tính có thể khác nhau.
* **Tại sao sử dụng hàm tạo**:
  * Giúp tái sử dụng code và giảm trùng lặp.
  * Tạo đối tượng theo khuôn mẫu nhất quán, dễ dàng quản lý và mở rộng.
* **Quy ước đặt tên hàm tạo**:
  * Sử dụng Pascal Case (viết hoa chữ cái đầu tiên của mỗi từ).
  * Tên hàm tạo thường là danh từ số ít để phản ánh việc tạo ra một instance duy nhất mỗi lần.
* **Sai lầm thường gặp**:
  * Quên từ khóa `new` khi tạo instance.
  * Sử dụng hàm tạo cho việc không cần thiết.
  * Đặt tên hàm tạo theo camelCase thay vì PascalCase.
  * Sử dụng động từ hoặc danh từ số nhiều để đặt tên hàm tạo.
{% endhint %}
