# querySelector

Phương thức `querySelector()` của **Document** trả về element đầu tiên trong document phù hợp với bộ chọn CSS hoặc nhóm `CSS Selector` được chỉ định. Nếu không tìm thấy phần tử nào, phương thức sẽ trả về `null`.

### Cú pháp

```javascript
querySelector(selectors)
```

### Tham số

* **selectors**: Chuỗi chứa một hoặc nhiều bộ chọn cần tìm. Chuỗi này phải là một chuỗi CSS Selector hợp lệ; nếu không, một execption **SyntaxError** sẽ được ném ra.

### Giá trị trả về

Một đối tượng **Element** đại diện cho element đầu tiên trong document phù hợp với CSS Selector đã chỉ định, hoặc `null` nếu không tìm thấy element nào.

Nếu bạn cần **danh sách tất cả các elemenmt phù hợp**, hãy sử dụng **`querySelectorAll()`** thay vì `querySelector()`.

### Expections

* **SyntaxError DOMException**: Được ném ra nếu cú pháp của bộ chọn không hợp lệ.

### Ví dụ

1. Tìm phần tử đầu tiên khớp với một class css:

```javascript
const el = document.querySelector(".myclass");
```

2. Bộ chọn phức tạp

```javascript
const el = document.querySelector("div.user-panel.main input[name='login']");
```

> Các Selector có thể rất mạnh mẽ. Ví dụ sau sẽ tìm thẻ `<input>` đầu tiên có `name="login"`, nhưng chỉ nếu nó nằm bên trong một `<div>` có lớp `"user-panel main"`

3. Selector phủ định

```javascript
const el = document.querySelector(
  "div.user-panel:not(.main) input[name='login']"
);
```

> Câu lệnh trên sẽ chọn thẻ `<input>` có `name="login"` nhưng chỉ khi nó nằm trong một `<div>` có lớp `"user-panel"` nhưng **không** có lớp `"main"`.





