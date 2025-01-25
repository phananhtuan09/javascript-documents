# Phương thức getTime, getTimezoneOffset

### Phương thức getTime

Phương thức `getTime()` trả về số mili giây cho ngày này kể từ kỷ nguyên([epoch](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date#the_epoch_timestamps_and_invalid_date)), được định nghĩa là nửa đêm vào đầu ngày 1 tháng 1 năm 1970, theo giờ UTC.

Ví dụ:

```javascript
const moonLanding = new Date('July 20, 69 20:17:40 GMT+00:00');
// Milliseconds since Jan 1, 1970, 00:00:00.000 GMT
console.log(moonLanding.getTime());
// Expected output: -14182940000
```

#### Ứng dụng

1. So sánh 2 date object

Trong Javascript ta có thể dùng các toán tử so sánh: >, <, <=, >=  để so sánh date object

Ví dụ:

```javascript
const date1 = new Date("2025-01-24");
const date2 = new Date("2025-01-25");

console.log(date1 < date2) // true
```

Tuy nhiên ta không thể sử dụng toán tử: == hoặc === (bởi vì Date vẵn là object nên tham chiếu khác nhau)

Sử dụng getTime để so sánh 2 Date object

```javascript
console.log(date1 === date2) // false
console.log(date1.getTime() === date2.getTime()) // true
```

2. Tính toán Date

Ví dụ tạo date2 lớn hơn date1 1 tiếng

```javascript
const date1 = new Date("2025-01-25");
const date2 = new Date(date1.getTime() + 3600000);

console.log(date1) // Sat Jan 25 2025 07:00:00 GMT+0700 (Indochina Time)
console.log(date2) // Sat Jan 25 2025 08:00:00 GMT+0700 (Indochina Time)
```

***

### Phương thức getTimezoneOffset

Phương thức `getTimezoneOffset()`  trả về sự khác biệt, tính bằng phút, giữa ngày này khi được đánh giá theo múi giờ UTC và cùng ngày đó khi được đánh giá theo múi giờ địa phương.

Ví dụ:

```javascript
const date= new Date('August 19, 1975 23:15:30 GMT+07:00');
console.log(date.getTimezoneOffset()); // - 420 (UTC+7)
```
