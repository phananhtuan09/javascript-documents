# Xử lý chuỗi có chứa Emoji

### Code Unit là gì?

Chuỗi JavaScript là chuỗi các giá trị 16 bit (gọi là code unit) biểu diễn các ký tự từ Mã hóa `UTF-16`.

Về mặt kỹ thuật, mỗi "element" trong chuỗi không phải là một "ký tự" mà là một "code unit".

Nếu chuỗi chỉ chứa các ký tự `ASCII` thì mỗi “code unit” tương ứng với một ký tự.

Nếu chuỗi chứa một ký tự có Codepoint ≥ 2^16 (ví dụ: 😂), ký tự đó là 2 đơn vị mã, do đó chiếm nhiều hơn 1 index. Kết quả của các string function có thể không như mong đợi.

Ví dụ: Sự khác biệt giữa đơn vị kí tự và code unit

```javascript
console.log("😂".length === 2); // true
// 😂
// name: FACE WITH TEARS OF JOY
// codepoint in decimal: 128514
```

Sau đây là ví dụ về phương thức `String.prototype.slice` cho kết quả không mong muốn.

```javascript
// we want to take the substring abc

console.log(("😂abc".slice(1) === "abc") === false); // true
// wrong

// 😂
// name: FACE WITH TEARS OF JOY
// codepoint in decimal: 128514
```

### Một số giải thích về Code Unit

Chuỗi và ký tự trong JavaScript được dựa trên tiêu chuẩn `Unicode`, phiên bản 5.1 hoặc mới hơn.\
Trong Unicode, mỗi ký tự có một integer ID riêng, gọi là **Codepoint**.\
Unicode quy định một số tiêu chuẩn mã hóa, trong đó phổ biến nhất là:\
• **UTF-8**\
• **UTF-16**

**Mã hóa** (Encoding) là một tiêu chuẩn chuyển đổi một ký tự thành một chuỗi byte.

Mã hóa UTF-16 chuyển đổi mỗi ký tự thành **2 byte hoặc 4 byte**, tùy thuộc vào ký tự đó. (Mỗi 2 byte được coi là một đơn vị, gọi là **code unit**.)

* Với các ký tự có **codepoint** nhỏ hơn 2^16, mã hóa của ký tự đó trong UTF-16 là 2 byte.
* Ngược lại, nếu **codepoint** lớn hơn hoặc bằng 2^16, mã hóa sẽ là 4 byte.

JavaScript định nghĩa các phần tử của chuỗi là một dãy các giá trị 2 byte của các ký tự được mã hóa trong UTF-16. Cụ thể:

* Đầu tiên, mã hóa ký tự trong chuỗi thành các bit theo UTF-16 (nhận được 2 hoặc 4 byte).
* Sau đó, nhóm mỗi 2 byte thành một **code unit**.
* **Index 0** là đơn vị 2 byte đầu tiên, Index **1** là đơn vị 2 byte thứ hai, v.v.

Điều này có nghĩa là, khi một chuỗi chứa các ký tự có **codepoint ≥ 2^16** kết quả của bất kỳ phương thức chuỗi nào có thể sẽ không như mong đợi, bởi vì index không tương ứng với ký tự thực tế.

### Xử lý chuỗi có chứa emoji

Sử dụng phương thức `Array.from` để xử lý chuỗi

Ví dụ:

```javascript
// Tách chuỗi emoji ra khỏi chuỗi - sử dụng phương thức slice bình thường
console.log("😂abc".slice(1)) // "�abc"
// Tách chuỗi emoji ra khỏi chuỗi - sử dụng phương thức Array.from trước khi dùng slice
console.log(Array.from("😂abc").slice(1).join('')) // "abc"
```
