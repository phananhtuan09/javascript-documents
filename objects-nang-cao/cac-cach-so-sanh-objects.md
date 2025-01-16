# Các cách so sánh objects

Mục lục

* [So sánh objects là gì?](cac-cach-so-sanh-objects.md#so-sanh-objects-la-gi)
* [Các cách so sánh objects](cac-cach-so-sanh-objects.md#cac-cach-so-sanh-objects)
  * [Dùng toán tử === để so sánh tham chiếu](cac-cach-so-sanh-objects.md#dung-toan-tu-de-so-sanh-tham-chieu)
  * [Sử dụng JSON.stringify để so sánh nội dung](cac-cach-so-sanh-objects.md#su-dung-json.stringify-de-so-sanh-noi-dung)
  * [Dùng thư viện bên ngoài như Lodash](cac-cach-so-sanh-objects.md#dung-thu-vien-ben-ngoai-nhu-lodash)

### So sánh objects là gì?

Trong JavaScript, objects không được so sánh trực tiếp dựa trên nội dung của chúng như các kiểu dữ liệu nguyên thủy (ví dụ như số hoặc chuỗi). Thay vào đó, khi so sánh hai objects, JavaScript so sánh các tham chiếu đến các đối tượng đó. Nếu hai biến tham chiếu đến cùng một object, chúng mới được coi là bằng nhau.

Ví dụ:

```javascript
let car1 = { make: 'Toyota', model: 'Corolla' };
let car2 = { make: 'Toyota', model: 'Corolla' };
let car3 = car1;

// Khác tham chiếu
console.log(car1 === car2); // false

// Cùng tham chiếu
console.log(car1 === car3); // true
```

So sánh objects thường được dùng để xác định xem hai biến có tham chiếu đến cùng một vị trí trong bộ nhớ không, hoặc để kiểm tra xem hai object có chứa cùng một cặp khóa/giá trị không.

***

### Các cách so sánh objects

#### Dùng toán tử === để so sánh tham chiếu

So sánh hai biến object xem chúng có cùng tham chiếu đến một object không.

```javascript
let person1 = { name: "Alice" };
let person2 = person1;

console.log(person1 === person2); // true
```

#### &#x20;Sử dụng JSON.stringify để so sánh nội dung

```javascript
let student1 = { id: 1, name: "Bob" };
let student2 = { id: 1, name: "Bob" };

console.log(JSON.stringify(student1) === JSON.stringify(student2)); // true
```

Tuy nhiên, điểm yếu của phương pháp này là khi các thuộc tính và giá trị giống nhau, nhưng thứ tự khác nhau sẽ cho kết quả `false`. Khi đó, chúng ta có thể sử dụng _đệ quy_ để so sánh sâu (_deep compare_). Để đơn giản, ta có thể sử dụng `_.isEqual()` của thư viện _Lodash_.

#### Dùng thư viện bên ngoài như Lodash

Sử dụng hàm `_.isEqual()` từ thư viện _Lodash_ để so sánh sâu (_deep compare_) giữa các objects.

```html
<script src="https://cdn.jsdelivr.net/npm/lodash@4.17.21/lodash.min.js"></script>
<script>
  let obj1 = { part: { id: 10, name: 'Top' } };
  let obj2 = { part: { id: 10, name: 'Top' } };

  console.log(_.isEqual(obj1, obj2)); // true
</script>
```

{% hint style="info" %}
Tóm tắt

* **Khái niệm so sánh objects trong JavaScript**: Trong JavaScript, khi so sánh hai objects, JavaScript kiểm tra xem hai biến có cùng tham chiếu đến một object hay không. Nếu không, mặc dù các thuộc tính và giá trị bên trong có thể giống nhau, chúng vẫn không được coi là bằng nhau.
  * **Ví dụ minh hoạ**: Hai biến `car1` và `car2` có cùng nội dung nhưng không cùng tham chiếu, nên `car1 === car2` trả về `false`. Biến `car3` và `car1` cùng tham chiếu đến một đối tượng, nên `car1 === car3` trả về `true`.
* **Phương pháp so sánh nội dung của objects**:
  * **Dùng JSON.stringify để so sánh**: Chuyển đổi object thành chuỗi JSON và so sánh các chuỗi này. Tuy nhiên, cách này có hạn chế khi thứ tự các thuộc tính trong object khác nhau có thể dẫn đến kết quả `false` ngay cả khi nội dung giống hệt nhau.
  * **Sử dụng thư viện như Lodash để so sánh sâu**: Hàm `_.isEqual()` cho phép so sánh chi tiết và chính xác hơn giữa các objects bằng cách xem xét từng cặp khóa/giá trị một cách đệ quy, bất chấp thứ tự của chúng trong object.
{% endhint %}

