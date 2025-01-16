# Đệm thêm chuỗi với padStart và padEnd

Mục lục

* [padStart](dem-them-chuoi-voi-padstart-va-padend.md#padstart)
  * [Cú pháp](dem-them-chuoi-voi-padstart-va-padend.md#cu-phap)
  * [Tham số](dem-them-chuoi-voi-padstart-va-padend.md#tham-so)
  * [Giá trị trả về](dem-them-chuoi-voi-padstart-va-padend.md#gia-tri-tra-ve)
  * [Ví dụ](dem-them-chuoi-voi-padstart-va-padend.md#vi-du)
* [padEnd](dem-them-chuoi-voi-padstart-va-padend.md#padend)
  * [Cú pháp](dem-them-chuoi-voi-padstart-va-padend.md#cu-phap-1)
  * [Tham số](dem-them-chuoi-voi-padstart-va-padend.md#tham-so-1)
  * [Giá trị trả về](dem-them-chuoi-voi-padstart-va-padend.md#gia-tri-tra-ve-1)
  * [Ví dụ](dem-them-chuoi-voi-padstart-va-padend.md#vi-du-1)

### padStart

Phương thức `padStart()` thêm phần đệm vào **đầu** một chuỗi bằng một chuỗi khác (có thể lặp lại, nếu cần) cho đến khi chuỗi đạt đến độ dài được chỉ định.

#### Cú pháp

```javascript
padStart(targetLength)
padStart(targetLength, padString)
```

#### Tham số

* **`targetLength`**:
  * Độ dài mong muốn của chuỗi sau khi thêm phần đệm.
  * Nếu giá trị nhỏ hơn hoặc bằng độ dài của chuỗi gốc (`str.length`), chuỗi sẽ được trả về nguyên trạng.
* **`padString`** _(tùy chọn)_:
  * Chuỗi dùng để đệm vào chuỗi gốc.
  * Nếu chuỗi này quá dài so với `targetLength`, nó sẽ bị cắt bớt từ cuối.
  * Mặc định là khoảng trắng `" "` (U+0020).

#### Giá trị trả về

Chuỗi mới có độ dài bằng `targetLength` với phần đệm được thêm vào đầu chuỗi gốc.

#### Ví dụ

```javascript
"abc".padStart(10); // "       abc"
"abc".padStart(10, "foo"); // "foofoofabc"
"abc".padStart(6, "123465"); // "123abc"
"abc".padStart(8, "0"); // "00000abc"
"abc".padStart(1); // "abc"
```

***

### padEnd

Phương thức `padEnd()` thêm phần đệm vào **cuối** một chuỗi bằng một chuỗi khác (có thể lặp lại, nếu cần) cho đến khi chuỗi đạt đến độ dài được chỉ định.

#### Cú pháp

```javascript
padEnd(targetLength)
padEnd(targetLength, padString)
```

#### Tham số

* **`targetLength`**:
  * Độ dài mong muốn của chuỗi sau khi thêm phần đệm.
  * Nếu giá trị nhỏ hơn hoặc bằng độ dài của chuỗi gốc (`str.length`), chuỗi sẽ được trả về nguyên trạng.
* **`padString`** _(tùy chọn)_:
  * Chuỗi dùng để đệm vào chuỗi gốc.
  * Nếu chuỗi này quá dài so với `targetLength`, nó sẽ bị cắt bớt:
    * Đối với ngôn ngữ viết từ trái sang phải (LTR), phần dư sẽ bị cắt từ **trái**.
    * Đối với ngôn ngữ viết từ phải sang trái (RTL), phần dư sẽ bị cắt từ **phải**.
  * Mặc định là khoảng trắng `" "` (U+0020).

#### Giá trị trả về

Chuỗi mới có độ dài bằng `targetLength` với phần đệm được thêm vào cuối chuỗi gốc.

#### Ví dụ

```javascript
"abc".padEnd(10); // "abc       "
"abc".padEnd(10, "foo"); // "abcfoofoof"
"abc".padEnd(6, "123456"); // "abc123"
"abc".padEnd(1); // "abc"
```

{% hint style="info" %}
**Tóm tắt**

Phương thức `padStart` và `padEnd` trong JavaScript được sử dụng để thêm phần đệm (padding) vào một chuỗi cho đến khi đạt được độ dài mong muốn.

* **`padStart`**: Thêm phần đệm vào **đầu** chuỗi.
* **`padEnd`**: Thêm phần đệm vào **cuối** chuỗi.\
  Cả hai phương thức đều hỗ trợ tùy chọn chuỗi đệm (`padString`) và có giá trị mặc định là khoảng trắng `" "` nếu không được chỉ định.
{% endhint %}
