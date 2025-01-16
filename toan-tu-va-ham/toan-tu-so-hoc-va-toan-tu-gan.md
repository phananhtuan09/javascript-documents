# Toán tử số học và toán tử gán

Mục lục

* [Số nguyên và số thực](toan-tu-so-hoc-va-toan-tu-gan.md#so-nguyen-va-so-thuc)
  * [Số nguyên (Integer)](toan-tu-so-hoc-va-toan-tu-gan.md#so-nguyen-integer)
  * [Số thực (Float)](toan-tu-so-hoc-va-toan-tu-gan.md#so-thuc-float)
* [Toán tử số học (Arithmetic Operators)](toan-tu-so-hoc-va-toan-tu-gan.md#toan-tu-so-hoc-arithmetic-operators)
  * [Toán tử cộng (+)](toan-tu-so-hoc-va-toan-tu-gan.md#toan-tu-cong)
  * [Toán tử trừ (-)](toan-tu-so-hoc-va-toan-tu-gan.md#toan-tu-tru)
  * [Toán tử nhân (\*)](toan-tu-so-hoc-va-toan-tu-gan.md#toan-tu-nhan)
  * [Toán tử chia (/)](toan-tu-so-hoc-va-toan-tu-gan.md#toan-tu-chia)
  * [Toán tử chia lấy dư (%)](toan-tu-so-hoc-va-toan-tu-gan.md#toan-tu-chia-lay-du)
  * [Toán tử tăng giá trị lên 1 (++)](toan-tu-so-hoc-va-toan-tu-gan.md#toan-tu-tang-gia-tri-len-1)
  * [Toán tử giảm giá trị đi 1 (--)](toan-tu-so-hoc-va-toan-tu-gan.md#toan-tu-giam-gia-tri-di-1)
  * [Toán tử lũy thừa (\*\*)](toan-tu-so-hoc-va-toan-tu-gan.md#toan-tu-luy-thua)
* [Toán tử gán (Assignment Operators)](toan-tu-so-hoc-va-toan-tu-gan.md#toan-tu-gan-assignment-operators)
  * [Toán tử gán](toan-tu-so-hoc-va-toan-tu-gan.md#toan-tu-gan)
  * [Toán tử gán kết hợp](toan-tu-so-hoc-va-toan-tu-gan.md#toan-tu-gan-ket-hop)
* [Lỗi thường gặp](toan-tu-so-hoc-va-toan-tu-gan.md#loi-thuong-gap)

### Số nguyên và số thực

#### Số nguyên (Integer)

Số nguyên là các số không có phần thập phân. Chúng bao gồm cả số dương, số âm và số không. Ví dụ về số nguyên bao gồm -3, 0, 7.

#### Số thực (Float)

Số thực bao gồm tất cả các số nguyên và các số có phần thập phân. Ví dụ về số thực bao gồm -3, 0, 7, 1.5, -3.2.

***

### Toán tử số học (Arithmetic Operators)

Toán tử số học để thực hiện các phép toán cơ bản trong lập trình. Ví dụ: cộng (`+`), trừ (`-`), nhân (`*`), chia (`/`).

| Toán tử | Ý nghĩa                 |
| ------- | ----------------------- |
| `+`     | Phép cộng               |
| `-`     | Phép trừ                |
| `*`     | Phép nhân               |
| `/`     | Phép chia               |
| `%`     | Phép chia lấy số dư     |
| `++`    | Tăng giá trị biến lên 1 |
| `--`    | Giảm giá trị biến đi 1  |
| `**`    | Phép lũy thừa           |

Phía dưới là các ví dụ cho thấy cách sử dụng của các toán tử số học này.

#### Toán tử cộng (`+`)

Dùng để cộng hai giá trị.

Ví dụ:

```js
let sumInt = 5 + 3; // sumInt = 8

let sumIntFlt = 7 + 3.5; // sumIntFlt = 10.5

let sumFlts = 2.3 + 4.7; // sumFlts = 7

let sumNegPos = -10 + 15; // sumNegPos = 5
```

#### Toán tử trừ (`-`)

Dùng để trừ giá trị này với giá trị kia.

Ví dụ:

```js
let diffInt = 10 - 4; // diffInt = 6

let diffIntFlt = 15 - 2.5; // diffIntFlt = 12.5

let diffFlts = 5.75 - 3.25; // diffFlts = 2.5

let diffPosNeg = 20 - -5; // diffPosNeg = 25

let diffFltInt = 7.5 - 3; // diffFltInt = 4.5
```

#### Toán tử nhân (`*`)

Dùng để nhân hai giá trị với nhau.

Ví dụ:

```js
let prodInt = 4 * 3; // prodInt = 12

let prodIntFlt = 7 * 2.5; // prodIntFlt = 17.5

let prodFlts = 3.5 * 2.2; // prodFlts = 7.7

let prodPosNeg = 5 * -3; // prodPosNeg = -15

let prodZero = 9 * 0; // prodZero = 0
```

#### Toán tử chia (`/`)

Dùng để chia một giá trị cho giá trị khác.

Ví dụ:

```js
let quotInt = 10 / 2; // quotInt = 5

let quotIntFlt = 9 / 1.5; // quotIntFlt = 6

let quotFlts = 7.5 / 2.5; // quotFlts = 3

let quotPosNeg = 20 / -4; // quotPosNeg = -5

let quotNegInt = -15 / 5; // quotNegInt = -3

let quotZero = 5 / 0; // quotZero = Infinity
```

> Lưu ý rằng trong JavaScript, khi chia cho số 0, kết quả sẽ là `Infinity` hoặc `-Infinity` tùy thuộc vào dấu của số bị chia, thay vì gây ra lỗi.

#### Toán tử chia lấy dư (`%`)

Toán tử này trả về phần dư của phép chia hai số. Nó rất hữu ích khi cần xác định số lẻ, số chẵn, hoặc khi cần lấy phần dư từ phép chia.

```js
let result1 = 10 % 3; // result1 = 1, vì 10 chia 3 dư 1
let result2 = 16 % 2; // result2 = 0, vì 16 chia 2 dư 0
let result3 = 8 % 16; // result3 = 8, vì 8 chia 16 dư 8
```

#### Toán tử tăng giá trị lên 1 (`++`)

Toán tử này tăng giá trị của biến lên `1`.

```js
let a = 5;
a++;
console.log(a); // 6
```

#### Toán tử giảm giá trị đi 1 (`--`)

Toán tử này giảm giá trị của biến đi `1`.

```js
let b = 5;
b--;
console.log(b); // 4
```

#### Toán tử lũy thừa (`**`)

Đây là toán tử lũy thừa, dùng để tính giá trị lũy thừa của một số.

```js
let c = 3 ** 2; // c = 9, tương đương với 3 mũ 2
```

Mỗi toán tử này đều có chức năng riêng biệt và được sử dụng trong nhiều tình huống khác nhau trong lập trình JavaScript, từ việc xử lý số học cơ bản đến việc thực hiện các phép tính toán phức tạp hơn.

***

### Toán tử gán (Assignment Operators)

Toán tử gán cho phép gán một giá trị cho một biến. Trong JavaScript các toán tử gán sau thường được sử dụng.

| Toán tử | Sử dụng   | Ý nghĩa      |
| ------- | --------- | ------------ |
| `=`     | `x = y`   | `x = y`      |
| `+=`    | `x += y`  | `x = x + y`  |
| `-=`    | `x -= y`  | `x = x - y`  |
| `*=`    | `x *= y`  | `x = x * y`  |
| `/=`    | `x /= y`  | `x = x / y`  |
| `%=`    | `x %= y`  | `x = x % y`  |
| `**=`   | `x **= y` | `x = x ** y` |

Có thể chia các toán tử gán này thành hai loại: toán tử gán thông thường (_chỉ thực hiện gán_) và toán tử gán kết hợp (_thực hiện phép toán rồi gán_).

#### Toán tử gán

Toán tử gán là nền tảng cơ bản trong JavaScript, cho phép bạn gán giá trị cho biến.

**Ví dụ:**

Tạo một biến và gán giá trị:

```js
let age = 25;
console.log(age); // 25
```

_`age` là biến, `25` là giá trị được gán._

**Lưu ý**: Toán tử gán luôn theo chiều từ phải sang trái.

#### Toán tử gán kết hợp

Trong JavaScript, các toán tử như `+=`, `-=`, `*=`, và `/=` được gọi là toán tử gán kết hợp. Chúng kết hợp một phép toán (như cộng, trừ, nhân, chia) với một phép gán.

**Toán tử `+=`**

Toán tử này cộng giá trị bên phải vào biến bên trái và sau đó gán kết quả trở lại biến bên trái.

```js
let a = 5;
a += 3; // Tương đương với a = a + 3; giờ a là 8
```

**Toán tử `-=`**

Toán tử này trừ giá trị bên phải từ biến bên trái và sau đó gán kết quả trở lại biến bên trái.

```js
let b = 10;
b -= 4; // Tương đương với b = b - 4; giờ b là 6
```

**Toán tử `*=`**

Toán tử này nhân biến bên trái với giá trị bên phải và sau đó gán kết quả trở lại biến bên trái.

```js
let c = 7;
c *= 3; // Tương đương với c = c * 3; giờ c là 21
```

**Toán tử `/=`**

Toán tử này chia biến bên trái cho giá trị bên phải và sau đó gán kết quả trở lại biến bên trái.

```js
let d = 20;
d /= 4; // Tương đương với d = d / 4; giờ d là 5
```

**Toán tử `%=`**

Toán tử này kết hợp phép chia lấy dư với phép gán. Nó chia giá trị của biến bên trái cho giá trị bên phải, sau đó gán phần dư của phép chia đó trở lại vào biến bên trái.

```js
let a = 10;
a %= 3; // Tương đương a = a % 3; giờ a là 1, vì 10 chia 3 dư 1
```

**Toán tử `**=`**

Toán tử này kết hợp phép tính lũy thừa với phép gán. Nó tính lũy thừa của biến bên trái với số mũ là giá trị bên phải, sau đó gán kết quả trở lại vào biến bên trái.

```js
let b = 3;
b **= 2; // Tương đương b = b ** 2; giờ b là 9, vì 3 mũ 2 là 9
```

***

### Lỗi thường gặp

* **Chia một số cho 0**: gây ra lỗi trong chương trình.
* **Quên ưu tiên phép tính**: ưu tiên phép nhân và chia trước, cộng và trừ sau.
* **Quên phép chia lấy số dư**: phép chia lấy dư sẽ trả về phần dư của phép chia sau khi lấy phần nguyên của kết quả.

{% hint style="info" %}
Tóm tắt

* **Số nguyên và số thực**
  * **Số nguyên**: Là các số không có phần thập phân, bao gồm số dương, số âm, và số 0.
  * **Số thực**: Bao gồm số nguyên và số có phần thập phân.
* **Toán tử số học**
  * **`+` (Cộng)**: Cộng hai giá trị.
  * **`-` (Trừ)**: Trừ một giá trị từ giá trị khác.
  * **`*` (Nhân)**: Nhân hai giá trị.
  * **`/` (Chia)**: Chia một giá trị cho giá trị khác.
  * **`%` (Chia lấy dư)**: Tính phần dư của phép chia.
  * **`++` (Tăng giá trị lên 1)**: Tăng giá trị của biến lên 1.
  * **`--` (Giảm giá trị đi 1)**: Giảm giá trị của biến đi 1.
  * **`**` (Lũy thừa)**: Tính lũy thừa của một số.
* **Toán tử gán**
  * **Toán tử gán (`=`)**: Gán giá trị cho biến.
  * **Toán tử gán kết hợp (`+=`, `-=`, `*=`, `/=`, `%=`, `**=`)**: Kết hợp phép toán với phép gán.
* **Lỗi thường gặp**
  * **Chia cho 0**: Kết quả là `Infinity` hoặc `-Infinity`.
  * **Quên ưu tiên phép tính**: Nhân/chia trước, cộng/trừ sau.
  * **Quên phép chia lấy số dư**: Trả về phần dư của phép chia.
{% endhint %}

