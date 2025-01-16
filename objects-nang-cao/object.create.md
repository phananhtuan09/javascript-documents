# Object.create()

Phương thức `Object.create()` tạo một đối tượng mới bằng cách sử dụng một đối tượng hiện có làm **nguyên mẫu** (prototype) của đối tượng mới được tạo.

**Cú pháp**

```javascript
Object.create(proto)
Object.create(proto, propertiesObject)
```

***

**Tham số**

1. **proto**
   * Đối tượng được chỉ định làm prototype của đối tượng mới.
   * Phải là một đối tượng hoặc `null`. Nếu không, sẽ ném lỗi `TypeError`.
2. **`propertiesObject`** _(Không bắt buộc)_
   * Nếu được cung cấp (và không phải `undefined`), đây là một đối tượng chứa các mô tả thuộc tính (property descriptors).
   * Các thuộc tính này sẽ được thêm vào đối tượng mới, tương tự như cách sử dụng `Object.defineProperties()`.

***

**Giá trị trả về**

Một đối tượng mới với:

* **Prototype** được chỉ định bởi `proto`.
* **Thuộc tính** được thêm vào từ `propertiesObject` (nếu có).

***

**Ngoại lệ**

* Ném lỗi `TypeError` nếu `proto` không phải là một đối tượng hoặc `null`.

***

**Ví dụ:**

1. Sử dụng `Object.create` với prototype

```javascript
const personPrototype = {
  getName() {
    console.log(this.name);
  },
};

const person = Object.create(personPrototype);
person.name = "John";
person.getName(); // John
```

* Đối tượng `person` kế thừa từ `personPrototype` nên có thể sử dụng phương thức `getName`.
* `personPrototype` nằm trong chuỗi prototype của `person`(person vẫn sẽ có Object.prototype và Function.prototype).

2. Sử dụng `Object.create` với `proto` là `null`

```javascript
const person = Object.create(null);
console.log(person); // {}
console.log(Object.getPrototypeOf(person)); // null
```

* Khi sử dụng Object.create với tham số đầu tiên là null thì đối tượng tạo ra sẽ là đối tượng rỗng và không có prototype

3. Sử dụng `Object.create` với `propertiesObject`

```javascript
const personPrototype = {
  greet() {
    console.log(`Hello, my name is ${this.name}`);
  },
};

// Tạo một đối tượng mới với prototype và định nghĩa các thuộc tính
const person = Object.create(personPrototype, {
  name: {
    value: "John Doe",
    writable: true, // Có thể sửa đổi
    enumerable: true, // Hiển thị khi lặp qua
    configurable: true, // Có thể thay đổi hoặc xóa
  },
  age: {
    value: 30,
    writable: false, // Không thể sửa đổi
    enumerable: true, // Hiển thị khi lặp qua
    configurable: false, // Không thể thay đổi hoặc xóa
  },
});

console.log(person.name); // John Doe
console.log(person.age); // 30

// Thay đổi thuộc tính `name`
person.name = "Jane Smith";
console.log(person.name); // Jane Smith

// Thử thay đổi thuộc tính `age`
person.age = 40;
console.log(person.age); // 30 (không thay đổi vì `writable: false`)

// Sử dụng phương thức từ prototype
person.greet(); // Hello, my name is Jane Smith

// Liệt kê các thuộc tính
console.log(Object.keys(person)); // ['name', 'age']
```

* `name` và `age` được định nghĩa với các thuộc tính kiểm soát (`writable`, `enumerable`, `configurable`).
* `person` kế thừa phương thức `greet` từ `personPrototype`.

***

**Ứng dụng**

* **Tạo đối tượng kế thừa từ prototype có sẵn:**\
  Giúp chia sẻ các phương thức hoặc thuộc tính mà không cần tạo lớp (class).
* **Tạo đối tượng không có prototype (`null`):**\
  Hữu ích cho việc tạo các đối tượng sạch sẽ không bị can thiệp bởi các phương thức từ `Object.prototype`.

{% hint style="info" %}
Tóm tắt

* **Công dụng**: Tạo đối tượng kế thừa từ một prototype cụ thể.
*   **Cú pháp**:

    ```javascript
    Object.create(proto, propertiesObject);
    ```
* **Tham số chính**:
  * `proto`: Đối tượng dùng làm prototype (hoặc `null` nếu không muốn có prototype).
  * `propertiesObject` (tuỳ chọn): Định nghĩa chi tiết các thuộc tính của đối tượng.
* **Trả về**: Một đối tượng mới với prototype và thuộc tính được chỉ định.
{% endhint %}
