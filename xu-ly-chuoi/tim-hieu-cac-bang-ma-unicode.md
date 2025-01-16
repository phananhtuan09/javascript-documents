# Tìm hiểu các bảng mã Unicode

Mục lục

* [Bảng phân biệt các định dạng Unicode](tim-hieu-cac-bang-ma-unicode.md#bang-phan-biet-cac-dinh-dang-unicode)
* [Bảng liệt kê kích thước của các ký tự Unicode](tim-hieu-cac-bang-ma-unicode.md#bang-liet-ke-kich-thuoc-cua-cac-ky-tu-unicode)

### Bảng phân biệt các định dạng Unicode

Các loại mã hóa UTF-8, UTF-16, và UTF-32 là các phương pháp để lưu trữ và biểu diễn ký tự Unicode. Mỗi loại mã hóa có cách sử dụng số byte khác nhau tùy vào loại ký tự, giúp tối ưu hóa cho các ứng dụng cụ thể như web, ngôn ngữ Đông Á, hoặc xử lý dữ liệu.

<table data-header-hidden><thead><tr><th></th><th width="171"></th><th></th><th></th></tr></thead><tbody><tr><td>Mã hóa</td><td>Kích thước byte</td><td>Đặc điểm</td><td>Ứng dụng phổ biến</td></tr><tr><td>UTF-8</td><td>1 đến 4 byte</td><td>Tiết kiệm dung lượng, đặc biệt với ký tự ASCII</td><td>Phổ biến nhất, dùng cho web, email</td></tr><tr><td>UTF-16</td><td>2 hoặc 4 byte</td><td>Tốt cho các ngôn ngữ như tiếng Trung, Nhật</td><td>Dùng trong Java, Windows</td></tr><tr><td>UTF-32</td><td>4 byte</td><td>Dễ dùng nhưng tốn nhiều bộ nhớ</td><td>Ít dùng, chủ yếu trong xử lý bên trong hệ thống</td></tr></tbody></table>

> 8 bit = 1 byte

**Ý nghĩa và ứng dụng:**

* **UTF-8:** Tiết kiệm bộ nhớ cho văn bản ASCII, phù hợp với các trang web và ứng dụng cần hiệu suất cao.
* **UTF-16:** Hiệu quả cho các ngôn ngữ như Trung Quốc, Nhật Bản, nơi ký tự lớn thường xuyên xuất hiện.
* **UTF-32:** Dễ dùng trong xử lý dữ liệu nội bộ với ký tự cố định (không phải ghép từ nhiều “mảnh” lại như UTF-8 và UTF-16), nhưng tốn nhiều bộ nhớ nên ít được sử dụng trong thực tế.

***

### &#x20;Bảng liệt kê kích thước của các ký tự Unicode

Các loại mã hóa UTF-8, UTF-16, và UTF-32 là những cách khác nhau để biểu diễn ký tự Unicode, với mỗi loại sử dụng số lượng byte khác nhau để lưu trữ ký tự. Mỗi mã hóa có những ưu và nhược điểm riêng, được sử dụng tùy theo yêu cầu cụ thể của từng ứng dụng như tối ưu dung lượng hay đơn giản trong xử lý ký tự.

<table data-header-hidden><thead><tr><th width="161"></th><th></th><th></th><th></th></tr></thead><tbody><tr><td>Mã hóa</td><td>Kích thước byte</td><td>Phạm vi ký tự</td><td>Ví dụ ký tự</td></tr><tr><td>UTF-8</td><td>1 byte</td><td>Ký tự ASCII (U+0000 đến U+007F)</td><td>A (U+0041), số 1 (U+0031)</td></tr><tr><td></td><td>2 byte</td><td>Ký tự từ U+0080 đến U+07FF</td><td>¢ (U+00A2), ß (U+00DF)</td></tr><tr><td></td><td>3 byte</td><td>Ký tự từ U+0800 đến U+FFFF</td><td>अ (U+0905), 中 (U+4E2D)</td></tr><tr><td></td><td>4 byte</td><td>Ký tự từ U+10000 đến U+10FFFF</td><td>𐍈 (U+10348), 😃 (U+1F603)</td></tr><tr><td>UTF-16</td><td>2 byte</td><td>Ký tự từ U+0000 đến U+FFFF</td><td>A (U+0041), 中 (U+4E2D)</td></tr><tr><td></td><td>4 byte</td><td>Ký tự từ U+10000 đến U+10FFFF</td><td>𐍈 (U+10348), 😃 (U+1F603)</td></tr><tr><td>UTF-32</td><td>4 byte</td><td>Tất cả các ký tự từ U+0000 đến U+10FFFF</td><td>A (U+0041), 中 (U+4E2D), 😃 (U+1F603)</td></tr></tbody></table>

**Giải thích:** `"U+XXXX"` là gì?

Mình lấy giá tị `"U+00A2"` để giải thích nhé: `"U+00A2"` là cách biểu diễn mã Unicode của một ký tự, trong trường hợp này là ký hiệu tiền tệ ¢ (ký hiệu cent). Trong đó:

* **U+:** Phần “U+” là cách thông báo rằng giá trị phía sau là mã Unicode.
* **00A2:** Đây là mã hex (hệ cơ số 16) đại diện cho ký tự ¢. Các số và chữ cái trong “00A2” tương ứng với một giá trị trong bảng mã Unicode.

**Ý nghĩa và ứng dụng:**

* **UTF-8:** Hiệu quả cho các ứng dụng web và các hệ thống sử dụng nhiều ký tự ASCII nhờ tiết kiệm dung lượng.
* **UTF-16:** Phù hợp với các ngôn ngữ chứa nhiều ký tự phức tạp như tiếng Trung và tiếng Nhật.
* **UTF-32:** Thích hợp cho xử lý dữ liệu nội bộ với kích thước ký tự cố định, nhưng tốn bộ nhớ hơn nên ít dùng trong các hệ thống thực tế.
