# Hiểu về khái niệm Hoisting

### Hoisting là gì?

Hoisting trong Javascript là một hành vi mặc định của Javascript, nơi mà các khai báo biến (`var`, `let`, `const`) và hàm (`function` declarations) được đưa lên đầu phạm vi của chúng trước khi code được thực thi.

Hoisting chỉ dùng được cho declaration function và khai báo biến var

Hành vi hoisting let và const:

* Các khai báo của chúng được chuyển lên đầu phạm vi của chúng trong giai đoạn biên dịch, tương tự như var.&#x20;
* Tuy nhiên, chúng không được khởi tạo cho đến khi định nghĩa của chúng trong mã được thực thi.
* Khoảng thời gian giữa lúc bắt đầu phạm vi khối và dòng mà biến được khai báo và khởi tạo được gọi là **Temporal Dead Zone.**
* Nếu bạn cố gắng truy cập biến trong khoảng thời gian này, nó sẽ ném ra lỗi ReferenceError.

#### **So sánh giữa `var`, `let` và `const`**

| Đặc điểm                | `var`                              | `let` / `const`                            |
| ----------------------- | ---------------------------------- | ------------------------------------------ |
| Hoisting                | Có                                 | Có                                         |
| Khởi tạo khi hoisting   | `undefined`                        | Không (TDZ áp dụng)                        |
| Truy cập trước khai báo | Được phép (giá trị là `undefined`) | **Không được phép** (lỗi `ReferenceError`) |
| Phạm vi                 | Phạm vi hàm                        | Phạm vi khối (block scope)                 |
