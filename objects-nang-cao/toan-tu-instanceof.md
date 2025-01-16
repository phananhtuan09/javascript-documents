# Toán tử instanceof

Toán tử `instanceof` được sử dụng để kiểm tra xem thuộc tính `prototype` của hàm tạo (constructor) có xuất hiện ở bất kỳ đâu trong chuỗi nguyên mẫu (`prototype chain`) của một đối tượng hay không. Giá trị trả về là kiểu boolean (`true` hoặc `false`).

**Cú pháp**

```javascript
object instanceof constructor
```

***

**Tham số**

1. `object`: Đối tượng cần kiểm tra.
2. `constructor`: Contructor để kiểm tra.

***

**Giá trị trả về**

* Trả về `true` nếu thuộc tính `prototype` của hàm khởi tạo xuất hiện trong chuỗi nguyên mẫu (`prototype chain`) của đối tượng.
* Trả về `false` trong các trường hợp khác.

***

**Ngoại lệ**

* Ném lỗi `TypeError` nếu:
  * `constructor` không phải là một đối tượng.
  * `constructor` không có phương thức `Symbol.hasInstance` và không phải là một hàm.

***

**Ví dụ:**

1. Kiểm tra với hàm khởi tạo

```javascript
function Person(name) {
  this.name = name;
}

const john = new Person("John");

console.log(john instanceof Person); // true
console.log(john instanceof Object); // true
```

* `john` được tạo bởi hàm khởi tạo `Person`, nên `john instanceof Person` trả về `true`.
* Trong JavaScript, tất cả các đối tượng đều kế thừa từ `Object.prototype`, vì vậy `john instanceof Object` cũng trả về `true`.

2. Kiểm tra với class

```javascript
class Animal {
  constructor(name) {
    this.name = name;
  }
}

class Dog extends Animal {
  constructor(name, breed) {
    super(name);
    this.breed = breed;
  }
}

const buddy = new Dog("Buddy", "Golden Retriever");

console.log(buddy instanceof Dog); // true
console.log(buddy instanceof Animal); // true
console.log(buddy instanceof Object); // true
```

* `buddy` là một thể hiện của `Dog`, và `Dog` kế thừa từ `Animal`.
* Vì vậy, `buddy instanceof Dog` và `buddy instanceof Animal` đều trả về `true`.
* Tất cả các đối tượng trong JavaScript đều kế thừa từ `Object`.

3. Kiểm tra với các đối tượng nguyên thủy

```javascript
const str = new String("Hello");
console.log(str instanceof String); // true
console.log(str instanceof Object); // true

const num = 42;
console.log(num instanceof Number); // false (42 là giá trị nguyên thủy)
```

* `str` được tạo từ `String` nên `instanceof String` trả về `true`.
* `num` là một giá trị nguyên thủy, không phải đối tượng, nên `instanceof Number` trả về `false`.

4. Kiểm tra với `null` và `undefined`

```javascript
console.log(null instanceof Object); // false
console.log(undefined instanceof Object); // false
```

* `null` và `undefined` không phải là đối tượng, nên `instanceof` luôn trả về `false`.

***

**Ứng dụng**

* **Kiểm tra kiểu của đối tượng**
  * `instanceof` được sử dụng để xác định một đối tượng có phải là thể hiện của một lớp hoặc hàm khởi tạo cụ thể không.
  *   **Ví dụ**:

      ```javascript
      if (user instanceof Admin) {
        console.log("Người dùng là quản trị viên.");
      }
      ```
* **Xử lý kế thừa trong lập trình hướng đối tượng**
  * Xác định mối quan hệ kế thừa giữa các lớp.
  *   **Ví dụ**:

      ```javascript
      if (animal instanceof Mammal) {
        console.log("Đây là động vật có vú.");
      }
      ```
* **Gỡ lỗi và xử lý lỗi**
  * Phân biệt các lỗi tùy chỉnh trong chương trình.
  *   **Ví dụ**:

      ```javascript
      try {
        throw new TypeError("Lỗi cú pháp");
      } catch (error) {
        if (error instanceof TypeError) {
          console.error("Đây là lỗi kiểu dữ liệu:", error.message);
        }
      }
      ```
* **Quản lý kiểu dữ liệu trong hàm đa hình**
  * Xử lý các loại dữ liệu khác nhau trong cùng một hàm.
  *   **Ví dụ**:

      ```javascript
      function handleInput(input) {
        if (input instanceof Array) {
          console.log("Dữ liệu là một mảng:", input);
        } else if (input instanceof String) {
          console.log("Dữ liệu là một chuỗi:", input);
        }
      }
      ```
* **Xác minh kiểu dữ liệu đặc biệt trong thư viện**
  * `instanceof` được sử dụng để kiểm tra các kiểu dữ liệu đặc biệt, ví dụ như `Promise`.
  *   **Ví dụ**:

      ```javascript
      const promise = new Promise(() => {});
      console.log(promise instanceof Promise); // true
      ```

{% hint style="info" %}
Tóm tắt

* Toán tử `instanceof` kiểm tra mối quan hệ giữa đối tượng và constructor dựa trên chuỗi nguyên mẫu (`prototype chain`).
* Thường được sử dụng trong lập trình hướng đối tượng và kiểm tra kiểu dữ liệu.
* Không áp dụng được với `null` và `undefined`.
* Hữu ích trong các ứng dụng thực tế như kiểm tra kiểu đối tượng, xử lý kế thừa, và gỡ lỗi.
{% endhint %}
