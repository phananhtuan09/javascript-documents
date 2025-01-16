# Tìm hiểu Symbol.toPrimitive, valueOf() và toString()

Mục lục

* [Symbol.toPrimitive](tim-hieu-symbol.toprimitive-valueof-va-tostring.md#symbol.toprimitive)
* [Object.prototype.valueOf](tim-hieu-symbol.toprimitive-valueof-va-tostring.md#object.prototype.valueof)
* [Object.prototype.toString](tim-hieu-symbol.toprimitive-valueof-va-tostring.md#object.prototype.tostring)
* [Ứng dụng](tim-hieu-symbol.toprimitive-valueof-va-tostring.md#ung-dung)
* [Thứ tự thực thi](tim-hieu-symbol.toprimitive-valueof-va-tostring.md#thu-tu-thuc-thi)

### Symbol.toPrimitive

Trong JavaScript, `Symbol.toPrimitive` là một phương thức chuyển đổi một đối tượng thành giá trị nguyên thủy. Trong tất cả các thuật toán ép kiểu (type coercion), nếu đối tượng có thuộc tính `Symbol.toPrimitive`, phương thức này sẽ được ưu tiên sử dụng để chuyển đổi đối tượng thành giá trị nguyên thủy, trước khi chuyển sang các phương thức `valueOf()` hoặc `toString()` .

**Cú pháp**

Được định nghĩa như một phương thức của đối tượng:

```javascript
const object = {
  [Symbol.toPrimitive](hint) {
   // Write logic here
  },
};
```

**Tham số**

1. `hint` : Giá trị của `hint` có thể là `"number"`, `"string"`, hoặc `"default"`, tương ứng với kiểu dữ liệu mà JavaScript mong đợi trong quá trình chuyển đổi.

**Giá trị trả về**

Trả về kết quả chuyển đổi.

**Ngoại lệ**

* Ném lỗi `TypeError` nếu hàm không trả về giá trị nguyên thuỷ(primitive).

**Ví dụ**

```javascript
// An object without Symbol.toPrimitive property.
const obj1 = {};
console.log(+obj1); // NaN
console.log(`${obj1}`); // "[object Object]"
console.log(obj1 + ""); // "[object Object]"

// An object with Symbol.toPrimitive property.
const obj2 = {
  [Symbol.toPrimitive](hint) {
    if (hint === "number") {
      return 10;
    }
    if (hint === "string") {
      return "hello";
    }
    return true;
  },
};
console.log(+obj2); // 10        — hint is "number"
console.log(`${obj2}`); // "hello"   — hint is "string"
console.log(obj2 + ""); // "true"    — hint is "default"
```

* `"default"` thường được sử dụng khi JavaScript không rõ ràng cần kiểu gì (ví dụ khi dùng toán tử `+` mà một trong hai toán hạng là đối tượng).

***

### Object.prototype.valueOf

Phương thức `valueOf()`  trả về giá trị của đối tượng đang gọi nó.

**Cú pháp**

```javascript
valueOf()
```

**Tham số**

Không

**Giá trị trả về**

Giá trị nguyên thủy hoặc đối tượng được trả về bởi phương thức `valueOf()` (thường là chính đối tượng nếu không được ghi đè).

**Ví dụ:**

1. Ví dụ sử dụng valueOf để lấy giá trị của đối tượng

```javascript
const obj = {
  name: "John",
};
const num = 123;
const str = "Hello";
const arr = [1, 2, 3];
console.log(obj.valueOf()); // { name: 'John' }
console.log(num.valueOf()); // 123
console.log(str.valueOf()); // 'Hello'
console.log(arr.valueOf()); // [ 1, 2, 3 ]
```

2. Ví dụ sử dụng valueOf với phương thức tuỳ chỉnh

```javascript
const obj = {
  name: "John",
  valueOf() {
    return this.name;
  },
};
console.log(obj.valueOf()); // John
```

* `valueOf` được ghi đè để trả về giá trị của thuộc tính `name`. Điều này cho phép đối tượng có thể được sử dụng như một giá trị nguyên thủy trong các biểu thức liên quan

***

### Object.prototype.toString

Phương thức `toString()` trả về một chuỗi biểu diễn đối tượng, và thường được sử dụng khi cần chuyển đổi đối tượng sang chuỗi.

**Cú pháp**

```javascript
toString()
```

**Tham số**

Theo mặc định, `toString()` không có tham số. Tuy nhiên, các đối tượng kế thừa từ Object có thể ghi đè lên nó bằng các triển khai riêng của chúng có tham số

**Giá trị trả về**

Một chuỗi đại diện cho đối tượng.

**Ví dụ:**

1. Ví dụ sử dụng toString để chuyển đổi các giá trị sang chuỗi

```javascript
console.log({}.toString()); // [object Object]
console.log("text".toString()); // text
console.log((123).toString()); // 123
console.log([1, 2, 3].toString()); // 1,2,3
```

* "`toString` mặc định của đối tượng trả về chuỗi dạng `[object Object]`, biểu thị rằng đây là một đối tượng thông thường."

2. Ví dụ về dùng toString với phương thức tuỳ chỉnh

```javascript
const obj = {
  name: "John",
  toString() {
    return this.name;
  },
};
console.log(obj.toString()); // John
```

***

### Ứng dụng

**Symbol.toPrimitive**

* Phương thức này cho phép tùy chỉnh cách đối tượng được chuyển đổi thành giá trị nguyên thủy, phù hợp với các yêu cầu cụ thể.

**valueOf**

* Phương thức này chủ yếu được JavaScript tự động gọi khi đối tượng cần được chuyển đổi thành giá trị nguyên thủy trong ngữ cảnh số học.

**toString**

* Chuyển đổi sang chuỗi.
* JavaScript thường tự động gọi phương thức này khi đối tượng cần được chuyển đổi thành chuỗi, đặc biệt trong các ngữ cảnh liên quan đến chuỗi (như template literals hoặc toán tử nối chuỗi).

***

### Thứ tự thực thi

Như đã nói ở phần Ứng dụng javascript sẽ gọi phương thức Symbol.toPrimitive, valueOf, toString khi cần ép kiểu thứ tự thực thi như sau:

* Ép kiểu số: \[Symbol.toPrimitive]\("number") → valueOf() → toString()
* Ép kiểu chuỗi: \[Symbol.toPrimitive]\("string") → toString() → valueOf()
* Ép kiểu nguyên thủy: \[Symbol.toPrimitive]\("default") → valueOf() → toString()&#x20;

Quy trình thực thi như sau:

1. Gọi phương thức Symbol.toPrimitive nếu nó tồn tại. Ném lỗi `TypeError` nếu `Symbol.toPrimitive` không trả giá trị nguyên thuỷ.
2. Nếu `Symbol.toPrimitive` không được định nghĩa, Javascript sẽ gọi `valueOf` hoặc `toString` theo thứ tự như trên sơ đồ.
3. Gọi phương thức còn lại nếu phương thức ở bước hai không trả giá trị nguyên thuỷ.
4. &#x20;Ném lỗi `TypeError` nếu cả hai phương thức `valueOf` và `toString` đều không trả về giá trị nguyên thuỷ.

Ví dụ về ép kiểu nguyên thủy

1. Ví dụ khi sử dụng Symbol.toPrimitive

```javascript
const obj = {
  [Symbol.toPrimitive](hint) {
    if (hint === "default") {
      return "hello";
    }
  },
};
console.log(obj + " test"); // hello test
```

* Ở ví dụ trên ta định nghĩa phương thức `Symbol.toPrimitive` trong đối tượng obj nên javascript sẽ dùng chính phương thức này để ép kiểu nên kết quả log là "hello test".

2. Ví dụ khi sử dụng valueOf và toString

```javascript
const obj = {
  valueOf() {
    return "valueOf";
  },
  toString() {
    return "toString";
  },
};
console.log(obj + " test"); // valueOf test

const obj2 = {
  valueOf() {
    return {};
  },
  toString() {
    return "toString";
  },
};
console.log(obj2 + " test"); // toString test
```

* Ở ví dụ này ta không định nghĩa `Symbol.toPrimitive` nên sẽ ưu tiên gọi hàm `valueOf` nên log 1 ỉn ra "valueOf test", còn ở log 2 phương thức `valueOf` không trả về kiểu nguyễn thuỷ nên phương thức `toString` được gọi nên kết quả là "toString test"
* Lưu ý: Nếu ở phương thức `valueOf` hoặc `toString` ta không return thì ta nhận được chuỗi "undefined"

Ví dụ về ép kiểu chuỗi

```javascript
const obj = {
  valueOf() {
    return "valueOf";
  },
  toString() {
    return "toString";
  },
};
console.log(`${obj}`); // toString
console.log(String(obj)); // toString
```

* Template literals (`${}`) hoặc `String(obj)` đều mặc định yêu cầu chuỗi, vì vậy `toString` sẽ được gọi trước.

{% hint style="info" %}
Tóm tắt

Trong JavaScript, ba phương thức chính liên quan đến việc chuyển đổi đối tượng thành giá trị nguyên thủy là `Symbol.toPrimitive`, `valueOf`, và `toString`. Mỗi phương thức có vai trò và thứ tự ưu tiên khác nhau trong các ngữ cảnh ép kiểu.

1. **Symbol.toPrimitive**
   * Là phương thức ưu tiên hàng đầu khi đối tượng cần chuyển đổi thành giá trị nguyên thủy.
   * Chấp nhận một tham số `hint` để chỉ định kiểu dữ liệu mong muốn (`"number"`, `"string"`, hoặc `"default"`).
   * Phải trả về một giá trị nguyên thủy, nếu không sẽ ném lỗi `TypeError`.
2. **valueOf**
   * Trả về giá trị nguyên thủy của đối tượng, nếu có.
   * Mặc định, hầu hết các đối tượng đều trả về chính đối tượng đó.
   * Thường được sử dụng trong các phép toán số học hoặc khi cần giá trị không phải chuỗi.
3. **toString**
   * Trả về chuỗi biểu diễn của đối tượng.
   * Được gọi khi đối tượng cần chuyển đổi thành chuỗi, chẳng hạn trong template literals hoặc các phép nối chuỗi.

**Thứ tự thực thi**

* Khi ép kiểu số: `Symbol.toPrimitive("number")` → `valueOf()` → `toString()`.
* Khi ép kiểu chuỗi: `Symbol.toPrimitive("string")` → `toString()` → `valueOf()`.
* Khi ép kiểu mặc định: `Symbol.toPrimitive("default")` → `valueOf()` → `toString()`.

**Ứng dụng**

* `Symbol.toPrimitive`: Tùy chỉnh logic ép kiểu.
* `valueOf`: Chủ yếu được gọi tự động bởi JavaScript trong ngữ cảnh số học.
* `toString`: Được sử dụng phổ biến nhất để chuyển đổi đối tượng thành chuỗi.
{% endhint %}
