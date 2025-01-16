# Phương thức bind, call và apply

Mục lục

* [Phương thức bind là gì?](phuong-thuc-bind-call-va-apply.md#phuong-thuc-bind-la-gi)
* [Phương thức call là gì?](phuong-thuc-bind-call-va-apply.md#phuong-thuc-call-la-gi)
* [Phương thức apply là gì?](phuong-thuc-bind-call-va-apply.md#phuong-thuc-apply-la-gi)
* [Tại sao cần sử dụng call và apply?](phuong-thuc-bind-call-va-apply.md#tai-sao-can-su-dung-call-va-apply)
* [Các cách làm việc với bind, call và apply](phuong-thuc-bind-call-va-apply.md#cac-cach-lam-viec-voi-bind-call-va-apply)
  * [Sử dụng bind để tạo hàm cố định this](phuong-thuc-bind-call-va-apply.md#su-dung-bind-de-tao-ham-co-dinh-this)
  * [Sử dụng call để mượn phương thức từ đối tượng khác](phuong-thuc-bind-call-va-apply.md#su-dung-call-de-muon-phuong-thuc-tu-doi-tuong-khac)
  * [Sử dụng apply để truyền mảng đối số cho hàm](phuong-thuc-bind-call-va-apply.md#su-dung-apply-de-truyen-mang-doi-so-cho-ham)

### Phương thức bind là gì?

Phương thức `bind` tạo ra một hàm mới mà khi được gọi, từ khóa `this` sẽ được tham chiếu tới bởi đối tượng đã cho.

**Cú pháp:**

```js
const newFunc = oldFunction.bind(thisArg[, arg1[, arg2[, ...]]]);
```

**Ví dụ:**

```javascript
const person = {
    firstName: 'John',
    greet: function(greeting) {
        console.log(`${greeting}, my name is ${this.firstName}`);
    }
};

const greetJohn = person.greet.bind(person, 'Hello');

greetJohn();
// Hello, my name is John
```

Phương thức `bind` rất hữu ích khi bạn cần một hàm luôn được gọi với cùng một giá trị của `this`, đặc biệt trong các trường hợp như:

* Chỉ định rõ ràng ngữ cảnh `this` cho hàm.
* “Mượn” các phương thức từ đối tượng khác.

**Ưu điểm:**

* Dễ dàng kiểm soát ngữ cảnh `this` của hàm.
* Giảm thiểu lỗi liên quan đến ngữ cảnh `this`.

**Bài toán và ví dụ:**

**Bài toán:** Chỉ định rõ ràng ngữ cảnh cho hàm.

```javascript
const app = {
  log(data) {
    console.log(data);
  },
  batch(list) {
    for (let item of list) {
      this.log(item);
    }
  }
};

const batch = app.batch.bind(app);

batch([
  { id: 1, name: 'Item 1' },
  { id: 2, name: 'Item 2' },
  { id: 3, name: 'Item 3' },
]);
// {id: 1, name: "Item 1"}
// {id: 2, name: "Item 2"}
// {id: 3, name: "Item 3"}
```

**Bài toán:** “Mượn hàm” từ đối tượng khác.

```javascript
const person1 = {
  firstName: 'John',
  greet() {
    console.log(`Hello, my name is ${this.firstName}`);
  }
};
const person2 = {
  firstName: 'Bob'
};

const person2Greet = person1.greet.bind(person2);

person2Greet();
// Hello, my name is Bob
```

***

### Phương thức call là gì?

Tương tự như `bind` ở điểm chỉ định ngữ cảnh `this`, `call` khác `bind` ở điểm thay vì trả về một hàm mới thì `call` sẽ thực hiện gọi hàm ngay.

**Cú pháp:**

```js
myFunction.call(thisArg, [, arg1[, arg2[, ...]]]);
```

**Ví dụ:**

```javascript
function introduce(greeting, punctuation) {
    console.log(`${greeting}, my name is ${this.firstName}${punctuation}`);
}

const person = { firstName: 'John' };

introduce.call(person, 'Hello', '!');
// Hello, my name is John!
```

***

### Phương thức apply là gì?

Tương tự như `call`, điểm khác là `apply` nhận các đối số dưới dạng một mảng.

**Cú pháp:**

```js
myFunction.apply(thisArg, [argsArray]);
```

**Ví dụ:**

```javascript
function introduce(greeting, punctuation) {
    console.log(`${greeting}, my name is ${this.firstName}${punctuation}`);
}

const person = { firstName: 'John' };

introduce.apply(person, ['Hi', '.']);
// Hi, my name is John.
```

***

### Tại sao cần sử dụng call và apply?

Phương thức `call` và `apply` rất hữu ích khi bạn cần gọi một hàm ngay với một giá trị this cụ thể và các đối số tùy ý.

**Ưu điểm khi dùng:**

* Linh hoạt trong việc truyền các đối số cho hàm.
* Thích hợp cho các trường hợp khi bạn không biết trước số lượng đối số.

**Bài toán và ví dụ:**

**Bài toán:** Sử dụng hàm với ngữ cảnh `this` khác nhau và các đối số khác nhau.

<pre class="language-javascript"><code class="lang-javascript">function introduce(greeting, punctuation) {
    console.log(`${greeting}, my name is ${this.firstName}${punctuation}`);
}

const person1 = { firstName: 'John' };
const person2 = { firstName: 'Bob' };

introduce.call(person1, 'Hello', '!');
introduce.call(person2, 'Hey', '.');
// Hello, my name is John!
<strong>// Hey, my name is Bob.
</strong></code></pre>

**Bài toán:** Chuyển mảng đối số cho hàm.

```javascript
function introduce(greeting, punctuation) {
    console.log(`${greeting}, my name is ${this.firstName}${punctuation}`);
}

const person = { firstName: 'John' };
const args = ['Hi', '!'];

introduce.apply(person, args);
// Hi, my name is John!
```

***

### Các cách làm việc với bind, call và apply

#### Sử dụng bind để tạo hàm cố định this

```javascript
const person = {
    firstName: 'John',
    greet: function(greeting) {
        console.log(`${greeting}, my name is ${this.firstName}`);
    }
};

const greetJohn = person.greet.bind(person);

greetJohn('Hello');
// Hello, my name is John
```

#### Sử dụng call để mượn phương thức từ đối tượng khác

```javascript
const person1 = {
    firstName: 'John',
    greet: function() {
        console.log(`Hello, my name is ${this.firstName}`);
    }
};

const person2 = { firstName: 'Bob' };

person1.greet.call(person2);
// Hello, my name is Bob
```

#### Sử dụng apply để truyền mảng đối số cho hàm

```javascript
function sum(a, b, c) {
    return a + b + c;
}

const numbers = [1, 2, 3];
const result = sum.apply(null, numbers);

console.log(result);
// 6
```

> Phương thức bind, call, apply không thể chỉ định this cho arrow function

{% hint style="info" %}
Tóm tắt

* **Phương thức bind**:
  * Phương thức `bind` tạo ra một hàm mới với từ khóa `this` được tham chiếu tới bởi đối tượng đã cho.
  *   **Ví dụ**:

      ```js
      const greetJohn = person.greet.bind(person, 'Hello');
      greetJohn(); // Output: "Hello, my name is John"
      ```
  * **Ứng dụng**:
    * Chỉ định ngữ cảnh `this` cố định cho hàm.
    * Mượn phương thức từ đối tượng khác.
* **Phương thức call**:
  * Phương thức `call` gọi hàm ngay lập tức với ngữ cảnh `this` được chỉ định và các đối số cụ thể.
  *   **Ví dụ**:

      ```js
      introduce.call(person, 'Hello', '!');
      ```
  * **Ứng dụng**:
    * Gọi hàm với ngữ cảnh `this` cụ thể và các đối số tùy ý.
* **Phương thức apply**:
  * Phương thức `apply` tương tự như `call`, nhưng nhận các đối số dưới dạng một mảng.
  *   **Ví dụ**:

      ```js
      introduce.apply(person, ['Hi', '.']);
      ```
  * **Ứng dụng**:
    * Truyền mảng đối số cho hàm.
{% endhint %}
