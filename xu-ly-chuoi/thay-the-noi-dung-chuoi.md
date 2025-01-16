# Thay thế nội dung chuỗi

Mục lục

* [replace() là gì?](thay-the-noi-dung-chuoi.md#replace-la-gi)
* [replaceAll() là gì?](thay-the-noi-dung-chuoi.md#replaceall-la-gi)

### replace() là gì?

`replace()` là một phương thức dùng để thay thế một phần của chuỗi bằng một giá trị mới.

**Cú pháp:**

```js
let newString = string.replace(searchValue, newValue);
```

**Ví dụ:**

```js
let text = "Hello World!";
let newText = text.replace("World", "JavaScript");

console.log(newText); // "Hello JavaScript!"
```

**Bài toán và ví dụ:**

Thay thế một từ trong câu:

```javascript
let sentence = "I love cats.";
let newSentence = sentence.replace("cats", "dogs");

console.log(newSentence); // I love dogs.
```

Sửa lỗi chính tả:

```javascript
let typoText = "I have a baot.";
let correctedText = typoText.replace("baot", "boat");

console.log(correctedText); // I have a boat.
```

`replace()` giúp dễ dàng thay thế một phần của chuỗi khi cần cập nhật nội dung hoặc sửa lỗi.

***

### replaceAll() là gì?

`replaceAll()` là một phương thức dùng để thay thế tất cả các phần tử phù hợp trong chuỗi bằng một giá trị mới.

**Cú pháp:**

```js
let newString = string.replaceAll(searchValue, newValue);
```

**Ví dụ:**

```js
let text = "cats are cute, cats are playful";
let newText = text.replaceAll("cats", "dogs");

console.log(newText); // "dogs are cute, dogs are playful"
```

`replaceAll()` hữu ích khi cần thay thế tất cả các phần tử phù hợp trong chuỗi.

**Bài toán và ví dụ:**

Thay thế tất cả các từ trong câu:

```javascript
let sentence = "banana, banana, banana";
let newSentence = sentence.replaceAll("banana", "apple");

console.log(newSentence); // apple, apple, apple
```

Thay thế ký tự trong chuỗi:

```javascript
let typoText = "a-b-c-d";
let correctedText = typoText.replaceAll("-", "/");

console.log(correctedText); // a/b/c/d
```

{% hint style="info" %}
Tóm tắt

* **Phương thức replace()**:
  * `replace()` là một phương thức dùng để thay thế một phần của chuỗi bằng một giá trị mới.
  * **Cú pháp**: `let newString = string.replace(searchValue, newValue);`
  * **Ứng dụng**: Thay thế một từ trong câu, sửa lỗi chính tả.
* **Phương thức replaceAll()**:
  * `replaceAll()` là một phương thức dùng để thay thế tất cả các phần tử phù hợp trong chuỗi bằng một giá trị mới.
  * **Cú pháp**: `let newString = string.replaceAll(searchValue, newValue);`
  * **Ứng dụng**: Thay thế tất cả các từ trong câu, thay thế ký tự trong chuỗi.
{% endhint %}
