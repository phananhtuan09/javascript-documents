# CharCodeAt

### charCodeAt

Phương thức **`charCodeAt`**`()` ​​trả về một số nguyên từ `0` đến `65535` biểu thị đơn vị mã UTF-16 tại chỉ mục đã cho.

#### Cú pháp

```javascript
charCodeAt(index)
```

#### Tham số

* `index`:
  * Index  của ký tự cần trả về.Nếu không truyền index hoặc truyền `undefined` thì tham số này sẽ nhận là số 0

#### Giá trị trả về

Một số nguyên từ `0` đến `65535` biểu diễn giá trị đơn vị mã UTF-16 của ký tự tại `index` được chỉ định. Nếu index nằm ngoài phạm vi `0` – `str.length - 1`, `charCodeAt()` trả về `NaN`

#### Ví dụ

```javascript
"ABC".charCodeAt(0); // returns 65
```
