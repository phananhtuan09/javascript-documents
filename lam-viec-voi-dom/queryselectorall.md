# querySelectorAll

Phương thức `querySelectorAll()` của `Document` trả về một danh sách `NodeList` tĩnh chứa tất cả các element trong document khớp với nhóm selector đã chỉ định.

### Cú pháp

```javascript
querySelectorAll(selectors)
```

### Tham số

* **selectors**\
  Một chuỗi chứa một hoặc nhiều selector cần khớp. Chuỗi này phải là một chuỗi selector CSS hợp lệ, nếu không sẽ gây ra expection `SyntaxError`.

### Giá trị trả về

Trả về một `NodeList` tĩnh chứa từng phần tử `Element` khớp với ít nhất một trong các selector đã chỉ định hoặc trả về một `NodeList` rỗng nếu không có element nào khớp.

Các phần tử trong danh sách được sắp xếp theo thứ tự document—nghĩa là, cha trước con, anh trước em.

**Lưu ý:** Nếu selector bao gồm một **pseudo-element CSS**, danh sách trả về luôn rỗng.

### Ngoại lệ

* **`SyntaxError DOMException`**\
  Được ném ra nếu chuỗi selector không hợp lệ.

### Ví dụ

#### Lấy danh sách các element khớp

Lấy danh sách tất cả các thẻ `<p>` trong document:

```js
const matches = document.querySelectorAll("p");
```

Lấy danh sách tất cả các thẻ `<div>` có lớp `note` hoặc `alert`:

```js
const matches = document.querySelectorAll("div.note, div.alert");
```

Lấy danh sách các thẻ `<p>` có cha trực tiếp là một `<div>` có lớp `highlighted` và nằm trong element có `id="test"`:

```js
const container = document.querySelector("#test");
const matches = container.querySelectorAll("div.highlighted > p");
```

Lấy danh sách tất cả các thẻ `<iframe>` có thuộc tính `data-src`:

```js
const matches = document.querySelectorAll("iframe[data-src]");
```

Lấy danh sách các phần tử `<li>` trong danh sách có `id="user-list"` mà có thuộc tính `data-active="1"`:

```js
const container = document.querySelector("#user-list");
const matches = container.querySelectorAll("li[data-active='1']");
```
