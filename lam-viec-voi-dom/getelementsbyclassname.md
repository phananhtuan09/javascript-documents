# getElementsByClassName

Phương thức `getElementsByClassName` là method của Document trả về một đối tượng giống mảng gồm tất cả các element con có tất cả các tên class đã cho.

Bạn cũng có thể gọi `getElementsByClassName` trên bất kỳ element nào; nó sẽ chỉ trả về các element là con của element gốc được chỉ định với tên class đã cho.

### Cú pháp

```javascript
getElementsByClassName(names)
```

Tham số

* `names`: Một chuỗi biểu diễn tên class cần khớp; nhiều tên class được phân tách bằng khoảng trắng.

### Giá trị trả về

Một `HTMLCollection` trực tiếp gồm các element được tìm thấy.

### Ví dụ

Lấy tất cả các element có class 'test':

```javascript
document.getElementsByClassName("test");
```

Lấy tất cả các element có cả class 'red' và 'test':

```javascript
document.getElementsByClassName("red test");
```

Lấy tất cả các element có class là 'test', bên trong một element có ID là 'main':

```javascript
document.getElementById("main").getElementsByClassName("test");
```

Lấy element đầu tiên có class là 'test' hoặc không xác định nếu không có element nào khớp:

```javascript
document.getElementsByClassName("test")[0];
```

Chúng ta cũng có thể sử dụng các phương thức của `Array.prototype` trên bất kỳ `HTMLCollection` nào bằng cách truyền `HTMLCollection` làm giá trị `this` của phương thức. Ở đây chúng ta sẽ tìm thấy tất cả các element `div` có class 'test':

```javascript
const testElements = document.getElementsByClassName("test");
const testDivs = Array.prototype.filter.call(
  testElements,
  (testElement) => testElement.nodeName === "DIV",
);
```

