# Tìm hiểu về giá trị Infinity

`Infinity` là một giá trị đặc biệt trong JavaScript đại diện cho một số lớn vô hạn (dương vô cùng). Tương tự, `-Infinity` đại diện cho một số nhỏ vô hạn (âm vô cùng).

**Cú pháp:**

```js
let positiveInfinity = Infinity;
let negativeInfinity = -Infinity;
```

`Infinity` và `-Infinity` thường được trả về trong một số thường hợp sau:

* Khi chia một số dương cho 0.
* Khi chia một số âm cho 0.
* Khi một phép tính số học vượt quá giá trị lớn nhất/nhỏ nhất có thể biểu diễn trong JavaScript.
* Các phép toán với `Infinity` hoặc `-Infinity` cũng sẽ trả về `Infinity` hoặc `-Infinity` tương ứng.

```javascript
console.log(1 / 0); // Infinity
console.log(-1 / 0); // -Infinity
console.log(10 ** 1000); // Infinity
console.log(-(10 ** 1000)); // -Infinity
console.log(Infinity + 100); // Infinity
console.log(-Infinity - 1000); // -Infinity
```

**Cách kiểm tra số hữu hạn:**

`isFinite` là hàm dùng để kiểm tra xem một giá trị có phải là số hữu hạn hay không. Nếu giá trị là một số hữu hạn (không phải `Infinity`, `-Infinity`, hoặc `NaN`), hàm sẽ trả về `true`. Ngược lại, hàm sẽ trả về `false`.

```js
console.log(isFinite(100)); // true
console.log(isFinite(Infinity)); // false
console.log(isFinite(-Infinity)); // false
console.log(isFinite(NaN)); // false

// Tự động ép kiểu sang số
console.log(isFinite("100")); // true
console.log(isFinite("abc")); // false
```

Dùng `isFinite` với giá trị không phải số có thể trả về kết quả không mong muốn do JavaScript tự động chuyển đổi kiểu. Vì vậy, bạn có thể kết hợp `typeof` hoặc dùng `Number.isFinite` để kiểm tra chính xác số hữu hạn.

Ví dụ:

```js
console.log(isFinite(true)); // true (true được chuyển thành 1)
console.log(Number.isFinite(true)); // false
```

***

### Tại sao cần sử dụng infinity

**Trường hợp cần dùng:**

* Khi muốn biểu diễn một giá trị lớn vô hạn hoặc nhỏ vô hạn trong các phép tính.
* Trong các thuật toán cần so sánh.

**Bài toán và ví dụ:**

Tìm giá trị lớn nhất trong mảng:

```javascript
function findMax(input) {
  let max = -Infinity;

  for (let i = 0; i < input.length; i++) {
    if (input[i] > max) {
      max = input[i];
    }
  }

  return max;
}

let arr = [1, 2, 3, 4, 5];

console.log(findMax(arr)); // 5
```

Tìm giá trị nhỏ nhất trong mảng:

```javascript
function findMin(input) {
  let min = Infinity;

  for (let i = 0; i < input.length; i++) {
    if (input[i] < min) {
      min = input[i];
    }
  }

  return min;
}

let arr = [1, 2, 3, 4, 5];

console.log(findMin(arr)); // 1
```

{% hint style="info" %}
Tóm tắt

* **Infinity trong JavaScript**: `Infinity` là một giá trị đặc biệt đại diện cho số lớn vô hạn (dương vô cùng), trong khi `-Infinity` đại diện cho số nhỏ vô hạn (âm vô cùng). Chúng thường xuất hiện trong các phép chia cho 0 hoặc khi kết quả của phép toán vượt quá giới hạn biểu diễn của JavaScript.
* **Sử dụng hàm `isFinite`**: Để kiểm tra xem một giá trị có phải là số hữu hạn hay không, bạn có thể sử dụng hàm `isFinite`. Tuy nhiên, cần lưu ý việc tự động ép kiểu trong JavaScript, có thể gây ra kết quả không mong muốn, vì vậy nên sử dụng `Number.isFinite` cho kết quả chính xác hơn.
* **Ứng dụng của Infinity**: Infinity được sử dụng trong các thuật toán, đặc biệt là khi cần so sánh. Ví dụ, có thể sử dụng `-Infinity` để tìm giá trị lớn nhất trong mảng và `Infinity` để tìm giá trị nhỏ nhất.
{% endhint %}
