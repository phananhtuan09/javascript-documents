# Lệnh Break và Continue

Mục lục

* [Lệnh Break](lenh-break-va-continue.md#lenh-break)
  * [Tìm hiểu về lệnh Break](lenh-break-va-continue.md#tim-hieu-ve-lenh-break)
  * [Ví dụ sử dụng lệnh Break](lenh-break-va-continue.md#vi-du-su-dung-lenh-break)
* [Lệnh Continue](lenh-break-va-continue.md#lenh-continue)
  * [Tìm hiểu lệnh Continue](lenh-break-va-continue.md#tim-hieu-lenh-continue)
  * [Ví dụ sử dụng lệnh Continue](lenh-break-va-continue.md#vi-du-su-dung-lenh-continue)

### Lệnh Break

#### Tìm hiểu về lệnh Break

Lệnh `break` được sử dụng để thoát ra khỏi vòng lặp và dừng việc thực thi các lệnh tiếp theo trong vòng lặp đó.

```javascript
for (let i = 0; i < 10; i++) {
  if (i === 5) {
    // Khi i đạt giá trị 5
    // thoát khỏi vòng lặp
    break;
  }
  console.log(i);
}
// 0
// 1
// 2
// 3
// 4
```

**Lưu ý**: Lệnh `break` chỉ dừng vòng lặp mà nó thuộc về, không ảnh hưởng đến các vòng lặp bên ngoài (_vòng lặp lồng nhau_) hoặc phía trước/sau nó.

#### Ví dụ sử dụng lệnh Break

Giả sử bạn có một mảng lớn chứa thông tin của hàng nghìn sản phẩm và bạn cần tìm kiếm một sản phẩm có mã sản phẩm cụ thể. Thay vì duyệt qua toàn bộ mảng, bạn có thể sử dụng lệnh `break` để thoát khỏi vòng lặp ngay khi tìm thấy sản phẩm đó, tiết kiệm thời gian xử lý.

<pre class="language-javascript"><code class="lang-javascript"><strong>let products = [
</strong>  { id: 1, name: "Sản phẩm A" },
  { id: 2, name: "Sản phẩm B" },
  { id: 3, name: "Sản phẩm C" },
  { id: 4, name: "Sản phẩm D" },
  { id: 5, name: "Sản phẩm E" },
  // ...
]; // Mảng lớn
let searchId = 2; // Mã sản phẩm cần tìm

for (let i = 0; i &#x3C; products.length; i++) {
  if (products[i].id === searchId) {
    console.log("Found product:", products[i]);
    // Thoát khỏi vòng lặp
    // ngay khi tìm thấy sản phẩm
    break;
  }
}
</code></pre>

***

### Lệnh Continue

#### Tìm hiểu lệnh Continue

Lệnh `continue` được sử dụng để bỏ qua phần còn lại của code trong vòng lặp cho lần lặp hiện tại, tiếp tục với lần lặp tiếp theo.

```javascript
for (let i = 0; i < 10; i++) {
  if (i === 5) {
    // Khi i đạt giá trị 5
    // bỏ qua lần lặp này
    continue;
  }
  console.log(i);
}
// 0
// 1
// 2
// 3
// 4
// 6
// 7
// 8
// 9
```

**Lưu ý**: Lệnh `continue` chỉ ảnh hưởng đến lần lặp hiện tại, giúp bỏ qua một số trường hợp không mong muốn mà không thoát khỏi vòng lặp.

#### Ví dụ sử dụng lệnh Continue

Trong một ứng dụng xử lý danh sách sản phẩm, bạn muốn in ra tên của các sản phẩm mà không phải là hàng điện tử. Sử dụng `continue` giúp bỏ qua các sản phẩm điện tử và chỉ xử lý các loại sản phẩm khác.

```javascript
let products = [
  {
    name: "Điện thoại thông minh",
    category: "Điện tử"
  },
  {
    name: "Quạt điều hòa",
    category: "Điện tử"
  },
  {
    name: "Sách lập trình JavaScript",
    category: "Sách"
  },
  {
    name: "Bàn làm việc",
    category: "Nội thất"
  }
];

for (let i = 0; i < products.length; i++) {
  if (products[i].category === "Điện tử") {
    continue; // Bỏ qua sản phẩm điện tử
  }
  console.log(`Sản phẩm: ${products[i].name}`);
}
// Sản phẩm: Sách lập trình JavaScript
// Sản phẩm: Bàn làm việc
```

{% hint style="info" %}
Tóm tắt

* **Lệnh Break**: Dùng để thoát ra khỏi vòng lặp, ngừng thực thi các lệnh tiếp theo trong vòng lặp.
  * **Ví dụ**: Thoát khỏi vòng lặp khi tìm thấy sản phẩm cụ thể trong một mảng lớn, tiết kiệm thời gian xử lý.
* **Lệnh Continue**: Dùng để bỏ qua phần còn lại của code trong vòng lặp cho lần lặp hiện tại, tiếp tục với lần lặp tiếp theo.
  * **Ví dụ**: Bỏ qua các sản phẩm điện tử trong danh sách sản phẩm, chỉ xử lý và in ra tên của các sản phẩm không phải điện tử.
{% endhint %}

