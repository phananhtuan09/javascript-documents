# Vòng lặp For-in và For-of

Mục lục

* [Vòng lặp for-in và for-of](vong-lap-for-in-va-for-of.md#vong-lap-for-in-va-for-of)
  * [Vòng lặp for-in](vong-lap-for-in-va-for-of.md#vong-lap-for-in)
  * [Vòng lặp for-of](vong-lap-for-in-va-for-of.md#vong-lap-for-of)
* [Một số ví dụ sử dụng for-in và for-of](vong-lap-for-in-va-for-of.md#mot-so-vi-du-su-dung-for-in-va-for-of)
* [Khác biệt giữa for-in, for-of và for?](vong-lap-for-in-va-for-of.md#khac-biet-giua-for-in-for-of-va-for)
  * [Sự khác biệt chính giữa for-in, for-of và for](vong-lap-for-in-va-for-of.md#su-khac-biet-chinh-giua-for-in-for-of-va-for)
  * [Tại sao nên sử dụng for-in và for-of hơn là for khi làm việc với array, object?](vong-lap-for-in-va-for-of.md#tai-sao-nen-su-dung-for-in-va-for-of-hon-la-for-khi-lam-viec-voi-array-object)
* [Sai lầm thường gặp](vong-lap-for-in-va-for-of.md#sai-lam-thuong-gap)
  * [Sử dụng for-in để duyệt mảng](vong-lap-for-in-va-for-of.md#su-dung-for-in-de-duyet-mang)
  * [Sử dụng for-of cho object](vong-lap-for-in-va-for-of.md#su-dung-for-of-cho-object)
  * [Quên sử dụng const hoặc let trong for-in và for-of](vong-lap-for-in-va-for-of.md#quen-su-dung-const-hoac-let-trong-for-in-va-for-of)

### Vòng lặp for-in và for-of

Vòng lặp `for-in` và `for-of` là hai cấu trúc lặp cung cấp trong JavaScript để duyệt qua các cấu trúc dữ liệu phức tạp như object và mảng, mỗi loại phục vụ một mục đích khác nhau.

#### Vòng lặp for-in

Vòng lặp `for-in` duyệt qua các thuộc tính của một object. Thích hợp khi bạn cần truy cập vào tất cả các keys (tên thuộc tính) của một object.

```javascript
const person = { name: "Nguyen Van A", age: 30 };

// Duyệt qua keys
for (const key in person) {
  console.log(key);
}

console.log('--------------');

// Duyệt qua keys và giá trị
for (const key in person) {
  console.log(`${key}: ${person[key]}`);
}
// name
// age
// --------------
// name: Nguyen Van A
// age: 30
```

#### Vòng lặp for-of

Vòng lặp `for-of` duyệt qua các giá trị của tất cả các phần tử trong một mảng và chuỗi. Là sự lựa chọn tốt khi bạn cần xử lý từng giá trị của một cấu trúc dữ liệu có thể duyệt được như mảng và chuỗi.

Ví dụ: Duyệt qua mảng

```javascript
const colors = ["red", "green", "blue"];

for (const color of colors) {
  console.log(color);
}
// red
// green
// blue
```

Ví dụ: Duyệt qua chuỗi

```javascript
const greeting = "Xin chào!";

for (const char of greeting) {
  console.log(char);
}
// X
// i
// n
// c
// h
// à
// o
// !
```

**Ưu điểm so với for**: Giảm thiểu cú pháp cần thiết để truy cập trực tiếp tới giá trị của từng phần tử mảng và chuỗi, làm cho code trở nên sáng sủa và dễ đọc hơn.

***

### Một số ví dụ sử dụng for-in và for-of

**Tình huống 1:**

Bạn đang phát triển một ứng dụng quản lý thông tin nhân viên. Bạn cần hiển thị thông tin chi tiết của từng nhân viên dưới dạng danh sách các thuộc tính và giá trị tương ứng.

```javascript
const employee = {
  name: "Nguyễn Văn B",
  age: 28,
  position: "Front-end Developer",
};

console.log("Thông tin nhân viên:");

for (const key in employee) {
  console.log(`${key}: ${employee[key]}`);
}
// Thông tin nhân viên:
// name: Nguyễn Văn B
// age: 28
// position: Front-end Developer
```

**Tình huống 2:**

Trong một ứng dụng quản lý sản phẩm, bạn cần kiểm tra xem một sản phẩm có đầy đủ các thuộc tính quan trọng như `id`, `name`, `price` trước khi đăng lên trang web.

Ví dụ:

```javascript
const product = {
  id: 1,
  name: "Điện thoại thông minh",
  price: 15000000,
};

const requiredProps = ["id", "name", "price"];

console.log("Kiểm tra thuộc tính sản phẩm:");

for (property of requiredProps) {
  if (property in product) {
    console.log(`Sản phẩm có ${property}.`);
  } else {
    console.log(`Sản phẩm thiếu ${property}.`);
  }
}
// Kiểm tra thuộc tính sản phẩm:
// Sản phẩm có id.
// Sản phẩm có name.
// Sản phẩm có price.
```

**Tình huống 3:**

Bạn đang xây dựng một ứng dụng bán hàng online. Mỗi loại sản phẩm sẽ được lưu trong một object với key là tên sản phẩm và value là số lượng. Bạn cần tính tổng số lượng sản phẩm có trong kho.

Ví dụ:

```javascript
const inventory = {
  aoThun: 25,
  quanJeans: 30,
  giayTheThao: 15,
};

let totalItems = 0;

for (const item in inventory) {
  totalItems += inventory[item];
}

console.log(`Tổng số sản phẩm: ${totalItems}`);
// Tổng số sản phẩm: 70
```

Trong mỗi tình huống trên, vòng lặp `for-in` được sử dụng để duyệt qua các keys của object, giúp xử lý dữ liệu một cách linh hoạt và hiệu quả. Việc áp dụng `for-in` trong các tình huống cụ thể như vậy giúp lập trình viên dễ dàng thao tác với dữ liệu dạng object trong JavaScript.

**Tình huống 4:**

Bạn đang làm việc trên một website thương mại điện tử và cần hiển thị danh sách các sản phẩm lên trang web. Mỗi sản phẩm là một object chứa thông tin như tên, giá, và mô tả.

Ví dụ:

```javascript
const products = [
  {
    name: "Điện thoại thông minh",
    price: 15000000,
    description: "Điện thoại mới nhất 2024"
  },
  {
    name: "Máy tính bảng",
    price: 12000000,
    description: "Thiết kế mỏng, nhẹ"
  },
  {
    name: "Laptop",
    price: 25000000,
    description: "Hiệu suất cao, cho dân thiết kế"
  },
];

console.log("Danh sách sản phẩm:");

for (const product of products) {
  console.log(`${product.name} - ${product.price} - ${product.description}`);
}
// Danh sách sản phẩm:
// Điện thoại thông minh - 15000000 - Điện thoại mới nhất 2024
// Máy tính bảng - 12000000 - Thiết kế mỏng, nhẹ
// Laptop - 25000000 - Hiệu suất cao, cho dân thiết kế
```

**Tình huống 5:**

Trong một ứng dụng quản lý thư viện, bạn cần tìm kiếm và hiển thị thông tin chi tiết của cuốn sách dựa trên tên sách được người dùng nhập vào.

```javascript
const books = [
  {
    title: "Sách lập trình JavaScript",
    author: "Nguyễn Văn A",
    year: 2023
  },
  {
    title: "Học thiết kế web",
    author: "Trần Thị B",
    year: 2022
  },
  {
    title: "Kỹ năng quản lý thời gian",
    author: "Lê Văn C",
    year: 2024
  },
];

const searchTitle = "Học thiết kế web";

for (const book of books) {
  if (book.title === searchTitle) {
    console.log(`Tìm thấy sách: ${book.title} - Tác giả: ${book.author} - Năm: ${book.year}`);
    break;
  }
}
// Tìm thấy sách: Học thiết kế web - Tác giả: Trần Thị B - Năm: 2022
```

**Tình huống 6:**

Bạn đang xây dựng một ứng dụng để quản lý điểm số của học sinh. Bạn cần tính toán điểm trung bình của mỗi học sinh từ một mảng điểm số.

Ví dụ:

```javascript
const scores = [8, 9, 7, 10, 9.5];
let totalScore = 0;

for (const score of scores) {
  totalScore += score;
}

const averageScore = totalScore / scores.length;

console.log(`Điểm trung bình: ${averageScore}`)
// Điểm trung bình: 8.7
```

Trong mỗi tình huống sử dụng vòng lặp `for-of`, chúng ta thấy được sự linh hoạt và tiện lợi khi làm việc với các object có thể duyệt được như mảng, chuỗi, và các cấu trúc dữ liệu khác. `for-of` giúp truy cập trực tiếp tới giá trị của từng phần tử, làm cho việc xử lý dữ liệu trở nên dễ dàng và trực quan hơn.

***

### Khác biệt giữa for-in, for-of và for?

Trong JavaScript, vòng lặp `for`, `for-in`, và `for-of` đều là các công cụ lặp qua các cấu trúc dữ liệu, nhưng chúng phù hợp sử dụng trong các trường hợp khác nhau với những đặc điểm riêng biệt.

#### Sự khác biệt chính giữa for-in, for-of và for

* **Mục đích sử dụng**: `for` phù hợp cho các trường hợp cần điều khiển chi tiết vòng lặp; `for-in` để duyệt qua các thuộc tính của object; `for-of` để duyệt qua các giá trị của cấu trúc dữ liệu có thể duyệt được như mảng và chuỗi.
* **Kiểu dữ liệu đích**: `for` và `for-of` thường được sử dụng với mảng và chuỗi; `for-in` được thiết kế để làm việc với object.
* **Cách sử dụng**: `for` cần khai báo biến đếm, điều kiện lặp, và biểu thức cập nhật; `for-in` và `for-of` đều dựa trên cú pháp giản lược hơn, tập trung vào các thuộc tính hoặc giá trị.

#### Tại sao nên sử dụng for-in và for-of hơn là for khi làm việc với array, object?

* **Dễ đọc và sự tiện lợi**: Cả `for-in` và `for-of` đều cung cấp một cách ngắn gọn và rõ ràng để duyệt qua các object và cấu trúc dữ liệu có thể duyệt được như mảng và chuỗi mà không cần quản lý chỉ số hoặc điều kiện dừng cụ thể như trong `for`.
* **Giảm thiểu lỗi**: Khi sử dụng `for`, bạn cần quản lý một biến đếm và điều kiện dừng, điều này có thể dẫn đến lỗi nếu không cẩn thận. `for-in` và `for-of` giảm thiểu rủi ro này bằng cách tự động duyệt qua các phần tử hoặc thuộc tính.

Tuy nhiên, điều quan trọng là lựa chọn loại vòng lặp phù hợp với mục đích cụ thể của bạn. Trong khi `for-in` và `for-of` mang lại nhiều lợi ích trong việc xử lý dữ liệu, vòng lặp `for` truyền thống vẫn có giá trị của nó, đặc biệt là khi bạn cần một vòng lặp với điều kiện lặp hoặc bước nhảy tùy chỉnh.

***

### Sai lầm thường gặp

Trong quá trình lập trình JavaScript, việc sử dụng không chính xác vòng lặp for-in và for-of có thể dẫn đến những lỗi không mong muốn và hiểu lầm về cách thức hoạt động của chúng.

#### Sử dụng for-in để duyệt mảng

**Sai lầm**: Dùng `for-in` để duyệt qua các phần tử của mảng có thể dẫn đến việc xử lý không chỉ các chỉ số mà còn cả các thuộc tính _kế thừa từ prototype (\*)_, gây ra kết quả không mong đợi.

Ví dụ:

```javascript
Array.prototype.thuocTinhMoRong = "Giá trị mở rộng";

const colors = ["Red", "Green", "Blue"];

for (const index in colors) {
  console.log(colors[index]);
}
// Red
// Green
// Blue
// Giá trị mở rộng
```

**Giải pháp**: Sử dụng vòng lặp `for-of` hoặc vòng lặp `for` truyền thống để duyệt mảng.

> _“Kế thừa từ prototype” các bạn sẽ được học trong chương chuyên biệt về Object._

#### Sử dụng for-of cho object

**Sai lầm**: Sử dụng `for-of` trực tiếp với object _không phải iterable (\*)_ sẽ gây ra lỗi.

Ví dụ:

```javascript
const person = {
  name: "Nguyen Van A",
  age: 30
};

// Uncaught TypeError: person is not iterable
for (const value of person) {
    console.log(value);
}
```

**Giải pháp**: Sử dụng `for-in` hoặc vòng lặp truyền thống để duyệt và truy cập object.

> _“Object không phải iterable” theo mặc định, tức là bạn không thể sử dụng vòng lặp `for-of` trực tiếp trên một object để duyệt qua các giá trị của nó như bạn có thể làm với các cấu trúc dữ liệu iterable khác như Array._

#### Quên sử dụng const hoặc let trong for-in và for-of

**Sai lầm**: Không sử dụng `const` hoặc `let` để khai báo biến trong vòng lặp `for-in` hoặc `for-of`, dẫn đến việc biến đó được khai báo toàn cục.

```javascript
const myArray = [1, 2, 3];

for (value of myArray) {
  console.log(value);
}

// value vẫn có thể truy cập được sau vòng lặp
console.log(value); // 3
```

**Giải pháp**: Luôn sử dụng `const` hoặc `let` để khai báo biến trong vòng lặp.

Nhận thức và tránh những sai lầm này sẽ giúp cải thiện chất lượng code và giảm thiểu lỗi trong quá trình phát triển với JavaScript.

{% hint style="info" %}
Tóm tắt

* **Vòng lặp for-in**: Dùng để duyệt qua các thuộc tính của object, thích hợp cho việc truy cập và xử lý các keys của object. Ví dụ, hiển thị thông tin chi tiết của nhân viên hoặc kiểm tra thuộc tính sản phẩm.
  * **Ưu điểm**: Cung cấp cách linh hoạt, đơn giản để truy cập các thuộc tính object mà không cần thiết lập điều kiện lặp rõ ràng.
* **Vòng lặp for-of**: Duyệt qua các giá trị của cấu trúc dữ liệu có thể duyệt được như mảng và chuỗi. Là lựa chọn tốt cho việc xử lý từng giá trị của mảng và chuỗi, ví dụ hiển thị danh sách sản phẩm hoặc tìm kiếm thông tin sách.
  * **Ưu điểm**: Giảm thiểu cú pháp cần thiết để truy cập giá trị của từng phần tử, làm code sáng sủa, dễ đọc hơn.
* **Khác biệt giữa for-in, for-of và for**: `for-in` dùng để duyệt qua thuộc tính của object, `for-of` dùng để duyệt qua giá trị của cấu trúc dữ liệu có thể duyệt được, trong khi `for` phù hợp cho trường hợp cần điều khiển chi tiết vòng lặp.
* **Sai lầm thường gặp**: Sử dụng `for-in` để duyệt mảng hoặc `for-of` cho object không phải _iterable_ gây ra lỗi không mong muốn. Quên sử dụng `const` hoặc `let` trong vòng lặp dẫn đến biến được khai báo toàn cục
{% endhint %}

