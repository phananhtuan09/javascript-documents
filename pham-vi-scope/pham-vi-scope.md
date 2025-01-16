# Phạm vi (Scope)

Mục lục

* [Phạm vi (Scope)](pham-vi-scope.md#pham-vi-scope)
  * [Phạm vi toàn cục (Global scope)](pham-vi-scope.md#pham-vi-toan-cuc-global-scope)
  * [Phạm vi hàm (Function scope)](pham-vi-scope.md#pham-vi-ham-function-scope)
  * [Phạm vi khối (Block scope)](pham-vi-scope.md#pham-vi-khoi-block-scope)
  * [Phạm vi module (Module scope)](pham-vi-scope.md#pham-vi-module-module-scope)
* [Lưu ý quan trọng](pham-vi-scope.md#luu-y-quan-trong)
  * [Mỗi hàm sẽ tạo ra một phạm vi mới](pham-vi-scope.md#moi-ham-se-tao-ra-mot-pham-vi-moi)
  * [Cách JavaScript tìm kiếm biến (Scope chain)](pham-vi-scope.md#cach-javascript-tim-kiem-bien-scope-chain)
  * [Hãy sử dụng let và const thay vì dùng var](pham-vi-scope.md#hay-su-dung-let-va-const-thay-vi-dung-var)
* [Sai lầm thường gặp](pham-vi-scope.md#sai-lam-thuong-gap)
  * [Sử dụng biến toàn cục khi không thực sự cần thiết](pham-vi-scope.md#su-dung-bien-toan-cuc-khi-khong-thuc-su-can-thiet)
  * [Hiểu nhầm về phạm vi của var, let, const](pham-vi-scope.md#hieu-nham-ve-pham-vi-cua-var-let-const)
  * [Không hiểu rõ phạm vi hàm](pham-vi-scope.md#khong-hieu-ro-pham-vi-ham)
* [Tóm tắt phạm vi và từ khóa khai báo](pham-vi-scope.md#tom-tat-pham-vi-va-tu-khoa-khai-bao)
  * [Bảng tóm tắt](pham-vi-scope.md#bang-tom-tat)
  * [Yếu tố cốt lõi](pham-vi-scope.md#yeu-to-cot-loi)
  * [Cách trả lời phỏng vấn](pham-vi-scope.md#cach-tra-loi-phong-van)

### Phạm vi (Scope)

Phạm vi là khu vực trong code nơi một biến có thể được truy cập và sử dụng. Hiểu về phạm vi bạn có thể phân biệt rõ ràng một biến hoặc hàm có thể truy cập và sử dụng ở những nơi nào trong code.

#### Phạm vi toàn cục (Global scope)

Một biến được khai báo ở ngoài mọi hàm và [_block_](https://javascript.fullstack.edu.vn/?id=208d287b-38d3-4bbc-b1e5-7b97aa75dcf8) (_khối code_) là một biến toàn cục. Nó có thể được truy cập và sử dụng từ bất kỳ đâu trong code, kể cả bên trong các hàm.

Ví dụ:

```js
let globalVar = "Tôi là cây toàn cục, nhìn thấy tôi từ mọi nơi!";

// Truy cập biến toàn cục từ bên ngoài hàm
console.log(globalVar); // Tôi là cây toàn cục, nhìn thấy tôi từ mọi nơi!

function checkGlobalVar() {
  // Truy cập được biến toàn cục từ bên trong hàm
  console.log(globalVar); // Tôi là cây toàn cục, nhìn thấy tôi từ mọi nơi!
}

checkGlobalVar();
```

> _Như là bầu trời xanh mênh mông, biến toàn cục là những biến được khai báo bên ngoài bất kỳ hàm và block nào, tự do và có thể truy cập từ mọi nơi._

#### Phạm vi hàm (Function scope)

Trong JavaScript, mỗi hàm tạo ra một phạm vi mới. Các biến được khai báo trong hàm (bao gồm cả các tham số của hàm) chỉ có thể được truy cập trong phạm vi của hàm đó.

Ví dụ:

```js
function funcGarden() {
  let localVar = "Tôi là cây cục bộ, chỉ nhìn thấy tôi trong phòng này!";
  console.log(localVar); // Tôi là cây cục bộ, chỉ nhìn thấy tôi trong phòng này!
}

funcGarden();

console.log(localVar); // Uncaught ReferenceError: localVar is not defined
```

**Trong trường hợp các hàm lồng nhau**: hàm con có thể truy cập và sử dụng các biến được khai báo ở các hàm cha, nhưng ở hàm cha sẽ không truy cập và sử dụng được các biến được khai báo trong hàm con.

Ví dụ:

```js
let globalVar = "Biến toàn cục";

function outerFunction() {
    let outerVar = "Biến ngoài";

    function innerFunction() {
        let innerVar = "Biến trong";

        console.log(innerVar); // Biến trong
        console.log(outerVar); // Biến ngoài
        console.log(globalVar); // Biến toàn cục
    }

    innerFunction();

    console.log(outerVar); // Biến ngoài
    // console.log(innerVar); // Uncaught ReferenceError: innerVar is not defined
}

outerFunction();

console.log(globalVar); // Biến toàn cục
// console.log(outerVar); // Uncaught ReferenceError: outerVar is not defined
```

> _Giống như một căn phòng kín đáo, biến cục bộ chỉ tồn tại và truy cập được bên trong hàm mà nó được khai báo._

#### Phạm vi khối (Block scope)

Phạm vi khối có nghĩa là các biến được khai báo bên trong một khối code (thường là bên trong các dấu ngoặc nhọn `{}`) chỉ có thể truy cập được bên trong khối code đó.

Ví dụ:

```js
if (true) {
    let blockScopedVar = "Tôi chỉ tồn tại trong khối if này";
    console.log(blockScopedVar); // Tôi chỉ tồn tại trong khối if này
}

console.log(blockScopedVar); // Uncaught ReferenceError: blockScopedVar is not defined
```

Trường hợp sử dụng cú pháp rút gọn của `if-else` (_không sử dụng ngoặc nhọn `{}`_) thì mỗi nhánh của `if-else` vẫn là một khối code.

Ví dụ:

```js
if (true)
    let blockScopedVar = "Tôi chỉ tồn tại trong khối if này";

console.log(blockScopedVar); // Uncaught ReferenceError: blockScopedVar is not defined
```

Thậm chí bạn có thể sử dụng độc lập một cặp ngoặc nhọn `{}` để tạo ra một phạm vi khối.

Ví dụ:

```js
{
    let blockScopedVar = "Tôi chỉ tồn tại trong khối này";
    console.log(blockScopedVar); // Tôi chỉ tồn tại trong khối này
}

console.log(blockScopedVar); // Uncaught ReferenceError: blockScopedVar is not defined
```

> Trước ES6 (2015) JavaScript chỉ có 2 phạm vi là **Global scope** và **Function scope**. ES6 cung cấp thêm hai từ khóa `let` và `const` cho phép tạo biến có _phạm vi khối_, các biến được khai báo bên trong một khối `{}` sẽ không thể được truy cập từ bên ngoài khối.

#### Phạm vi module (Module scope)

Trong một module, biến, hàm, hoặc các thành phần khác mà bạn khai báo chỉ có thể truy cập và sử dụng trong chính module đó, trừ khi chúng được `export` để sử dụng ở nơi khác.

Để sử dụng modules trong trang web của bạn, thêm thuộc tính `type="module"` vào thẻ `script` trong HTML.

Ví dụ:

```html
<script type="module" src="main.js"></script>
```

`Export` các giá trị từ một module khác:

```js
// File: myModule.js
export const myVar = 1;
export function myFunction() {
  console.log("Hello world");
}
```

`Import` và sử dụng các giá trị được `export`:

```js
// File: main.js
import { myVar, myFunction } from './myModule.js';

console.log(myVar); // 1
myFunction(); // Hello world
```

Sử dụng modules giúp bạn tổ chức mã nguồn một cách hiệu quả, tách biệt logic và tái sử dụng mã giữa các file và dự án khác nhau.

> Phạm vi module xuất hiện khi bạn sử dụng ES6 Modules.

***

### Lưu ý quan trọng

#### Mỗi hàm sẽ tạo ra một phạm vi mới

rong JavaScript, mỗi hàm tạo ra một phạm vi mới. Các biến được khai báo trong hàm (bao gồm cả các tham số của hàm) chỉ có thể được truy cập trong phạm vi của hàm đó.

Ví dụ:

```js
// (1) Phạm vi toàn cục

function hamCha() {
  // (2) Phạm vi của hamCha

  function hamCon() {
    // (3) Phạm vi của hamCon
  }
}
```

> _Mỗi hàm sẽ tạo ra một phạm vi mới. Trong hàm con có thể truy cập và sử dụng các biến được khai báo ở các hàm cha, nhưng ở hàm cha sẽ không truy cập và sử dụng được các biến được khai báo trong hàm con._

#### Cách JavaScript tìm kiếm biến (Scope chain)

Scope Chain là chuỗi các phạm vi lồng nhau, nơi mỗi phạm vi có thể truy cập biến từ phạm vi bên ngoài của nó.

Khi một biến được truy cập, JavaScript sẽ tìm kiếm biến đó trong phạm vi hiện tại. Nếu không tìm thấy, nó sẽ tìm trong phạm vi ngoại cục tiếp theo và tiếp tục quá trình này cho đến khi tìm thấy biến hoặc đến phạm vi toàn cục.

Ví dụ:

```js
// (3) Tìm thấy biến myVar
let myVar = "Hello, tôi ở đây!"; // Biến toàn cục

function hamCha() {
  // (2) Tìm biến myVar trong phạm vi hamCha
  // Kết quả: không thấy => Tiếp tục tìm kiếm phạm vi ngoại cục

  function hamCon() {
    // (1) Tìm biến myVar trong phạm vi hamCon
    // Kết quả: không thấy => Tiếp tục tìm kiếm phạm vi ngoại cục
    console.log(myVar);
  }
  hamCon();
}

hamCha();
```

> Trong JavaScript, các biến khai báo ở phạm vi khác nhau dù đặt trùng tên vẫn hợp lệ, nó sẽ là các biến khác nhau và độc lập trong phạm vi của nó.

#### Hãy sử dụng let và const thay vì dùng var

Sử dụng `let` và `const` giúp hạn chế lỗi liên quan đến phạm vi. Vì `let` và `const` có phạm vi _block_, nên sẽ an toàn hơn về mặt phạm vi và giúp quản lý biến hiệu quả hơn.

Từ khoá `var` có thể đặt tên trùng (cái sau khi đè cái trước).

***

### Sai lầm thường gặp

#### Sử dụng biến toàn cục khi không thực sự cần thiết

Sử dụng biến toàn cục cho mọi trường hợp, kể cả khi không cần thiết làm tăng khả năng xung đột (_giữa tên biến và tên hàm_), dễ gây ra các lỗi không mong muốn và khó khăn trong quản lý dữ liệu trong chương trình.

#### Hiểu nhầm về phạm vi của var, let, const

Sử dụng `var` thay vì `let` hoặc `const` trong các block, dẫn đến việc biến có phạm vi rộng hơn so với mong muốn.

Ví dụ:

```js
if (true) {
  var x = "Tôi là biến var";
}

// Vẫn truy cập được x, dù nó nằm trong block if
console.log(x); // Tôi là biến var
```

**Hậu quả**: Biến `x` có phạm vi toàn cục, không giới hạn trong block `if`.

#### Không hiểu rõ phạm vi hàm

Sử dụng biến khai báo trong một hàm ở ngoài phạm vi hàm đó.

Ví dụ:

```js
function myFunction() {
  var y = "Tôi là biến cục bộ";
}
myFunction();
console.log(y); // Uncaught ReferenceError: y is not defined
```

**Hậu quả**: Gây lỗi không tìm thấy biến (`ReferenceError`) khi cố gắng truy cập biến cục bộ từ bên ngoài hàm.

***

### Tóm tắt phạm vi và từ khóa khai báo

#### Bảng tóm tắt

Bảng này cung cấp một cái nhìn tổng quan về cách các từ khóa khai báo ảnh hưởng đến phạm vi của biến hoặc hàm trong JavaScript.

| Loại phạm vi   | var | let | const | function |
| -------------- | --- | --- | ----- | -------- |
| Global Scope   | ✔️  | ✔️  | ✔️    | ✔️       |
| Function Scope | ✔️  | ✔️  | ✔️    | ✔️       |
| Block Scope    | ❌   | ✔️  | ✔️    | ❌\*      |
| Module Scope   | ✔️  | ✔️  | ✔️    | ✔️       |

_\* Trong Module, `function` cũng có phạm vi khối._

#### Yếu tố cốt lõi

* **Phụ thuộc vào nơi được khai báo:**
  * Phạm vi của biến hoặc hàm phụ thuộc vào nơi chúng được khai báo trong code.
* **Phụ thuộc vào tính chất của từ khóa khai báo:**
  * Cách biến hoặc hàm được quản lý phụ thuộc vào từ khóa được sử dụng để khai báo (`var`, `let`, `const`, `function`).

#### Cách trả lời phỏng vấn

Đối với cách khai báo biến hoặc hàm, chúng ta thường quan tâm đến phạm vi hẹp nhất mà chúng có thể tạo ra, nên cách nói dưới đây sẽ áp dụng cho câu trả lời khi đi phỏng vấn:

* `let` và `const`: Các biến được khai báo bằng `let` hoặc `const` có “phạm vi khối” (_block scope_). Điều này có nghĩa là chúng chỉ tồn tại và có thể được truy cập trong khối code mà chúng được khai báo. Một khối code là phần được bao bọc bởi cặp ngoặc nhọn `{}`.
* `var` và `function`: Ngược lại, biến được khai báo bằng `var` và hàm được khai báo bắt đầu với `function` có “phạm vi hàm” (_function scope_). Nghĩa là chúng có thể được truy cập từ bất kỳ nơi nào trong hàm mà chúng được định nghĩa.
* Tất cả các biến và hàm sẽ ở phạm vi toàn cục nếu chúng không nằm trong bất kỳ hàm, block, và module nào.

Nhận thức về sự khác biệt giữa các loại phạm vi này giúp bạn viết code chính xác và hiệu quả hơn, đồng thời tránh được các lỗi không mong muốn liên quan tới phạm vi.

{% hint style="info" %}
Tóm tắt

* **Phạm vi toàn cục (Global scope)**: Biến toàn cục giống như cây cối trong khu vườn, có thể nhìn thấy từ mọi nơi. Chúng được khai báo ngoài mọi hàm, khối code và module, và có thể truy cập từ bất kỳ đâu trong code.
* **Phạm vi hàm (Function scope)**: Mỗi hàm tạo ra phạm vi riêng của nó. Biến được khai báo trong hàm chỉ có thể truy cập trong hàm đó. Hàm con có thể truy cập biến của hàm cha nhưng ngược lại thì không.
* **Phạm vi khối (Block scope)**: Các biến được khai báo trong một khối (được bao bọc bởi `{}`) chỉ có thể truy cập trong khối đó. Điều này áp dụng với `let` và `const` từ phiên bản ES6.
* **Phạm vi module (Module scope)**: Từ ES6, modules giới hạn phạm vi biến, hàm, và các thành phần khác chỉ trong module đó, trừ khi được `export`.
* **Lưu ý quan trọng**: Mỗi hàm tạo ra phạm vi mới; scope chain cho phép truy cập biến từ phạm vi bên ngoài. Nên sử dụng `let` và `const` thay vì `var` để hạn chế lỗi liên quan đến phạm vi.
* **Sai lầm thường gặp**: Sử dụng biến toàn cục không cần thiết, hiểu nhầm phạm vi của `var`, `let`, `const`, và không nhận thức đúng về phạm vi hàm.
* **Bảng tóm tắt**: ([_Xem bảng tóm tắt phạm vi của các cách khai báo_](pham-vi-scope.md#bang-tom-tat)).
  * `let` và `const`: Các biến được khai báo bằng `let` hoặc `const` có “phạm vi khối” (_block scope_). Chúng chỉ tồn tại và có thể được truy cập trong khối code mà chúng được khai báo.
  * `var` và `function`: Ngược lại, biến được khai báo bằng `var` và hàm được khai báo bắt đầu với `function` có “phạm vi hàm” (_function scope_). Chúng có thể được truy cập từ bất kỳ nơi nào trong hàm mà chúng được định nghĩa.
  * Tất cả các biến và hàm sẽ ở phạm vi toàn cục nếu chúng không nằm trong bất kỳ hàm, block, và module nào.
{% endhint %}

