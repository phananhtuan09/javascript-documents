# Date() constructor

Theo mặc định javascript sử dụng múi giờ cúa trình duyệt để hiển thị output

Hàm tạo `Date()` tạo ra các đối tượng Date. Khi được gọi như một hàm, nó trả về một chuỗi biểu diễn thời gian hiện tại.

### Syntax

```javascript
new Date()
new Date(value)
new Date(dateString)
new Date(dateObject)

new Date(year, monthIndex)
new Date(year, monthIndex, day)
new Date(year, monthIndex, day, hours)
new Date(year, monthIndex, day, hours, minutes)
new Date(year, monthIndex, day, hours, minutes, seconds)
new Date(year, monthIndex, day, hours, minutes, seconds, milliseconds)

Date()
```

***

### Parameters

#### Không có parameter

Khi không có tham số nào được truyền, đối tượng Date mới được tạo sẽ đại diện cho ngày và giờ hiện tại tại thời điểm gọi.Timestamp trả về giống như khi gọi  `Date.now()`.

Ví dụ:

```javascript
new Date()
```

#### dateString hoặc timestamp&#x20;

* #### timestamp
  * Một số nguyên đại diện cho dấu thời gian (số mili-giây kể từ nửa đêm đầu tiên của ngày 1 tháng 1 năm 1970 theo giờ UTC — hay còn gọi là "epoch").
  * Ví dụ: `new Date(1737790862392)`
* dateString
  * Một chuỗi đại diện cho ngày tháng, được phân tích và diễn giải bằng thuật toán tương tự như **Date.parse()**
  * Ví dụ: `new Date("2022-03-25")`

#### dateObject

Một đối tượng Date hiện có. Điều này sẽ tạo ra một bản sao của đối tượng Date hiện tại với cùng ngày và giờ.&#x20;

#### Các giá trị thành phần ngày giờ riêng lẻ

Khi ít nhất có năm và tháng được cung cấp, dạng này của **Date()** sẽ trả về một đối tượng Date với các giá trị thành phần (năm, tháng, ngày, giờ, phút, giây và mili-giây) lấy từ các tham số sau đây. Bất kỳ trường nào bị thiếu sẽ được gán giá trị thấp nhất có thể (1 cho ngày và 0 cho các thành phần khác). Các giá trị tham số được đánh giá dựa trên múi giờ cục bộ, không phải UTC.&#x20;

Nếu bất kỳ tham số nào vượt quá giới hạn của nó, nó sẽ "dồn" sang thành phần cao hơn. Ví dụ:

* **new Date(1990, 12, 1)** sẽ trả về ngày 1 tháng 1 năm 1991.
* **new Date(2020, 5, 19, 25, 65)** sẽ trả về 2:05 sáng ngày 20 tháng 6 năm 2020.

Tương tự, nếu bất kỳ tham số nào bị thiếu, nó sẽ "mượn" từ thành phần cao hơn. Ví dụ:

* **new Date(2020, 5, 0)** sẽ trả về ngày 31 tháng 5 năm 2020.

#### Các tham số chi tiết:

* **year**\
  Giá trị nguyên đại diện cho năm. Các giá trị từ 0 đến 99 sẽ ánh xạ tới các năm từ 1900 đến 1999. Các giá trị khác là năm thực tế.
* **monthIndex**\
  Giá trị nguyên đại diện cho tháng, bắt đầu từ 0 cho tháng 1 đến 11 cho tháng 12.
* **day** _(Tùy chọn)_\
  Giá trị nguyên đại diện cho ngày trong tháng. Mặc định là 1.
* **hours** _(Tùy chọn)_\
  Giá trị nguyên từ 0 đến 23 đại diện cho giờ trong ngày. Mặc định là 0.
* **minutes** _(Tùy chọn)_\
  Giá trị nguyên đại diện cho phút. Mặc định là 0.
* **seconds** _(Tùy chọn)_\
  Giá trị nguyên đại diện cho giây. Mặc định là 0.
* **milliseconds** _(Tùy chọn)_\
  Giá trị nguyên đại diện cho mili-giây. Mặc định là 0.

***

### Giá trị trả về

Khi gọi **new Date()** (hàm khởi tạo **Date()**) sẽ trả về một đối tượng Date. Nếu gọi với chuỗi ngày không hợp lệ, hoặc nếu ngày được tạo ra có timestamp nhỏ hơn -8,640,000,000,000,000 hoặc lớn hơn 8,640,000,000,000,000 mili-giây, nó sẽ trả về một ngày không hợp lệ (một đối tượng Date mà phương thức **toString()** trả về `"Invalid Date"` và phương thức **valueOf()** trả về `NaN`).

Khi gọi hàm **Date()** (không dùng từ khóa `new`), nó sẽ trả về một chuỗi đại diện cho ngày và giờ hiện tại, giống hệt như **new Date().toString()**. Mọi tham số được truyền vào khi gọi hàm **Date()** (không có `new`) đều bị bỏ qua. Dù được gọi với chuỗi ngày không hợp lệ hay bất kỳ giá trị tùy ý nào, nó vẫn trả về chuỗi đại diện cho ngày và giờ hiện tại.
