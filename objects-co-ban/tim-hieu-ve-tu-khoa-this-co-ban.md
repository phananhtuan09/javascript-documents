# Tìm hiểu về từ khóa this cơ bản

Mục lục

* [Từ khóa this là gì?](tim-hieu-ve-tu-khoa-this-co-ban.md#tu-khoa-this-la-gi)
* [Tại sao cần sử dụng this?](tim-hieu-ve-tu-khoa-this-co-ban.md#tai-sao-can-su-dung-this)

### Từ khóa this là gì?

`this` là một từ khóa trong Javascript, tham chiếu đến đối tượng mà nó thuộc về. Giá trị của `this` phụ thuộc vào ngữ cảnh mà nó được sử dụng, nghĩa là nó có thể thay đổi giá trị tùy thuộc vào cách mà function chứa nó được gọi.

Ví dụ: Trường hợp `this` tham chiếu tới đối tượng mà nó thuộc về.

```javascript
const person = {
  firstName: 'John',
  lastName: 'Smith',
  getFullName: function() {
    console.log(this);
  }
};

person.getFullName();
// {firstName: "John", lastName: "Smith", getFullName: ƒ getFullName()}
```

Trường hợp sử dụng `this` bên trong một phương thức được gọi thông qua một object, ví dụ `person.getFullName()`; lúc này `this` sẽ trả về chính object mà nó thuộc về (hay object được sử dụng để truy cập phương thức), ở ví dụ này `this` sẽ tham chiếu tới `person`.

Ví dụ: Hoàn thiện phương thức `getFullName()` để in ra “tên đầy đủ”.

```javascript
const person = {
  firstName: 'John',
  lastName: 'Smith',
  getFullName: function() {
    return `${this.firstName} ${this.lastName}`;
  }
};

console.log(person.getFullName()); // John Smith
```

***

### Tại sao cần sử dụng this?

`this` cung cấp một phương thức linh hoạt để truy cập vào đối tượng mà function đang thao tác. Điều này không chỉ tăng cường khả năng tái sử dụng và bảo trì code mà còn giúp làm cho chương trình của chúng ta dễ hiểu và quản lý hơn.

Ví dụ: Sử dụng `this` trong phương thức của đối tượng

```javascript
const person = {
  name: 'Alice',
  greet: function() {
    // Nên viết là
    console.log('Hello, ' + this.name);

    // Thay vì
    //console.log('Hello, ' + person.name);
  }
};

person.greet(); // Hello, Alice
```

Tại ví dụ trên, sử dụng `person.name` không linh hoạt bằng `this.name`, vì khi biến `person` được đổi thành tên khác thì `person.name` sẽ lỗi vì biến `person` không còn tồn tại, do đó sẽ phải sửa lại code ở nhiều chỗ.

{% hint style="info" %}
Tóm tắt

* **Khái niệm**: `this` là một từ khóa trong Javascript, tham chiếu đến đối tượng mà nó thuộc về, với giá trị phụ thuộc vào ngữ cảnh sử dụng.
* **This tham chiếu tới đối tượng mà nó thuộc về**:
  * Khi `this` được sử dụng bên trong một phương thức gọi qua một đối tượng, nó tham chiếu chính xác đến đối tượng đó.
  * **Ví dụ cụ thể**: Sử dụng `this` trong phương thức `getFullName` của đối tượng `person` để trả về tên đầy đủ.
* **Lợi ích của `this`**: Tăng cường khả năng tái sử dụng và bảo trì code, làm cho code dễ quản lý và hiểu hơn thông qua việc cung cấp phương thức linh hoạt truy cập đối tượng hiện hành.
{% endhint %}
