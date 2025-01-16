# Pass by value và Pass by reference

Mục lục

* [Pass by value là gì?](pass-by-value-va-pass-by-reference.md#pass-by-value-la-gi)
* [Pass by reference là gì?](pass-by-value-va-pass-by-reference.md#pass-by-reference-la-gi)
* [Trong JavaScript chỉ có Pass by value](pass-by-value-va-pass-by-reference.md#trong-javascript-chi-co-pass-by-value)
  * [Tại sao có sự nhầm lẫn rằng JavaScript có Pass by reference?](pass-by-value-va-pass-by-reference.md#tai-sao-co-su-nham-lan-rang-javascript-co-pass-by-reference)

### Pass by value là gì?

Pass by value (truyền theo giá trị) là khái niệm mô tả cách một biến được truyền vào hàm. Khi một biến được truyền bằng cách pass by value, giá trị của biến đó được sao chép và bản sao này được truyền vào hàm dưới dạng tham số. Điều này có nghĩa là khi gán lại giá trị của tham số bên trong hàm sẽ không làm ảnh hưởng tới biến gốc bên ngoài hàm.

**Cách hoạt động của Pass by value:**

* Khi bạn truyền một biến vào một hàm, giá trị của biến đó được sao chép và bản sao này được sử dụng trong hàm.
* Vì chỉ có bản sao của giá trị được truyền vào, nên khi gán lại tham số bên trong hàm sẽ không ảnh hưởng đến giá trị của biến ban đầu bên ngoài hàm.

**Ví dụ:**

```javascript
function changeValue(y) {
    y = 20;
    console.log(y); // 20
}

let x = 10;

changeValue(x);

console.log(x); // 10
```

**Giải thích:**

* Biến `x` có giá trị ban đầu là `10`.
* Khi `x` được truyền vào hàm `changeValue`, một bản sao của biến `x` được truyền vào tham số `y` của hàm. Cách thức tạo bản sao này tương tự như `let y = x`.
* Bên trong hàm, `y` được gán lại với giá trị `20`, và điều này chỉ ảnh hưởng đến bản sao, không ảnh hưởng đến biến `x` ban đầu.
* Kết quả là, sau khi hàm kết thúc, giá trị của `x` bên ngoài hàm vẫn là `10`.

**Tóm lại:**

* Pass by value nghĩa là truyền một bản sao của giá trị vào trong hàm.
* Gán lại tham số trong hàm không ảnh hưởng đến biến gốc bên ngoài hàm.

> **Lưu ý:** trong JavaScript chỉ có **pass by value**. Một số người cho rằng JavaScript có **pass by reference** cho kiểu object (bao gồm cả array, function, v.v) thì đó là một sự nhầm lẫn. Mình sẽ làm rõ điều này ở phần số 3 trong bài học này.

Tiếp theo, chúng ta cùng tìm hiểu xem một ngôn ngữ có **pass by reference** sẽ có đặc điểm như thế nào nhé.

***

### Pass by reference là gì?

Pass by reference (truyền theo tham chiếu) là một khái niệm mô tả cách một biến được truyền vào hàm. Khi một biến được truyền bằng cách pass by reference, thay vì truyền giá trị của biến đó, một tham chiếu (hoặc địa chỉ bộ nhớ) đến biến gốc được truyền vào hàm. Điều này có nghĩa là bất kỳ thay đổi nào đối với tham số trong hàm sẽ ảnh hưởng trực tiếp đến biến gốc bên ngoài hàm ngay lập tức.

> Bởi trong JavaScript hoàn toàn là **pass by value** nên mình sẽ lấy ví dụ cho _Pass by reference_ bằng ngôn ngữ lập trình PHP, một ngôn ngữ có **pass by reference**.

**Cách hoạt động của Pass by reference trong PHP:**

Trong PHP, khi bạn truyền một biến vào một hàm bằng cách sử dụng tham chiếu (sử dụng cú pháp `&`), tham số hàm sẽ nhận được một tham chiếu đến biến gốc. Điều này có nghĩa là trong hàm có thể trực tiếp thay đổi giá trị của biến gốc, và thay đổi này sẽ được phản ánh ngay lập tức ở biến bên ngoài hàm.

**Ví dụ:**

```php
<?php
function changeValue(&$y) {
    $y = 20;
    echo $y; // 20
}

$x = 10;

changeValue($x);

echo $x; // 20
```

**Giải thích:**

* Trước khi gọi hàm `changeValue`:
  * Biến `$x` được khởi tạo với giá trị `10`.
* Khi truyền `$x` vào hàm `changeValue` bằng tham chiếu:
  * Tham số `$y` trong hàm `changeValue` nhận tham chiếu đến biến `$x`. Điều này có nghĩa là `$y` và `$x` trỏ đến cùng một địa chỉ bộ nhớ, nơi đang lưu trữ giá trị `10`.
* Trong hàm `changeValue`:
  * Khi bạn thay đổi giá trị của `$y` thành `20`, giá trị của `$x` cũng bị thay đổi thành `20` vì `$y` là tham chiếu đến `$x`.
* Sau khi gọi hàm:
  * Giá trị của `$x` bên ngoài hàm đã bị thay đổi thành `20`.

**Tóm lại:**

Pass by reference cho phép bạn truyền một biến vào hàm sao cho hàm đó có thể thay đổi giá trị của biến gốc. Điều này có nghĩa là bất kỳ thay đổi nào đối với tham số bên trong hàm sẽ trực tiếp ảnh hưởng đến biến được truyền vào từ bên ngoài hàm.

***

### Trong JavaScript chỉ có Pass by value

Trong JavaScript, mọi giá trị truyền vào hàm đều được truyền theo kiểu pass by value. Điều này có nghĩa là khi bạn truyền một biến vào một hàm, JavaScript sẽ luôn tạo ra một bản sao giá trị của biến đó và truyền bản sao này vào hàm.

#### Tại sao có sự nhầm lẫn rằng JavaScript có Pass by reference?

Sự nhầm lẫn này thường xuất phát từ việc truyền một object từ bên ngoài vào hàm, sau đó bên trong hàm thực hiện các thay đổi thuộc tính trên object nhận được, những thay đổi này được phản ánh thông qua biến gốc ngoài hàm. Điều này tạo cảm giác giống như tham chiếu của biến gốc được truyền trực tiếp vào hàm vậy. Tuy nhiên, thực chất JavaScript chỉ sao chép giá trị của biến (lúc này là một tham chiếu tới object) và truyền vào hàm, chứ không truyền tham chiếu tới biến gốc vào hàm.

**Ví dụ:** Thay đổi thuộc tính của object bên trong hàm, object bên ngoài hàm cũng thay đổi.

```javascript
function changeValue(obj) {
  obj.name = 'Bob';
}

let person = {
  name: 'John'
};

changeValue(person);

console.log(person); // {name: 'Bob'}
```

Trong ví dụ này, thay đổi thuộc tính `obj.name = 'Bob'` ở trong hàm dẫn tới sự thay đổi kết quả trên biến `person` bên ngoài hàm, điều này có thể tạo ra cảm giác giống như pass by reference, nhưng thực chất JavaScript vẫn chỉ pass by value.

Điểm mấu chốt để kết luận rằng đây không phải là **pass by reference** bởi khi gán một giá trị mới cho `obj` thì biến `person` bên ngoài hàm không bị ảnh hưởng. Bởi pass by value, nghĩa là tham số trong hàm chỉ là bản sao, nên việc gán lại bản sao sẽ không ảnh hưởng tới bản gốc.

**Ví dụ:** Gán lại tham số trong hàm, biến ngoài hàm không bị ảnh hưởng.

```javascript
function changeValue(obj) {
  obj = {
    name: 'Bob'
  };
}

let person = {
  name: 'John'
};

changeValue(person);

console.log(person); // {name: 'John'}
```

Nếu là **pass by reference** thì việc gán lại `obj` bên trong hàm sẽ làm biến `person` ở ngoài hàm cũng sẽ thay đổi theo ngay lập tức. Bởi với pass by reference, thay vì tạo bản sao của biến gốc, thì tham chiếu tới biến gốc được truyền vào hàm, nên việc gán lại tham số trong hàm sẽ làm thay đổi biến bên ngoài hàm ngay lập tức.

> _Các bạn nhớ xem thật kỹ video nhé, bởi vì trong video mình sử dụng các ví dụ minh họa trực quan sẽ giúp các bạn hiểu bài hơn. Tuy nhiên, đây vẫn là một kiến thức khó, vì vậy hãy xem lại nhiều lần và dành thời gian để suy ngẫm cho tới khi hiểu các bạn nhé!_

{% hint style="info" %}
Tóm tắt

* **Khái niệm Pass by Value**: Pass by value là khi một biến được truyền vào hàm, giá trị của biến đó được sao chép và bản sao này được sử dụng trong hàm dưới dạng tham số. Khi gán giá trị mới cho tham số trong hàm sẽ không làm thay đổi giá trị của biến gốc bên ngoài hàm.
* **Khái niệm Pass by Reference**: Pass by reference là khi một tham chiếu (địa chỉ bộ nhớ) đến biến gốc được truyền vào hàm dưới dạng tham số. Khi gán lại giá trị của tham số này thì ngay lập tức giá trị của biến gốc bên ngoài hàm cũng thay đổi theo.
* **JavaScript truyền mọi thứ theo kiểu Pass by Value**: Trong JavaScript, dù làm việc với các kiểu dữ liệu phức tạp như object hay array, tất cả đều được truyền theo pass by value. Tuy nhiên, giá trị truyền vào là một tham chiếu đến vị trí của object trong bộ nhớ Heap, dẫn đến việc thay đổi thuộc tính của object trong hàm sẽ làm thay đổi object gốc bên ngoài.
  * **Lý do gây nhầm lẫn về Pass by Reference trong JavaScript**: Khi bạn thay đổi thuộc tính của một object trong hàm, sự thay đổi này cũng xuất hiện trên object gốc bên ngoài hàm. Điều này có thể làm bạn nghĩ rằng JavaScript sử dụng pass by reference, nhưng thực tế nó vẫn chỉ sao chép giá trị của biến gốc vào hàm (pass by value), bởi vì lúc này giá trị của biến gốc lại là một tham chiếu tới object được lưu ở Heap, nên bất cứ thay đổi nào trên thuộc tính của tham số bên trong hàm cũng được phản ánh thông qua biến gốc bên ngoài hàm.
  * **Điểm mấu chốt để biết JavaScript không có pass by reference**: Khi bạn gán lại tham số bên trong hàm bằng một giá trị mới, biến gốc bên ngoài sẽ không thay đổi. Điều này chứng tỏ rằng JavaScript không có pass by reference.
{% endhint %}
