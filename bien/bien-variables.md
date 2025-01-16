# Biến (Variables)

Mục lục

* [Biến là gì?](bien-variables.md#bien-la-gi)
* [Cách khai báo biến](bien-variables.md#cach-khai-bao-bien)
* [Lưu trữ và cập nhật giá trị](bien-variables.md#luu-tru-va-cap-nhat-gia-tri)
* [Nguyên tắc đặt tên biến](bien-variables.md#nguyen-tac-dat-ten-bien)
* [Lỗi thường gặp](bien-variables.md#loi-thuong-gap)

### Biến là gì?

Biến trong JavaScript dùng để lưu trữ dữ liệu. Giống như hộp “gạo” trong cửa hàng của bác Sơn, mỗi biến có một tên duy nhất và chứa một giá trị cụ thể.

***

### Cách khai báo biến

Có ba cách để khai báo biến trong JavaScript:

* `var`: Được sử dụng trong JavaScript cũ, có phạm vi rộng.
* `let`: Có phạm vi hẹp hơn, chỉ tồn tại trong khối code gần nhất.
* `const`: Giống như let nhưng giá trị không thể thay đổi sau khi được gán.

```javascript
var storeName = 'Cửa hàng bác Sơn';
let riceQuantity = 100;
const storeAddress = '123 đường ABC';
```

***

### Lưu trữ và cập nhật giá trị

Biến có thể được gán và thay đổi giá trị:

```javascript
let riceQuantity = 100;
riceQuantity = 150; // Cập nhật số lượng gạo

let storeName = 'Cửa hàng tạp hóa';
storeName = 'Cửa hàng bác Sơn'; // Cập nhật tên cửa hàng
```

Trường hợp cập nhật giá trị của một biến đã được khai báo với `const` sẽ dẫn đến lỗi trong JavaScript. Biến khai báo với `const` được dùng để định nghĩa những giá trị không thay đổi trong suốt quá trình chạy chương trình.

Hãy xem xét ví dụ sau:

```javascript
const storeAddress = '123 đường ABC';
storeAddress = '456 đường XYZ'; // TypeError: Assignment to constant variable.
```

Khi chạy đoạn code trên, JavaScript sẽ báo lỗi (_TypeError: Assignment to constant variable._), vì bạn đang cố gắng gán một giá trị mới cho một biến `const`, điều này không được phép trong JavaScript.

> _“TypeError: Assignment to constant variable” là “Lỗi kiểu: Gán giá trị cho biến hằng số”._

Điều này cho thấy tầm quan trọng của việc hiểu rõ sự khác biệt giữa `let`và `const` khi khai báo biến trong JavaScript. Sử dụng `const` cho những giá trị bạn biết chắc chắn sẽ không thay đổi trong suốt quá trình chạy chương trình, như địa chỉ cố định của cửa hàng trong ví dụ trên.

***

### Nguyên tắc đặt tên biến

Trong JavaScript, việc đặt tên biến là một phần quan trọng của việc viết code sáng sủa và dễ bảo trì. Đây là một số nguyên tắc và _best practices_ khi đặt tên biến:

* **Sử dụng tiếng Anh**: tiếng Anh được coi là ngôn ngữ chuẩn trong lập trình. Mã nguồn viết bằng tiếng Anh dễ dàng được hiểu bởi lập trình viên trên toàn thế giới.
* **Rõ ràng và mô tả ý nghĩa**: Tên biến phải mô tả rõ nghĩa và mục đích sử dụng của nó.
  * Ví dụ: Để lưu tuổi của người dùng, thay vì chỉ dùng `age` thì hãy dùng `userAge` bởi vì nó rõ ràng hơn.
* **Sử dụng camelCase**: Trong JavaScript, quy ước chung là sử dụng camelCase cho tên biến.
  * Ví dụ: `customerName` cho tên khách hàng và `totalAmount` cho tổng số tiền, thay vì `CustomerName` và `TotalAmount` hay `customer_name` và `total_amount`.
* **Phân biệt chữ hoa, chữ thường**: Ví dụ biến `a` và `A` là hai biến khác nhau. Hãy luôn tuân thủ quy ước đặt tên biến để hạn chế những nhầm lẫn do chữ hoa, chữ thường gây ra.
* **Không bắt đầu bằng số**: Tên biến không bắt đầu bằng số.
  * Ví dụ: Sử dụng `year2023` thay vì `2023year`.
* **Không sử dụng từ khóa của JavaScript**: Không dùng các từ khoá của JavaScript làm tên biến.
  * Ví dụ: `userCount` thay vì `const` hoặc `let`.
* **Độ dài tên biến phù hợp**: Tên biến nên có độ dài phù hợp, không quá ngắn hoặc quá dài.
  * Ví dụ: `inventoryList` thay vì chỉ `inv` hoặc `listOfProductsInInventory`.

***

### Lỗi thường gặp

* Đặt tên biến không rõ ràng, không mô tả chính xác nội dung lưu trữ.
* Khai báo biến trùng tên với biến đã tồn tại.
* Nhầm lẫn giữa `let` và `const`.
* Sử dụng `var` trong các dự án mới mà không cần thiết.

***

{% hint style="info" %}
Tóm tắt

* **Biến như hộp đựng**: Biến trong JavaScript tương tự như các hộp đựng trong cửa hàng tạp hóa, được đặt tên và lưu trữ dữ liệu.
* **Khai báo biến**: Sử dụng `var`, `let`, và `const` để khai báo biến, với mỗi loại có phạm vi và tính chất riêng. Ngày nay, không nên dùng `var` cho các dự án mới nữa.
* **Gán và cập nhật giá trị**: Có thể thay đổi giá trị của biến với `let` và `var`, nhưng không thể thay đổi giá trị của biến `const`.
* **Đặt tên biến**: Sử dụng tiếng Anh, camelCase, tránh từ khóa JavaScript và số ở đầu tên. Tên biến cần rõ ràng và mô tả ý nghĩa. Tên biến có phân biệt chữ HOA và thường, ví dụ biến `a` và biến `A` sẽ là hai biến khác nhau.
* **Lỗi thường gặp**: Gặp lỗi khi sử dụng `let` và `const` không đúng cách, hoặc đặt tên biến không chính xác, quên khai báo biến, khai báo biến trùng với biến đã tồn tại.
{% endhint %}

