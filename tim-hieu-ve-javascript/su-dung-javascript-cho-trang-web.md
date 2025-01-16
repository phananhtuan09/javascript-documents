# Sử dụng JavaScript cho trang web

Mục lục

* [Tích hợp JavaScript vào web](su-dung-javascript-cho-trang-web.md#tich-hop-javascript-vao-web)
  * [Các bước tích hợp](su-dung-javascript-cho-trang-web.md#cac-buoc-tich-hop)
* [Điểm quan trọng](su-dung-javascript-cho-trang-web.md#diem-quan-trong)
* [Lỗi thường gặp](su-dung-javascript-cho-trang-web.md#loi-thuong-gap)

> _Hãy tưởng tượng bạn đang xây một ngôi nhà. Cấu trúc và kiểu dáng của ngôi nhà được tạo nên từ các viên gạch và xi măng - giống như HTML và CSS trên một trang web. Nhưng để ngôi nhà thực sự sử dụng tốt, bạn cần thêm hệ thống điện, nước, và thiết bị thông minh khác, và JavaScript giống như hệ thống đó - nó mang lại sự tương tác và trải nghiệm tốt cho người sử dụng trang web của bạn._

<figure><img src="../.gitbook/assets/66fcf2673ebc2.png" alt=""><figcaption><p><em>Javascript xây dựng các tính năng tương tác hiện đại cho trang web của bạn.</em></p></figcaption></figure>

### Tích hợp JavaScript vào web

Chúng ta sẽ sử dụng thêm thẻ `script` trong HTML. Bạn có thể viết trực tiếp JavaScript trong thẻ `script` hoặc liên kết tới một file JavaScript ở ngoài.

#### Các bước tích hợp

Đặt thẻ `script` trong thẻ `head` hoặc trong thẻ `body` (ngay trước thẻ đóng của `body`).

**1. Viết code bên trong thẻ script.**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>
<body>
  <h1>My document</h1>
  <script>
  	alert("Hello world!");
  </script>
</body>
</html>

```

Sử dụng cách này đối với đoạn code JavaScript nhỏ và chỉ cần dùng trong file HTML hiện tại.

**2. Link tới file JavaScript bên ngoài**\
Đầu tiên, tạo file `main.js` với nội dung sau:

```javascript
// main.js
alert("Hello world!");
```

Tiếp theo, dùng thẻ `script` để liên kết tới file `main.js` vừa tạo:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>
<body>
  <h1>My document</h1>
  <script src="./main.js"></script>
</body>
</html>

```

Cách này dùng khi muốn tái sử dụng lại các đoạn code JavaScript ở nhiều trang khác nhau. Ví dụ như ở trang chủ, tin tức, liên hệ, v.v cùng liên kết về file `main.js` để dụng code JavaScript trong đó.

***

### Điểm quan trọng

* Nên đặt thẻ `script` ở vị trí cuối cùng trong thẻ `body` (ngay trước thẻ đóng của `body`) để tránh một số lỗi thường gặp và giúp trang web hiển thị nhanh hơn.
* Hạn chế viết trực tiếp JavaScript trong file HTML (chỉ sử dụng khi là đoạn code nhỏ và không có tính tái sử dụng), viết JavaScript ra file riêng bên ngoài giúp dễ quản lý và bảo trì hơn.

### Lỗi thường gặp

* Đặt vị trí thẻ `script` ở sai vị trí trong HTML dẫn tới lỗi và làm chậm trang web.
* Sử dụng quá nhiều JavaScript không thực sự cần thiết gây nặng trang. Ví dụ như thêm quá nhiều các thư viện mà không dùng tới, thêm các thư viện tạo hiệu ứng trên trang gây chậm trang, giảm trải nghiệm người dùng.\\

{% hint style="info" %}
Tóm tắt

* JavaScript giống như hệ thống điện, nước, tiện nghi trong ngôi nhà của bạn: nó cần thiết để cho trang web trở nên hiện đại và phản hồi lại các tương tác của người dùng.
* Tích hợp JavaScript vào trang web bằng cách sử dụng thẻ `script`. Đặt nó ở vị trí cuối cùng của thẻ `body` là cách đơn giản nhất để hạn chế một số lỗi thường gặp và giúp trang web hiển thị nhanh hơn.
* Có thể viết code JavaScript trực tiếp trong thẻ `script` hoặc link nó tới một file JavaScript ở bên ngoài. Hãy link tới file bên ngoài để dễ quản lý và bảo trì hơn.
* Tránh sử dụng quá nhiều JavaScript không cần thiết vì sẽ gây nặng trang và giảm trải nghiệm người dùng.
{% endhint %}
