# Làm việc với mảng cơ bản

Mục lục

* [Thêm và xóa phần tử](lam-viec-voi-mang-co-ban.md#them-va-xoa-phan-tu)
  * [push()](lam-viec-voi-mang-co-ban.md#push)
  * [pop()](lam-viec-voi-mang-co-ban.md#pop)
  * [unshift()](lam-viec-voi-mang-co-ban.md#unshift)
  * [shift()](lam-viec-voi-mang-co-ban.md#shift)
* [Tìm kiếm và kiểm tra phần tử](lam-viec-voi-mang-co-ban.md#tim-kiem-va-kiem-tra-phan-tu)
  * [indexOf()](lam-viec-voi-mang-co-ban.md#indexof)
  * [lastIndexOf()](lam-viec-voi-mang-co-ban.md#lastindexof)
  * [includes()](lam-viec-voi-mang-co-ban.md#includes)
* [Chuyển đổi và đảo ngược mảng](lam-viec-voi-mang-co-ban.md#chuyen-doi-va-dao-nguoc-mang)
  * [join()](lam-viec-voi-mang-co-ban.md#join)
  * [reverse()](lam-viec-voi-mang-co-ban.md#reverse)
  * [toString()](lam-viec-voi-mang-co-ban.md#tostring)
* [Các sai lầm thường gặp](lam-viec-voi-mang-co-ban.md#cac-sai-lam-thuong-gap)
  * [Quên rằng push(), pop(), unshift(), shift() và reverse() thay đổi mảng ban đầu](lam-viec-voi-mang-co-ban.md#cac-sai-lam-thuong-gap)
  * [Sử dụng indexOf() trên mảng có chứa NaN](lam-viec-voi-mang-co-ban.md#su-dung-indexof-tren-mang-co-chua-nan)

### Thêm và xóa phần tử

#### push()

`push()` thêm một hoặc nhiều phần tử vào cuối mảng và trả về độ dài mới của mảng.

```javascript
let fruits = ["Apple", "Banana"];
let newLength = fruits.push("Cherry");

console.log(fruits); // (3) ["Apple", "Banana", "Cherry"]
console.log(newLength); // 3
```

_**Lưu ý:** Mảng sẽ bị thay đổi sau khi gọi method này._

**Trường hợp sử dụng:** Khi muốn thêm một hoặc nhiều phần tử vào cuối mảng. Đây là cách cơ bản và phổ biến nhất để thêm dữ liệu vào một mảng.

Ngoài ra, `push()` có thể nhận nhiều tham số hơn, tương ứng với số phần tử muốn thêm vào cuối mảng.

```javascript
let fruits = ["Apple", "Banana"];

// Thêm nhiều phần tử vào cuối mảng cùng một lúc
fruits.push("Cherry", "Dragonfruit", "Elderberry");

console.log(fruits); // (5) ["Apple", "Banana", "Cherry", "Dragonfruit", "Elderberry"]
```

#### &#x20;pop()

`pop()` loại bỏ phần tử cuối cùng của mảng và trả về phần tử đó.

```javascript
let fruits = ["Apple", "Banana", "Cherry"];
let lastFruit = fruits.pop();

console.log(lastFruit); // Cherry
console.log(fruits); // (2) ["Apple", "Banana"]
```

_**Lưu ý:** Mảng sẽ bị thay đổi sau khi gọi method này._

**Trường hợp sử dụng:** Khi cần xóa và lấy phần tử cuối cùng của mảng.

#### unshift()

`unshift()` thêm một hoặc nhiều phần tử vào đầu mảng và trả về độ dài mới của mảng.

```javascript
let fruits = ["Banana", "Cherry"];
let newLength = fruits.unshift("Apple");

console.log(fruits); // (3) ["Apple", "Banana", "Cherry"]
console.log(newLength); // 3
```

_**Lưu ý:** Mảng sẽ bị thay đổi sau khi gọi method này._

**Trường hợp sử dụng:** Khi muốn thêm một hoặc nhiều phần tử vào đầu mảng. Đặc biệt hữu ích khi bạn muốn giữ nguyên thứ tự của các phần tử sau khi thêm mới.

Ngoài ra, `unshift()` có thể nhận nhiều tham số hơn, tương ứng với số phần tử muốn thêm vào đầu mảng.

```javascript
let numbers = [3, 4, 5];

// Thêm 1 và 2 vào đầu mảng
numbers.unshift(1, 2);

console.log(numbers); // (5) [1, 2, 3, 4, 5]
```

#### shift()

`shift()` loại bỏ phần tử đầu tiên của mảng và trả về phần tử đó.

```javascript
let fruits = ["Apple", "Banana", "Cherry"];
let firstFruit = fruits.shift();

console.log(firstFruit); // Apple
console.log(fruits); // (2) ["Banana", "Cherry"]
```

_**Lưu ý:** Mảng sẽ bị thay đổi sau khi gọi method này._

**Trường hợp sử dụng:** Khi muốn xóa phần tử đầu tiên của mảng và cần sử dụng giá trị của phần tử đó. Phương thức này thường được dùng trong các tình huống như xử lý hàng đợi.

***

### Tìm kiếm và kiểm tra phần tử

#### indexOf()

`indexOf()` tìm chỉ số đầu tiên của một phần tử trong mảng. Nếu không tìm thấy, trả về -1.

```javascript
let fruits = ["Apple", "Banana", "Cherry"];

console.log(fruits.indexOf("Banana")); // 1
console.log(fruits.indexOf("Mango")); // -1
```

_**Lưu ý:**_&#x20;

* _So sánh giữa các phần tử là chính xác (strict equality), tức là cả kiểu dữ liệu và giá trị._
* _`NaN` không bằng chính nó nên indexOf  luôn trả về -1 khi tìm `NaN` trong mảng._

**Trường hợp sử dụng**: Khi cần xác định vị trí của một phần tử trong mảng. Đặc biệt hữu ích khi kiểm tra xem một giá trị có tồn tại trong mảng hay không và biết được vị trí của nó.

Ngoài ra, `indexOf()` có thể nhận thêm một tham số thứ hai, đó là vị trí bắt đầu tìm kiếm trong mảng.

```javascript
let fruits = ["Apple", "Banana", "Cherry", "Apple"];

// Tìm "Apple" bắt đầu từ vị trí 2
console.log(fruits.indexOf("Apple", 2)); // 3
```

#### lastIndexOf()

`lastIndexOf()` tìm chỉ số cuối cùng của một phần tử trong mảng. Nếu không tìm thấy, trả về -1.

```javascript
let numbers = [1, 2, 3, 2, 1];

console.log(numbers.lastIndexOf(2)); // 3
```

_**Lưu ý:**_&#x20;

* _Tìm kiếm từ cuối mảng về đầu mảng._
* _Tương tự như phương thức_ `indexOf`, `lastIndexOf` so sánh chính xác _(strict equality) và không thể tìm NaN trong mảng._

**Trường hợp sử dụng:** Khi cần tìm vị trí xuất hiện cuối cùng của một phần tử, đặc biệt hữu ích trong các mảng có các phần tử lặp lại và bạn muốn biết vị trí lần xuất hiện cuối cùng của chúng.

Ngoài ra, giống như `indexOf()`, `lastIndexOf()` cũng có thể nhận một tham số thứ hai là vị trí bắt đầu tìm kiếm, nhưng nó sẽ tìm từ cuối mảng lên.

```javascript
let numbers = [1, 2, 3, 4, 2, 5];

// Tìm "2" bắt đầu từ vị trí 4 về đầu mảng
console.log(numbers.lastIndexOf(2, 3)); // 1
```

#### &#x20;includes()

`includes()` kiểm tra xem một mảng có chứa một phần tử nhất định hay không, trả về `true` hoặc `false`.

```javascript
let numbers = [1, 2, 3];

console.log(numbers.includes(2)); // true
console.log(numbers.includes(4)); // false
```

_**Lưu ý:** Phương thức này sử dụng **same-value-zero** comparison algorithm để xác định xem một mảng có chứa một giá trị nhất định hay không. Điều này khác biệt so với **strict equality** (`===`) ở chỗ nó coi `NaN` là bằng nhau (trong khi `NaN === NaN` trả về `false`)._

**Trường hợp sử dụng:** Khi cần kiểm tra xem một mảng có chứa một phần tử nhất định hay không, mà không quan tâm đến vị trí của phần tử đó.

***

### Chuyển đổi và đảo ngược mảng

#### join()

`join()` nối tất cả các phần tử của mảng thành một chuỗi, với một dấu phân cách giữa chúng.

```javascript
let fruits = ["Apple", "Banana", "Cherry"];

console.log(fruits.join(" / ")); // Apple / Banana / Cherry
```

_**Lưu ý:** Nếu mảng có phần tử `undefined` hoặc `null`, chúng sẽ được chuyển thành chuỗi rỗng trong chuỗi kết quả._

**Trường hợp sử dụng:** Khi muốn biến một mảng thành một chuỗi, có thể dùng để tạo ra một chuỗi từ các phần tử của mảng, như tạo ra một danh sách được ngăn cách bằng dấu phẩy, hoặc một đoạn văn.

#### &#x20;reverse()

```javascript
let numbers = [1, 2, 3];

// Đảo ngược thứ tự các phần tử
const reversed = numbers.reverse();

console.log(reversed); // (3) [3, 2, 1]
```

_**Lưu ý:** Mảng sẽ bị thay đổi sau khi gọi method này._

**Trường hợp sử dụng:** Khi muốn đảo ngược thứ tự các phần tử trong mảng, có thể dùng cho việc sắp xếp hoặc đơn giản chỉ là để đảo ngược thứ tự hiển thị.

#### &#x20;toString()

`toString()` chuyển đổi mảng thành một chuỗi các giá trị, cách nhau bằng dấu phẩy.

```javascript
let fruits = ["Apple", "Banana", "Cherry"];

console.log(fruits.toString()); // Apple,Banana,Cherry
```

_**Lưu ý:** Tương tự như `join()` nhưng không thể chỉ định dấu phân cách._

**Trường hợp sử dụng:** Khi cần chuyển một mảng thành một chuỗi để hiển thị hoặc lưu trữ. Phương thức này tự động được gọi khi một mảng cần được chuyển đổi thành chuỗi, như trong việc nối chuỗi (_ép kiểu_).

***

### Các sai lầm thường gặp

#### Quên rằng push(), pop(), unshift(), shift() và reverse() thay đổi mảng ban đầu

* **Sai lầm:** Sử dụng các phương thức này với suy nghĩ mảng ban đầu không thay đổi, dẫn đến việc mất mát dữ liệu không mong muốn.
* **Khắc phục:** Luôn nhớ rằng những phương thức này sẽ thay đổi mảng gốc. Nếu muốn giữ nguyên mảng ban đầu, cân nhắc sử dụng các phương thức khác hoặc sao chép mảng trước khi thực hiện thay đổi.

#### Sử dụng indexOf() trên mảng có chứa NaN

* **Sai lầm:** `indexOf()` không thể tìm thấy `NaN` trong mảng vì `NaN` không bằng chính nó (`NaN === NaN` là `false`).
* **Khắc phục:** Sử dụng `includes()` để xử lý trường hợp có `NaN`.

{% hint style="info" %}
Tóm tắt

* **Thêm và xóa phần tử**: Các phương thức `push()`, `pop()`, `unshift()`, và `shift()` cho phép thêm hoặc xóa các phần tử từ mảng và thay đổi mảng gốc.
  * **push()**: Thêm phần tử vào cuối mảng.
  * **pop()**: Xóa phần tử cuối cùng của mảng.
  * **unshift()**: Thêm phần tử vào đầu mảng.
  * **shift()**: Xóa phần tử đầu tiên của mảng.
* **Tìm kiếm và kiểm tra phần tử**: `indexOf()`, `lastIndexOf()`, và `includes()` giúp tìm vị trí hoặc kiểm tra sự tồn tại của phần tử trong mảng.
  * **indexOf()**: Tìm chỉ số đầu tiên của phần tử.
  * **lastIndexOf()**: Tìm chỉ số cuối cùng của phần tử.
  * **includes()**: Kiểm tra sự tồn tại của phần tử.
* **Chuyển đổi và đảo ngược mảng**: `join()`, `toString()`, và `reverse()` cho phép chuyển đổi mảng thành chuỗi và đảo ngược thứ tự của mảng.
  * **join()**: Nối các phần tử mảng thành chuỗi với dấu phân cách.
  * **toString()**: Chuyển mảng thành chuỗi, các phần tử cách nhau bằng dấu phẩy.
  * **reverse()**: Đảo ngược thứ tự các phần tử trong mảng.
* **Các sai lầm thường gặp**
  * **Sử dụng push() và unshift() không đúng cách**: Gọi mà không truyền tham số, khiến mảng thay đổi độ dài mà không thêm phần tử mới.
  * **Quên rằng push(), pop(), unshift(), shift() và reverse() thay đổi mảng ban đầu**: Dẫn đến thay đổi hoặc mất mát dữ liệu không mong muốn.
  * **Sử dụng indexOf() trên mảng có chứa NaN**: `indexOf()` không thể tìm thấy `NaN` vì `NaN` không bằng chính nó.
{% endhint %}
