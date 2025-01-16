# Phương thức slice() và splice()

Mục lục

* [Tìm hiểu phương thức slice()](phuong-thuc-slice-va-splice.md#tim-hieu-phuong-thuc-slice)
  * [Phương thức slice() là gì?](phuong-thuc-slice-va-splice.md#phuong-thuc-slice-la-gi)
  * [Các cách làm việc với slice()](phuong-thuc-slice-va-splice.md#cac-cach-lam-viec-voi-slice)
* [Tìm hiểu phương thức splice()](phuong-thuc-slice-va-splice.md#tim-hieu-phuong-thuc-splice)
  * [Phương thức splice() là gì?](phuong-thuc-slice-va-splice.md#phuong-thuc-splice-la-gi)
  * [Các cách làm việc với splice()](phuong-thuc-slice-va-splice.md#cac-cach-lam-viec-voi-splice)
* [Các sai lầm thường gặp](phuong-thuc-slice-va-splice.md#cac-sai-lam-thuong-gap)
  * [Không hiểu về chỉ số âm](phuong-thuc-slice-va-splice.md#khong-hieu-ve-chi-so-am)
  * [“Tưởng” slice() thay đổi mảng gốc](phuong-thuc-slice-va-splice.md#tuong-slice-thay-doi-mang-goc)
  * [Sử dụng “delete” để xóa phần tử trong mảng](phuong-thuc-slice-va-splice.md#su-dung-delete-de-xoa-phan-tu-trong-mang)

### Tìm hiểu phương thức slice()

#### Phương thức slice() là gì?

Phương thức `slice()` tạo một bản sao hoặc trích xuất một phần của mảng ban đầu mà không làm thay đổi mảng ban đầu. Nó trả về một mảng mới chứa các phần tử được trích xuất từ mảng gốc.

Cú pháp:

```js
array.slice(start, end);
```

Cách sử dụng:

* `slice()`: Trích xuất toàn bộ mảng.
* `slice(start)`: Trích xuất mảng bắt đầu từ chỉ số `start` đến cuối mảng.
* `slice(start, end)`: Trích xuất một phần của mảng từ chỉ số `start` đến trước chỉ số `end`.

Ví dụ sử dụng:

```javascript
let fruits = [
  "Apple",
  "Banana",
  "Mango",
  "Orange",
  "Papaya"
];
let result = fruits.slice(2, 4);

console.log(result); // (2) ["Mango", "Orange"]
```

`slice()` rất hữu ích khi bạn cần tạo một bản sao nhanh chóng của một phần mảng mà không muốn thay đổi mảng gốc. Nó cho phép bạn:

* Trích xuất một phần của mảng mà không gây ảnh hưởng đến mảng ban đầu.
* Tạo bản sao của mảng để thực hiện thao tác trên đó mà không làm ảnh hưởng dữ liệu mảng ban đầu.

> slice() là phương thức sallow copy (sao chép nông).

#### Các cách làm việc với slice()

**1. Tạo bản sao của toàn bộ mảng**

Để tạo một bản sao của toàn bộ mảng, bạn có thể gọi `slice()` mà không cần truyền tham số (_hoặc truyền số 0_).

Ví dụ:

```javascript
let numbers = [1, 2, 3, 4, 5];
let copyOfNumbers = numbers.slice();
// hoặc: let copyOfNumbers = numbers.slice(0);

console.log(copyOfNumbers); // (5) [1, 2, 3, 4, 5]
```

Lúc này, việc chỉnh sửa vào mảng `copyOfNumbers` sẽ không ảnh hưởng tới mảng ban đầu (`numbers`).

**2. Trích xuất một phần của mảng**

Bạn có thể trích xuất một phần của mảng bằng cách chỉ định chỉ số bắt đầu và kết thúc.

Ví dụ:

```javascript
let numbers = [1, 2, 3, 4, 5];
let result = numbers.slice(1, 4);

console.log(result); // (3) [2, 3, 4]
```

Ví dụ, bạn có một danh sách sản phẩm và trên trang chủ của bạn chỉ muốn hiển thị 3 sản phẩm đầu tiên, bạn có thể sử dụng `array.slice(0, 3)` để lấy ra mảng mới gồm 3 phần tử đầu tiên của mảng.

**3. Sử dụng chỉ số âm**

`slice()` cũng hỗ trợ chỉ số âm, nơi `-1` đại diện cho phần tử cuối cùng của mảng.

Ví dụ:

```javascript
let numbers = [1, 2, 3, 4, 5];
let result = numbers.slice(-3);

console.log(result); // (3) [3, 4, 5]
```

Ví dụ, bạn có một danh sách các thông báo và chỉ muốn hiển thị 5 thông báo mới nhất trên giao diện, bạn có thể sử dụng `array.slice(-5)` để lấy ra mảng mới gồm 5 phần tử cuối cùng của mảng.

***

### Tìm hiểu phương thức splice()

#### Phương thức splice() là gì?

Phương thức `splice()` được sử dụng để thêm hoặc loại bỏ các phần tử trong một mảng, nó hữu ích khi muốn thêm và loại bỏ phần tử tại bất kỳ vị trí nào trong mảng. Phương thức này sẽ sửa đổi vào mảng ban đầu.

Cú pháp:

```js
array.splice(start, deleteCount, item1, item2, ...);
```

Ý nghĩa các tham số:

* `start`: chỉ định vị trí bắt đầu thêm hoặc loại bỏ phần tử trong mảng. Nếu giá trị này là âm, `start` sẽ được tính từ cuối mảng, với `-1` là phần tử cuối cùng của mảng.
* `deleteCount` (tùy chọn): số lượng phần tử cần loại bỏ, bắt đầu từ vị trí `start`. Nếu `deleteCount` bị bỏ qua hoặc lớn hơn số phần tử còn lại từ vị trí `start` đến cuối mảng, thì tất cả các phần tử từ `start` đến cuối mảng sẽ bị loại bỏ. Nếu `deleteCount` là `0`, phương thức này sẽ không xóa bất kỳ phần tử nào nhưng vẫn có thể thêm các phần tử mới vào mảng tại vị trí chỉ định.
* `item1, item2, ...` (tùy chọn): các phần tử cần được thêm vào mảng, bắt đầu từ vị trí start. Nếu không có phần tử nào được thêm, `splice()` chỉ đơn giản loại bỏ các phần tử khỏi mảng.

#### Các cách làm việc với splice()

**1. Thêm phần tử vào mảng**

Để thêm một hoặc nhiều phần tử vào mảng, bạn chỉ cần đặt `deleteCount` thành 0 và thêm các phần tử sau đó.

Ví dụ:

```javascript
let numbers = [1, 2, 4, 5];

// Thêm số 3 vào vị trí index 2
numbers.splice(2, 0, 3);

console.log(numbers); // (5) [1, 2, 3, 4, 5]
```

Trường hợp thêm một hoặc nhiều phần tử vào đầu hoặc cuối mảng bạn có thể dùng `unshift()` và `push()` cho ngắn gọn và đơn giản. Tuy nhiên, trường hợp cần thêm một hoặc nhiều phần tử vào các vị trí khác bạn sẽ cần sử dụng tới `splice()`.

**2. Loại bỏ phần tử từ mảng**

Bạn có thể loại bỏ phần tử khỏi mảng bằng cách chỉ định số lượng phần tử cần loại bỏ mà không cần thêm phần tử mới.

Ví dụ:

```javascript
let numbers = [1, 2, 3, 4, 5];

// Loại bỏ 3 phần tử bắt đầu từ vị trí 1
numbers.splice(1, 3);

console.log(numbers); // (2) [1, 5]
```

Sử dụng `shift()` và `pop()` chỉ hiệu quả trong tình huống cần loại bỏ một phần tử ở đầu hoặc cuối mảng. Trong tình huống cần loại bỏ một hoặc nhiều phần tử liên tiếp nhau ở các vị trí khác bạn sẽ cần sử dụng tới `splice()`.

**3. Thay thế phần tử trong mảng**

Bạn có thể thay thế một hoặc nhiều phần tử trong mảng bằng cách loại bỏ chúng và thêm các phần tử mới cùng một lúc.

Ví dụ:

```javascript
let animals = ["Dog", "Cat", "Rabbit", "Horse"];

// Thay thế "Rabbit" bằng "Snake"
animals.splice(2, 1, "Snake");

console.log(animals); // (4) ["Dog", "Cat", "Snake", "Horse"]
```

Một cách khác để thay thế `"Rabbit"` bằng `"Snake"` ở trên là `animals[2] = "Snake"`. Tuy nhiên cách này chỉ hiệu quả khi thay thế một phần tử. Trường hợp bạn cần thay thế nhiều phần tử một lúc thì cần sử dụng tới `splice()`.

***

### Các sai lầm thường gặp

#### Không hiểu về chỉ số âm

Một số người mới sử dụng có thể nhầm lẫn về việc sử dụng chỉ số âm, dẫn đến việc không trích xuất hoặc xóa đúng phần tử mong muốn.

**Cách giải quyết tốt:**

Luôn nhớ rằng chỉ số âm được tính từ cuối mảng. `-1` là phần tử cuối cùng.

#### “Tưởng” slice() thay đổi mảng gốc

`slice()` không thay đổi mảng gốc mà trả về một bản sao hoặc phần của mảng gốc. Việc không nhận thức rõ về điều này có thể gây nhầm lẫn.

**Cách giải quyết tốt:**

Luôn gán kết quả của `slice()` vào một biến mới để sử dụng.

#### Sử dụng “delete” để xóa phần tử trong mảng

Khi sử dụng `delete array[index]` để xóa một phần tử khỏi mảng, bạn sẽ gặp một số vấn đề. Cách tiếp cận này chỉ xóa giá trị tại vị trí chỉ định và để lại một “lỗ trống” (_empty_) trong mảng, nghĩa là vị trí đó không còn giữ giá trị nào nữa nhưng mảng vẫn giữ nguyên kích thước ban đầu. Điều này dẫn đến việc khi truy cập vị trí đó sẽ có giá trị là `undefined`.

Ví dụ:

<pre class="language-javascript"><code class="lang-javascript">let fruits = ["Apple", "Banana", "Mango"];

delete fruits[1];

console.log(fruits); // (3) ["Apple", "Mango"]
console.log(fruits.length); // 3

// Vòng lặp vẫn chạy 3 lần,
// giá trị của lần lặp "empty" sẽ là undefined
for (let fruit of fruits) {
  console.log(fruit);
  // Apple
  // undefined
<strong>  // Mango
</strong>}
</code></pre>

Trong ví dụ trên, sau khi xóa, `fruits[1]` trả về `undefined`, nhưng kích thước của mảng (`fruits.length`) vẫn không thay đổi.

**Cách giải quyết là sử dụng splice():**

Phương thức `splice()` giải quyết vấn đề này bằng cách cho phép bạn loại bỏ phần tử khỏi mảng mà không để lại “lỗ trống”. Mảng sẽ được tự động “dồn lại”, đảm bảo rằng không có giá trị `undefined` nào giữa các phần tử, và `length` của mảng sẽ được cập nhật lại đúng với số lượng phần tử hiện tại.

Ví dụ sử dụng `splice()` để loại bỏ một phần tử:

```javascript
let fruits = ["Apple", "Banana", "Mango"];

fruits.splice(1, 1);

console.log(fruits); // (2) ["Apple", "Mango"]
console.log(fruits.length); // 2
```

Trong ví dụ này, `splice(1, 1)` loại bỏ một phần tử bắt đầu từ vị trí index 1. Mảng `fruits` sau đó sẽ không còn “lỗ trống” nào, và kích thước của mảng giảm xuống còn 2, phản ánh chính xác số lượng phần tử trong mảng sau khi một phần tử đã bị loại bỏ.

{% hint style="info" %}
Tóm tắt

* **Phương thức slice()**: Tạo bản sao hoặc trích xuất một phần của mảng mà không làm thay đổi mảng gốc, trả về một mảng mới. Có thể sử dụng chỉ số âm để trích xuất từ cuối mảng.
* **Phương thức splice()**: Thêm hoặc loại bỏ các phần tử của mảng tại bất kỳ vị trí nào, sửa đổi mảng gốc. Cho phép thêm, loại bỏ hoặc thay thế phần tử.
* **Sai lầm thường gặp**:
  * Sử dụng chỉ số âm sai cách. Hãy luôn nhớ `-1` là ứng với phần tử cuối cùng.
  * Nhầm tưởng `slice()` thay đổi mảng gốc. Hãy luôn nhận giá trị mới được trả về từ `slice()`.
  * Sử dụng `delete` để xóa phần tử trong mảng sẽ tạo ra “lỗ trống”. Hãy dùng `splice()` để loại bỏ phần tử mà không để lại “lỗ trống”.
{% endhint %}
