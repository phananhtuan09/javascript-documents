# Toán tử Logical cơ bản

Mục lục

* [Toán tử Logical](toan-tu-logical-co-ban.md#toan-tu-logical)
  * [Toán tử AND (&&)](toan-tu-logical-co-ban.md#toan-tu-and-and-and)
  * [Toán tử OR (||)](toan-tu-logical-co-ban.md#toan-tu-or-or-or)
  * [Toán tử NOT (!)](toan-tu-logical-co-ban.md#toan-tu-not)
* [Kết hợp nhiều toán tử Logical](toan-tu-logical-co-ban.md#ket-hop-nhieu-toan-tu-logical)
  * [Kết hợp toán tử AND (&&)](toan-tu-logical-co-ban.md#ket-hop-toan-tu-and-and-and)
  * [Kết hợp toán tử OR (||)](toan-tu-logical-co-ban.md#ket-hop-toan-tu-or-or-or)
  * [Kết hợp toán tử AND và OR](toan-tu-logical-co-ban.md#ket-hop-toan-tu-and-va-or)
* [Lỗi thường gặp](toan-tu-logical-co-ban.md#loi-thuong-gap)
  * [Không nắm được độ ưu tiên giữa các toán tử](toan-tu-logical-co-ban.md#khong-nam-duoc-do-uu-tien-giua-cac-toan-tu)
  * [Dùng nhầm toán tử & hoặc | thay vì && và ||](toan-tu-logical-co-ban.md#dung-nham-toan-tu-and-hoac-or-thay-vi-and-and-va-or-or)

### Toán tử Logical

Toán tử logical trong lập trình JavaScript là các ký hiệu đặc biệt dùng để kết hợp các điều kiện logic. Chúng giúp xác định tính đúng hoặc sai của một hoặc nhiều điều kiện.

#### Toán tử AND (&&)

Trả về `true` nếu cả hai các biểu thức là `true`. Ví dụ: `expr1 && expr2` trả về `true` nếu cả `expr1` và `expr2` đều `true`.

Sử dụng trong các tình huống cần tất cả các điều kiện phải đúng.

Ví dụ: Nếu _nhiệt độ > 20 độ C_ **và** _hôm nay là ngày nghỉ_ thì sẽ đi picnic.

```js
let temperature = 25; // Nhiệt độ 25 độ C
let dayOff = "Sunday"; // Ngày nghỉ là Chủ nhật
let today = "Sunday"; // Ngày hôm nay

if (temperature > 20 && today === dayOff) {
  console.log("Đi picnic!");
} else {
  console.log("Ở nhà!");
}
// Kết quả: Đi picnic!
```

Cách viết khác:

```js
let temperature = 25; // Nhiệt độ 25 độ C
let dayOff = "Sunday"; // Ngày nghỉ là Chủ nhật
let today = "Sunday"; // Ngày hôm nay

// Tách thành biến giúp code có ý nghĩa hơn
let isWeatherGood = temperature > 20;
let hasFreeTime = today === dayOff;

if (isWeatherGood && hasFreeTime) {
  console.log("Đi picnic!");
} else {
  console.log("Ở nhà!");
}
// Kết quả: Đi picnic!
```

#### Toán tử OR (||)

Trả về `true` nếu ít nhất một trong các biểu thức là `true`. Ví dụ: `expr1 || expr2` trả về `true` nếu `expr1` hoặc `expr2` là `true`.

Thường dùng khi chỉ cần một trong các điều kiện đúng.

Ví dụ:

```js
let isComedyAvailable = true; // Có phim hài
let isActionAvailable = false; // Không có phim hành động

if (isComedyAvailable || isActionAvailable) {
  console.log("Xem phim vui vẻ!");
} else {
  console.log("Chọn hoạt động khác!");
}
// Kết quả: Xem phim vui vẻ!
```

#### Toán tử NOT (!)

Toán tử `!` được sử dụng để phủ định một điều kiện, biến `true` thành `false` và ngược lại.

Ví dụ: `!expr` trả về `false` nếu `expr` là `true`.

Dùng để đảo ngược giá trị logic của một biểu thức.

Ví dụ: Nếu không thích mèo, thì in ra “Không thích mèo!”.

```js
let isCatLover = false;

if (!isCatLover) {
  console.log("Không thích mèo!");
}
// Kết quả: Không thích mèo!
```

***

### Kết hợp nhiều toán tử Logical

#### Kết hợp toán tử AND (&&)

**Tình huống**: Kiểm tra xem một người có đủ điều kiện tham gia một khóa học lập trình không. Điều kiện bao gồm: đủ tuổi (trên 16 tuổi), có kiến thức cơ bản về máy tính, và đã đăng ký trước.

Ví dụ:

```js
let age = 17;
let hasBasicComputerSkills = true;
let isRegistered = true;

if (age > 16 && hasBasicComputerSkills && isRegistered) {
  console.log("Đủ điều kiện tham gia khóa học");
} else {
  console.log("Không đủ điều kiện");
}
// Kết quả: Đủ điều kiện tham gia khóa học
```

#### Kết hợp toán tử OR (||)

**Tình huống**: Một ứng dụng streaming phim cho phép truy cập nếu người dùng là thành viên VIP, có mã quà tặng, hoặc đã thanh toán phí đăng ký.

Ví dụ:

```js
let isVipMember = false;
let hasGiftCode = true;
let hasPaidSubscription = false;

if (isVipMember || hasGiftCode || hasPaidSubscription) {
  console.log("Truy cập nội dung VIP");
} else {
  console.log("Không thể truy cập nội dung VIP");
}
// Kết quả: Truy cập nội dung VIP
```

#### Kết hợp toán tử AND và OR

**Tình huống**: Một người dùng sẽ đủ điều kiện nhận quà khi vừa đăng ký mới (điều kiện A) HOẶC là thành viên VIP (điều kiện B), và đã mua hàng trên 500.000đ (điều kiện C).

Ví dụ:

```js
let isNewUser = true;
let isVipMember = false;
let purchaseAmount = 600000;

if ((isNewUser || isVipMember) && purchaseAmount > 500000) {
  console.log("Đủ điều kiện nhận quà");
} else {
  console.log("Không đủ điều kiện");
}
// Kết quả: Đủ điều kiện nhận quà
```

Lưu ý:

* Không nên sử dụng ! trong điều kiện có cả if và esle&#x20;
* Thứ tự thực thi:
  * !
  * &&
  * ||

***

### Lỗi thường gặp

#### Không nắm được độ ưu tiên giữa các toán tử

Khi kết hợp toán tử AND (`&&`) và OR (`||`) có thể dẫn đến kết quả không mong muốn do thứ tự ưu tiên của các phép toán không được kiểm soát chính xác.

#### Dùng nhầm toán tử & hoặc | thay vì && và ||

Đây là một nhầm lẫn phổ biến đối với người mới học lập trình. Điều này có thể dẫn đến kết quả không mong muốn vì `&` và `|` hoạt động ở cấp độ bit.

{% hint style="info" %}
Tóm tắt

* **Toán tử Logical trong JavaScript**: Toán tử logical được sử dụng để kết hợp các điều kiện logic, quyết định tính đúng sai của các biểu thức.
  * **Toán tử AND (`&&`)**: Trả về `true` khi tất cả các biểu thức là `true`. Dùng trong tình huống cần mọi điều kiện đều đúng.
  * **Toán tử OR (`||`)**: Trả về `true` nếu ít nhất một biểu thức là `true`. Dùng khi chỉ cần một trong các điều kiện đúng.
  * **Toán tử NOT (`!`)**: Phủ định giá trị logic của biểu thức, biến `true` thành `false` và ngược lại.
* **Ví dụ thực tế**:
  * **Ví dụ với AND**: `if (temperature > 20 && today === dayOff) { console.log("Đi picnic!"); }` - Điều kiện cho việc đi picnic là nhiệt độ trên 20 độ và là ngày nghỉ.
  * **Ví dụ với OR**: `if (isComedyAvailable || isActionAvailable) { console.log("Xem phim vui vẻ!"); }` - Có thể xem phim nếu có phim hài hoặc phim hành động.
  * **Ví dụ với NOT**: `if (!isCatLover) { console.log("Không thích mèo!"); }` - In ra “Không thích mèo!” nếu không phải là người yêu mèo.
* **Kết hợp nhiều toán tử**:
  * **AND và OR cùng lúc**: `if ((isNewUser || isVipMember) && purchaseAmount > 500000) { console.log("Đủ điều kiện nhận quà"); }` - Đủ điều kiện nhận quà nếu là người dùng mới hoặc thành viên VIP và đã mua hàng trên 500.000đ.
  * **Chú ý về độ ưu tiên**: Sử dụng ngoặc đơn `()` để nhóm các biểu thức cần ưu tiên thực hiện trước.
* **Độ ưu tiên của toán tử Logical**:
  * Toán tử NOT (`!`) có độ ưu tiên cao hơn toán tử AND (`&&`). Toán tử AND (`&&`) có độ ưu tiên cao hơn so với OR (`||`).
  * Trong biểu thức kết hợp nhiều toán tử Logical, phần được xử lý trước sẽ tuân theo thứ tự ưu tiên này.
  * Để đảm bảo logic chính xác, sử dụng dấu ngoặc đơn `()` để xác định rõ ràng thứ tự thực hiện các biểu thức.
* **Lỗi thường gặp**:
  * **Nhầm lẫn về độ ưu tiên**: Cần chú ý đến thứ tự ưu tiên khi kết hợp nhiều toán tử.
  * **Dùng nhầm `&`/`|` thay cho `&&`/`||`**: `&` và `|` là toán tử bit-level, có hành vi khác `&&` và `||`, nó thường hiếm khi được sử dụng với lập trình ứng dụng như lập trình web.
{% endhint %}

