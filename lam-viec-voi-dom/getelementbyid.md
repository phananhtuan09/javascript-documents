# getElementById

Phương thức `getElementById()` của `Document` trả về một đối tượng `Element` đại diện cho phần tử có thuộc tính `id` khớp với chuỗi đã chỉ định. Vì ID trong tài liệu phải là duy nhất, phương thức này giúp truy xuất phần tử nhanh chóng.

> Lưu ý: ID phải là duy nhất bên trong một document. Nếu hai hoặc nhiều element trong một document có cùng ID, phương thức này trả về element đầu tiên được tìm thấy.

### Cú  pháp

```javascript
getElementById(id)
```

### Tham số

* `id`: ID của element cần xác định. ID là chuỗi phân biệt chữ hoa chữ thường và duy nhất trong document; chỉ một element có ID được chỉ định.

### Giá trị trả về

Đối tượng Element mô tả đối tượng element DOM khớp với ID đã chỉ định hoặc `null` nếu không tìm thấy element khớp nào trong document.

### Ví dụ

```javascript
// HTML
<html lang="en">
  <head>
    <title>getElementById example</title>
  </head>
  <body>
    <p id="para">Some text here</p>
    <button onclick="changeColor('blue');">blue</button>
    <button onclick="changeColor('red');">red</button>
  </body>
</html>
// JS
function changeColor(newColor) {
  const elem = document.getElementById("para");
  elem.style.color = newColor;
}
```

Khi tạo một thẻ HTML với thuộc tính id thì nó sẽ tạo ra một biến với id đã tạo

```javascript
console.log(para); 
// Nó sẽ trỏ về HTML p có id = "para" tương tự như dùng getElementById
```
