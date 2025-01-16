# Làm việc với Object cơ bản

Mục lục

* [Destructuring (Phân rã)](lam-viec-voi-object-co-ban.md#destructuring-phan-ra)
* [Enhanced object literals](lam-viec-voi-object-co-ban.md#enhanced-object-literals)
  * [Property shorthand (Viết tắt thuộc tính)](lam-viec-voi-object-co-ban.md#property-shorthand-viet-tat-thuoc-tinh)
  * [Method shorthand (Viết tắt phương thức)](lam-viec-voi-object-co-ban.md#method-shorthand-viet-tat-phuong-thuc)
  * [Computed property names (Tên thuộc tính động)](lam-viec-voi-object-co-ban.md#computed-property-names-ten-thuoc-tinh-dong)

### Destructuring (Phân rã)

Cho phép bạn trích xuất nhiều thuộc tính từ một object vào các biến riêng biệt một cách ngắn gọn.

Ví dụ đơn giản:

```javascript
const person = {
  name: 'John',
  age: 30
};
const { name, age } = person;

console.log(name); // John
console.log(age); // 30
```

Đối với cấu trúc Object phức tạp hơn:

```javascript
const course = {
  title: 'JavaScript Pro',
  info: {
    url: 'https://fullstack.edu.vn',
    description: 'JavaScript Basic, Advanced.',
    keywords: 'js basic, js advanced'
  }
};

const {
  title,
  info: {
    keywords: topics
  }
} = course;

console.log(title); // JavaScript Pro
console.log(topics); // js basic, js advanced
```

***

### Enhanced object literals

_Enhanced object literals_ cung cấp một cách viết ngắn gọn và mạnh mẽ hơn cho object literals. Tính năng này bao gồm một số cải tiến để giúp việc khai báo và làm việc với object trở nên dễ dàng và trực quan hơn.

#### Property shorthand (Viết tắt thuộc tính)

Cho phép bạn khai báo các thuộc tính của object mà không cần phải viết tên và giá trị của thuộc tính nếu chúng giống nhau. Điều này làm cho code trở nên ngắn gọn hơn.

```javascript
const name = "John Doe";
const age = 30;

const person = { name, age };

console.log(person); // {name: "John Doe", age: 30}
```

#### Method shorthand (Viết tắt phương thức)

Cung cấp cú pháp ngắn gọn hơn để định nghĩa các phương thức trong object literals.

```javascript
const dog = {
  name: "Scooby Doo",
  speak() {
    console.log('Go go...');
  }
};

dog.speak(); // Go go...
```

#### Computed property names (Tên thuộc tính động)

Cho phép bạn sử dụng biểu thức trong ngoặc vuông `[]` để đặt tên cho các thuộc tính của object.

Ví dụ:

```javascript
const property = 'lastName';
const person = {
  firstName: 'John',
  [property]: 'Smith'
};

console.log(person.lastName); // Smith
```

Các tính năng trên giúp giảm đáng kể lượng code cần viết khi làm việc với _Object literals_.

{% hint style="info" %}
Tóm tắt

* **Destructuring (Phân rã)**: Cho phép trích xuất thuộc tính từ object vào biến một cách ngắn gọn. Hỗ trợ cả object đơn giản và phức tạp.
  * **Ví dụ đơn giản**: `const { name, age } = person;` trích xuất `name` và `age` từ `person`.
  * **Ví dụ phức tạp**: `const { title, info: { keywords: topics } } = course;` trích xuất `title` và `keywords` từ `course`, đổi tên `keywords` thành `topics`.
* **Enhanced object literals**: Cung cấp cách viết ngắn gọn và mạnh mẽ cho object literals.
  * **Property shorthand (Viết tắt thuộc tính)**: Cho phép khai báo thuộc tính mà không cần phải viết tên và giá trị nếu chúng giống nhau. `const person = { name, age };`
  * **Method shorthand (Viết tắt phương thức)**: Cung cấp cú pháp ngắn gọn để định nghĩa phương thức. `const dog = { name: "Scooby", speak() { console.log('Go go...'); } };`
  * **Computed property names (Tên thuộc tính động)**: Sử dụng biểu thức trong ngoặc vuông `[]` để đặt tên cho thuộc tính. `const person = { [property]: 'Smith' };`
{% endhint %}

