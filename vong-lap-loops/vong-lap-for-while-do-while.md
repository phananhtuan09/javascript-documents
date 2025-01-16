# Vòng lặp For, While, Do-While

Mục lục

* [Vòng lặp (Loops)](vong-lap-for-while-do-while.md#vong-lap-loops)
  * [Vòng lặp là gì?](vong-lap-for-while-do-while.md#vong-lap-la-gi)
  * [Tại sao vòng lặp quan trọng?](vong-lap-for-while-do-while.md#tai-sao-vong-lap-quan-trong)
* [Các loại vòng lặp trong JavaScript](vong-lap-for-while-do-while.md#cac-loai-vong-lap-trong-javascript)
  * [Vòng lặp For](vong-lap-for-while-do-while.md#vong-lap-for)
  * [Vòng lặp While](vong-lap-for-while-do-while.md#vong-lap-while)
  * [Vòng lặp Do-While](vong-lap-for-while-do-while.md#vong-lap-do-while)
  * [So sánh và ứng dụng](vong-lap-for-while-do-while.md#so-sanh-va-ung-dung)
* [Sai lầm thường gặp](vong-lap-for-while-do-while.md#sai-lam-thuong-gap)
  * [Vòng lặp vô hạn dẫn tới treo chương trình](vong-lap-for-while-do-while.md#vong-lap-vo-han-dan-toi-treo-chuong-trinh)
  * [Sử dụng vòng lặp không phù hợp với bài toán](vong-lap-for-while-do-while.md#su-dung-vong-lap-khong-phu-hop-voi-bai-toan)
  * [Sai điều kiện dẫn tới nhận undefined khi duyệt mảng](vong-lap-for-while-do-while.md#sai-dieu-kien-dan-toi-nhan-undefined-khi-duyet-mang)
  * [Thực hiện công việc không cần thiết trong vòng lặp](vong-lap-for-while-do-while.md#thuc-hien-cong-viec-khong-can-thiet-trong-vong-lap)

### Vòng lặp (Loops)

#### Vòng lặp là gì?

Vòng lặp trong lập trình là một cấu trúc cho phép chúng ta thực thi một khối mã lặp đi lặp lại một số lần nhất định hoặc cho đến khi một điều kiện nhất định được thỏa mãn. Vòng lặp giúp chúng ta “viết lại” một hành động nhiều lần mà không cần phải “copy/paste” code.

#### Tại sao vòng lặp quan trọng?

**Ví dụ 1**: Bài toán in ra số từ 1-5.

**Cách chưa tốt**: In ra số bằng từng dòng code thủ công

```js
console.log(1);
console.log(2);
console.log(3);
console.log(4);
console.log(5);
```

**Cách tốt hơn**: Sử dụng vòng lặp `for` để tự động hóa quy trình

```js
for (let i = 1; i <= 5; i++) {
    console.log(i);
}
```

Cách này tốt hơn vì chúng ta chỉ cần viết một đoạn code ngắn gọn để thực hiện cùng một tác vụ, giúp tiết kiệm thời gian và công sức, đồng thời làm cho code dễ quản lý và bảo trì hơn.

**Ví dụ 2**: Bài toán in ra 1000 tên người dùng trong mảng.

**Cách chưa tốt**: Viết code thủ công in từng phần tử

```js
let userNames = ["User 1", "User 2", "User 3", ...]; // và 997 tên khác

console.log(userNames[0]);
console.log(userNames[1]);
console.log(userNames[2]);
// lặp lại 997 dòng console.log() nữa
```

**Cách tốt hơn**: Sử dụng vòng lặp `for` để tự động hóa quy trình

```js
let userNames = ["User 1", "User 2", "User 3", ...]; // và 997 tên khác

for (let i = 0; i < userNames.length; i++) {
  console.log(userNames[i]);
}
```

Tương tự như ví dụ 1, cách này tốt hơn vì code ngắn gọn, tiết kiệm công sức và giúp code dễ bảo trì hơn.

**Lợi ích của vòng lặp mang lại**:

* **Code ít hơn, dễ quản lý hơn**: Vòng lặp giúp giảm thiểu lượng code cần viết, làm cho chương trình ngắn gọn hơn và dễ quản lý hơn.
* **Tiết kiệm thời gian hơn**: Vòng lặp cho phép tự động hóa các tác vụ lặp đi lặp lại, từ đó tiết kiệm thời gian và công sức.
* **Tái sử dụng code**: Có thể sử dụng lại cùng một đoạn code cho các tác vụ lặp đi lặp lại.
* **Dễ dàng xử lý dữ liệu phức tạp**: Trong thực tế, vòng lặp thường được sử dụng để xử lý các tập dữ liệu, ví dụ như mảng hoặc danh sách các đối tượng.

***

### Các loại vòng lặp trong JavaScript

Trong JavaScript có nhiều loại vòng lặp khác nhau, mỗi loại sẽ có tình huống cụ thể phù hợp để sử dụng khác nhau. Nhưng mục đích chung của các loại vòng lặp đều để code ít hơn, tái sử dụng code, tự động hóa quy trình xử lý dữ liệu và giúp code dễ bảo trì hơn.

#### Vòng lặp For

Vòng lặp `for` thực hiện một khối lệnh dựa trên số lần xác định từ trước.

**Cú pháp**: Cấu trúc cơ bản của vòng lặp `For` bao gồm ba phần: khởi tạo, điều kiện lặp, và cập nhật. Mỗi phần được phân tách bằng dấu chấm phẩy (;).

```js
for (khởi_tạo; điều_kiện; cập_nhật) {
    // Khối code được lặp đi lặp lại
}
```

**Ví dụ**: In số từ 1 đến 100

```javascript
for (let i = 1; i <= 100; i++) {
    console.log(i);
}
```

**Giải thích**:

* `let i = 1`: Khởi tạo biến `i` bằng 1.
* `i <= 100`: Điều kiện lặp - vòng lặp sẽ tiếp tục miễn là `i` nhỏ hơn hoặc bằng 100.
* `i++`: Cập nhật sau mỗi lần lặp - tăng giá trị của `i` lên 1.

#### Vòng lặp While

Vòng lặp `while` thực hiện khối lệnh dựa trên một điều kiện và tiếp tục lặp cho đến khi điều kiện đó không còn đúng. Thích hợp cho các tình huống khi số lần lặp không biết trước.

**Cú pháp**:

```js
while (điều_kiện) {
    // Khối code được lặp đi lặp lại
}
```

**Ví dụ 1**: In số từ 1 đến 100

```javascript
let i = 1;

while (i <= 100) {
    console.log(i);
    i++;
}
```

**Giải thích**:

* `let i = 1`: Khởi tạo biến `i` là `1`.
* `while (i <= 100)`: Kiểm tra điều kiện lúc này là đúng, khối lệnh trong vòng lặp được thực thi - `console.log(i)` sẽ in ra giá trị của biến `i` hiện tại.
* `i++`: Cập nhật lại giá trị của biến `i`.

**Ví dụ 2**: Đợi cho tới khi người dùng nhập một giá trị số không âm.

```javascript
let input = -1;

while (input < 0) {
    input = +prompt("Nhập một số không âm:");
}

console.log(`Bạn đã nhập: ${input}`);
```

**Giải thích**:

* `input < 0`: Vì `input` được khởi tạo là `-1` nên điều kiện trong vòng lặp đúng, khối lệnh trong vòng lặp được chạy và hộp thoại _Prompt_ được bật lên.
* Sau khi người dùng nhập liệu, giá trị sẽ được chuyển đổi sang kiểu số bởi toán tử `+` và lưu vào `input`. Vòng lặp tiếp tục kiểm tra điều kiện, nếu `input` lúc này là số âm thì điều kiện lại đúng, _Prompt_ sẽ hiển thị lại cho tới khi người dùng nhập vào một số không âm.

**Ví dụ 3**: Tìm ước chung lớn nhất (cách 1).

```js
// Khởi tạo hai biến a và b với giá trị ban đầu
let a = 60;
let b = 48;

// Đảm bảo rằng a luôn lớn hơn b
if (b > a) {
    // Nếu b lớn hơn a, đổi chỗ a và b
    let temp = a; // Sử dụng biến tạm để giữ giá trị của a
    a = b;        // Gán giá trị của b cho a
    b = temp;     // Gán giá trị tạm (a ban đầu) cho b
}

// Thực hiện vòng lặp để tìm UCLN sử dụng thuật toán Euclid
while (b != 0) {
    let temp = b;  // Lưu giá trị hiện tại của b vào biến tạm
    b = a % b;     // Cập nhật b bằng phần dư của a chia cho b
    a = temp;      // Cập nhật a bằng giá trị cũ của b
    // Lặp lại quy trình này cho đến khi b bằng 0
}

// Khi b = 0, a chính là UCLN của hai số ban đầu
console.log(`Ước chung lớn nhất là ${a}`); // Ước chung lớn nhất là 12
```

Đoạn code trên tìm Ước chung lớn nhất (UCLN) của hai số `a` và `b` sử dụng thuật toán Euclid, dựa trên nguyên tắc rằng UCLN không thay đổi khi thay thế số lớn hơn bằng phần dư của nó khi chia cho số nhỏ hơn.

Cụ thể, cách thức hoạt động như sau:

1. **Đảm bảo a lớn hơn b**: Nếu `b` lớn hơn `a`, chúng ta hoán đổi giá trị của `a` và `b` để `a` luôn là số lớn hơn. Điều này làm cho việc áp dụng thuật toán Euclid trở nên đơn giản hơn.
2. **Áp dụng thuật toán Euclid**:
   * Trong vòng lặp `while`, điều kiện tiếp tục lặp là `b != 0`.
   * Trong mỗi lần lặp, chúng ta tính phần dư của `a` chia cho `b` (`a % b`) và gán giá trị này cho `b`.
   * Đồng thời, cập nhật giá trị của `a` thành giá trị cũ của `b` trước khi được cập nhật.
   * Quá trình này tiếp tục cho đến khi `b` bằng `0`.
3. **Kết luận**: Khi `b` bằng `0`, giá trị hiện tại của `a` là UCLN của hai số ban đầu. Lý do là qua mỗi lần lặp, thuật toán giảm kích thước của bài toán mà không làm thay đổi UCLN của `a` và `b`. Khi một trong hai số bằng `0`, số còn lại chính là UCLN.

Trong ví dụ này, ban đầu `a = 60` và `b = 48`. Qua các bước thực hiện, `a` và `b` được cập nhật liên tục cho đến khi `b = 0`. Lúc này, `a = 12`, chính là UCLN của 60 và 48.

**Ví dụ 4**: Tìm ước chung lớn nhất (cách 2).

```js
// Khởi tạo hai biến a và b với giá trị ban đầu
let a = 60;
let b = 48;

// Lặp lại cho đến khi a và b bằng nhau
while (a !== b) {
    // Nếu a lớn hơn b, giảm a đi b
    if (a > b) {
      a -= b; // a = a - b
    } else {
      // Ngược lại, nếu b lớn hơn a, giảm b đi a
      b -= a; // b = b - a
    }
    // Quá trình này lặp lại cho đến khi a và b bằng nhau,
    // Lúc này, a hoặc b chính là ước chung lớn nhất của hai số ban đầu.
}

// In ra ước chung lớn nhất
console.log(`Ước chung lớn nhất là ${a}`); // Ước chung lớn nhất là 12
```

Đoạn code trên tìm Ước chung lớn nhất (UCLN) của hai số `a` và `b` thông qua một phương pháp dựa trên việc giảm giá trị của số lớn hơn bằng cách trừ đi số nhỏ hơn, cho đến khi cả hai số bằng nhau.

Cụ thể, cách thức hoạt động như sau:

1. **Vòng lặp while**: Tiếp tục lặp cho đến khi giá trị của `a` và `b` bằng nhau. Đây là điều kiện dừng của vòng lặp.
2. **So sánh a và b**: Trong mỗi lần lặp, kiểm tra nếu `a` lớn hơn `b`, giảm `a` đi `b` (`a -= b`). Nếu không, tức là `b` lớn hơn hoặc bằng `a`, giảm `b` đi `a` (`b -= a`). Quá trình này giảm giá trị của số lớn hơn bằng cách trừ đi số nhỏ hơn, dần dần đưa chúng về một giá trị chung.
3. **Tìm UCLN**: Khi `a` và `b` bằng nhau, vòng lặp kết thúc, và giá trị đó chính là UCLN của hai số. Điều này dựa trên nguyên tắc rằng nếu trừ một số cho số khác, UCLN của hai số không thay đổi. Do đó, khi `a` và `b` bằng nhau, chúng ta đã tìm được UCLN.

Trong ví dụ này, bắt đầu với `a = 60` và `b = 48`. Qua các bước thực hiện:

* Lần 1: `a > b`, vậy `a = a - b = 60 - 48 = 12`.
* Lần 2 trở đi: `b` lớn hơn `a` mới (48 > 12), vậy `b` sẽ được giảm đi `a` cho đến khi `b` cũng bằng 12.

Khi cả `a` và `b` đều bằng 12, vòng lặp kết thúc, và `a` (hoặc `b`, vì chúng bằng nhau) chính là UCLN của hai số ban đầu, được in ra là `12`.

#### Vòng lặp Do-While

Vòng lặp `Do-While` là một cấu trúc lặp thực hiện hành động trước rồi mới kiểm tra điều kiện lặp sau. Điều này đảm bảo rằng thân vòng lặp sẽ được thực thi ít nhất một lần, ngay cả khi điều kiện ban đầu không được thỏa mãn.

Cú pháp:

```js
do {
    // Khối code được lặp đi lặp lại
} while (điều_kiện);
```

Ví dụ: Viết một hàm `promptForPassword` mô phỏng việc yêu cầu người dùng nhập mật khẩu. Người dùng cần nhập lại mật khẩu cho đến khi đúng với mật khẩu đã được định trước. Hãy giả định mật khẩu đúng là `"secret"`.

```javascript
let password = null;
do {
    password = prompt("Enter your password:");
} while (password !== "secret");
  
console.log("Password correct!");

```

**Giải thích**:

* Phần `prompt("Please enter your password:")` được thực thi ngay, hộp thoại được bật lên.
* Người dùng nhập nội dung và nhấn “OK” thì giá trị đó sẽ được lưu vào `password`.
* Vòng lặp kiểm tra điều kiện `password !== "secret"`, nếu `password` không phải `"secret"` thì vòng lặp sẽ tiếp tục lặp.
* Cho tới khi nhập đúng mật khẩu là `"secret"` thì vòng lặp mới bị thoát.

#### So sánh và ứng dụng

* **For và While**: `For` thường được sử dụng khi biết trước số lần lặp, trong khi `While` phù hợp hơn cho các tình huống số lần lặp không xác định.
* **While và Do-While**: Cả hai đều dựa vào một điều kiện, nhưng `Do-While` đảm bảo rằng khối lệnh được thực hiện ít nhất một lần, ngay cả khi điều kiện không đúng.

**Bảng so sánh**:

<table><thead><tr><th width="141">Tiêu chí</th><th>For</th><th>While</th><th>Do-While</th></tr></thead><tbody><tr><td><strong>Đặc điểm</strong></td><td>Số lần lặp xác định từ trước</td><td>Số lần lặp không xác định</td><td>Số lần lặp không xác định</td></tr><tr><td><strong>Sử dụng khi</strong></td><td>Biết trước số lần lặp</td><td>Không biết trước số lần lặp</td><td>Không biết trước số lần lặp, nhưng muốn đảm bảo thân vòng lặp được thực thi ít nhất một lần</td></tr><tr><td><strong>Cú pháp</strong></td><td>for (khởi_tạo; điều_kiện; cập_nhật) { // code }</td><td>while (điều_kiện) { // code }</td><td>do { // code } while (điều_kiện);</td></tr><tr><td><strong>Ví dụ</strong></td><td>Duyệt qua một mảng hoặc tạo vòng lặp với số lần lặp cụ thể</td><td>Xử lý một tác vụ cho đến khi điều kiện không còn đúng</td><td>Thực hiện một tác vụ ít nhất một lần, sau đó tiếp tục nếu điều kiện đúng</td></tr></tbody></table>

Sự lựa chọn giữa `While` và `For` thường dựa trên yếu tố cá nhân và tình huống cụ thể. `For` thường được ưa chuộng khi số lần lặp đã biết trước hoặc dễ xác định, còn `While` thì phù hợp với các tình huống mà điều kiện dừng phức tạp hơn hoặc không rõ ràng ngay từ đầu.

***

### Sai lầm thường gặp

#### Vòng lặp vô hạn dẫn tới treo chương trình

**Vấn đề**

Vòng lặp vô hạn xảy ra khi điều kiện lặp không bao giờ trở nên sai, thường là do quên cập nhật biến điều kiện hoặc viết sai điều kiện - khiến chương trình bị treo.

Ví dụ: Vòng lặp `For` vô hạn do sai điều kiện dừng

```js
for (let i = 0; i <= 10; i--) {
  // Xảy ra lặp vô hạn
}
```

Điểm sai ở đây là dùng `i--` dẫn tới điều kiện `i <= 10` luôn đúng, vòng lặp này sẽ chạy vô hạn dẫn tới treo chương trình.

Ví dụ: Vòng lặp `For` vô hạn do không cập nhật biến điều kiện.

```js
for (let i = 0; i <= 10;) {
  // Xảy ra lặp vô hạn
}
```

Ví dụ: Vòng lặp `For` vô hạn do để trống các thành phần

```js
for (;;) {
  // Xảy ra lặp vô hạn
}
```

Ví dụ: Vòng lặp `While` hoặc `Do-While` bị treo do quên cập nhật biến điều kiện, dẫn tới điều kiện thoát không rõ ràng.

```js
let i = 0;
while (i <= 10) {
  // Xảy ra lặp vô hạn
}
```

Trường hợp này biến `i` không được cập nhật nên giá trị luôn bằng `0`, dẫn tới điều kiện `i <= 10` luôn đúng và xảy ra lặp vô hạn. Tương tự, vòng lặp `Do-While` cũng có thể gặp phải vấn đề như vậy.

**Cách debug vòng lặp vô hạn**

Khi gặp phải vòng lặp vô hạn, việc đầu tiên là cần phải dừng chương trình. Sau đó, áp dụng các phương pháp sau để debug:

**1. Sử dụng console.log để in giá trị biến điều khiển vòng lặp**: Điều này giúp bạn theo dõi sự thay đổi của biến và xác định điều kiện thoát vòng lặp có được thực thi đúng hay không.

```js
let i = 0;

while (i <= 10) {
    console.log(i); // Theo dõi giá trị của i
    // Phát hiện: Quên không cập nhật giá trị của i
}
```

**2. Giới hạn số lần lặp trong quá trình debug**: Đặt một giới hạn cho số lần lặp để tránh treo chương trình. Ví dụ, bạn có thể thêm một biến đếm và dừng vòng lặp khi đạt đến giới hạn nhất định.

```js
let i = 0;
let count = 0; // Biến đếm để giới hạn vòng lặp

while (i <= 10 && count < 100) {
    console.log(i); // Theo dõi giá trị của i
    // Phát hiện: Quên không cập nhật giá trị của i
    count++; // Cập nhật biến đếm
}
```

**3. Sử dụng Breakpoints trong Chrome DevTools**: Đây là một phương pháp hữu ích để bắt đầu debug. Bạn có thể đặt một breakpoint trực tiếp trên dòng code mà bạn nghi ngờ gây ra vòng lặp vô hạn và theo dõi sự thay đổi của các biến qua từng lần lặp.

Để sử dụng công cụ debug của Chrome:

* Mở Developer Tools, chuyển đến tab “Sources”, tìm đến file JavaScript của bạn.
* Đặt breakpoint bằng cách nhấp vào số dòng bên cạnh dòng code.
* Chạy script của bạn. Chrome sẽ tự động dừng script tại breakpoint, cho phép bạn kiểm tra giá trị của các biến và thực hiện bước qua từng dòng code.

**Cách phòng tránh**

* Luôn cập nhật biến điều kiện trong vòng lặp và đảm bảo có một điều kiện thoát rõ ràng.
* Tắt tính năng tự động lưu (_Auto save_) của trình viết code, vì điều này có thể dẫn tới việc thực thi vòng lặp ngoài ý muốn. Ví dụ khi bạn chưa chắc điều kiện trong vòng lặp đã đúng thì code đã được thực thi có thể dẫn tới treo chương trình.

> _Nếu vô tình để xảy ra lặp vô hạn dẫn tới treo chương trình, với trình duyệt bạn chỉ cần tắt Tab bị treo, sửa lại code và mở lại trên trình duyệt._

#### Sử dụng vòng lặp không phù hợp với bài toán

**Vấn đề**

Sử dụng vòng lặp chưa phù hợp. Ví dụ dùng `While` hoặc `Do-While` cho vòng lặp xác định được số lần lặp, sử dụng `For` cho trường hợp không xác định được số lần lặp.

**Cách phòng tránh**

Dựa vào nhu cầu cụ thể của bài toán để chọn `For`, `While`, hay `Do-While`. Chọn loại vòng lặp phù hợp giúp cho code của bạn dễ đọc và bảo trì hơn.

#### Sai điều kiện dẫn tới nhận undefined khi duyệt mảng

**Vấn đề**: Sai điều kiện dẫn tới truy cập vượt quá phần tử cuối cùng của mảng.

Ví dụ: Trong bài toán in ra giá trị của mảng. Mảng có 3 phần tử nhưng vòng lặp lại chạy tới 4 lần, giá trị cuối cùng là `undefined`.

```javascript
let userNames = ["User 1", "User 2", "User 3"];

for (let i = 0; i <= userNames.length; i++) {
  console.log(userNames[i]);
}
// User 1
// User 2
// User 3
// undefined
```

Lý do cho kết quả trên là vì index của mảng tính từ `0`, với điều kiện `i <= userNames.length` thì lần lặp cuối cùng `i` sẽ là `3` (_trong khi mảng này index lớn nhất là 2_), nên giá trị của lần lặp cuối tương đương `userNames[3]` sẽ là `undefined`.

Ở đây, điều kiện dừng đúng đắn phải là `i < userNames.length`, không phải là `i <= userNames.length`.

**Cách phòng tránh**

Kiểm tra rõ ràng điều kiện lặp, đảm bảo có điều kiện dừng chính xác.

#### Thực hiện công việc không cần thiết trong vòng lặp

**Vấn đề**

Khi lập trình, việc thực hiện công việc không cần thiết trong vòng lặp không chỉ làm chậm chương trình mà còn làm cho code trở nên khó đọc và bảo trì.

**Ví dụ**: Bài toán nhân từng phần tử với phần tử đầu tiên trong mảng

**Cách chưa tốt**: Đọc giá trị không thay đổi trong vòng lặp

```javascript
let values = [1, 2, 3, 4, 5];

for (let i = 0; i < values.length; i++) {
    let firstValue = values[0]; // Đọc giá trị không đổi
    console.log(values[i] * firstValue);
}
// 1
// 2
// 3
// 4
// 5
```

**Cách tốt hơn**: Đọc một lần trước vòng lặp

```javascript
let values = [1, 2, 3, 4, 5];
let firstValue = values[0]; // Đọc một lần trước vòng lặp

for (let i = 0; i < values.length; i++) {
    console.log(values[i] * firstValue);
}
// 1
// 2
// 3
// 4
// 5
```

Qua ví dụ trên, có thể thấy rằng việc loại bỏ các công việc không cần thiết khỏi vòng lặp không chỉ giúp tăng hiệu suất chương trình mà còn làm cho code trở nên rõ ràng và dễ bảo trì hơn.

**Cách phòng tránh**

Đưa các logic không cần thiết phải đặt trong vòng lặp ra bên ngoài.

> _Việc giảm bớt các thao tác không cần thiết trong vòng lặp không chỉ giúp tăng tốc độ thực thi chương trình mà còn giảm bớt khả năng xảy ra lỗi do phức tạp hóa logic._

{% hint style="info" %}
Tóm tắt

* **Vòng lặp là gì**: Cấu trúc cho phép thực thi một khối mã lặp đi lặp lại, giúp giảm thiểu việc viết đi viết lại code.
* **Tại sao vòng lặp quan trọng**: Giúp tiết kiệm thời gian, công sức và làm cho code dễ quản lý, bảo trì hơn. Ví dụ: in ra 1000 tên người dùng mà không cần viết code thủ công.
* **Các loại vòng lặp trong JavaScript**:
  * **Vòng lặp For**: Phù hợp cho trường hợp biết trước số lần lặp.
  * **Vòng lặp While**: Thích hợp khi số lần lặp không xác định.
  * **Vòng lặp Do-While**: Đảm bảo thực thi khối lệnh ít nhất một lần, ngay cả khi điều kiện ban đầu không đúng.
* **Sai lầm thường gặp**:
  * **Vòng lặp vô hạn**: Xảy ra khi điều kiện lặp không bao giờ đúng, dẫn tới treo chương trình.
  * **Sử dụng vòng lặp không phù hợp**: Chọn loại vòng lặp chưa phù hợp cho bài toán cụ thể.
  * **Sai điều kiện dẫn tới nhận `undefined` khi duyệt mảng**: Ví dụ, dùng `<=` thay vì `<` khi kiểm tra điều kiện dừng của vòng lặp duyệt mảng.
  * **Thực hiện công việc không cần thiết trong vòng lặp**: Làm chậm chương trình và làm code khó bảo trì hơn.
{% endhint %}

