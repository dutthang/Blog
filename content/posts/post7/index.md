---
title: "Bài viết 6 - Vòng lặp for…in trong JavaScript"
date: 2025-10-24
draft: false
---

# Vòng lặp for…in trong JavaScript

## 1. Khi nào dùng `for…in`?

Vòng lặp `for…in` được sử dụng để **lặp qua các thuộc tính của một đối tượng (object)** hoặc các chỉ mục (index) của một mảng. Khi bạn đã hiểu rõ đối tượng trong JavaScript thì `for…in` là công cụ rất hữu ích. 

---

## 2. Cú pháp

```js
for (variablename in object) {
  // khối lệnh sẽ được thực thi
}
```
Ở mỗi lần lặp:

variablename sẽ nhận tên của một thuộc tính hoặc chỉ mục từ object.

Vòng lặp tiếp tục cho tới khi tất cả thuộc tính của object được xử lý. 
VietJack

## 3. Ví dụ minh họa
```html
<html>
  <body>
    <script type="text/javascript">
       var aProperty;
       document.write("Navigator Object Properties<br />");

       for (aProperty in navigator) {
         document.write(aProperty);
         document.write("<br />");
       }
       document.write("Exiting from the loop!");
    </script>
    <p>Thay đổi đối tượng khác rồi thử lại…</p>
  </body>
</html>
```
Kết quả hiển thị

```vbnet
Navigator Object Properties
serviceWorker
webkitPersistentStorage
webkitTemporaryStorage
geolocation
… (và nhiều thuộc tính khác)
Exiting from the loop!
```

## 4. Những lưu ý khi sử dụng for…in
for…in lặp qua tất cả thuộc tính enumerable của đối tượng, bao gồm cả những thuộc tính thừa kế từ prototype.

Nếu dùng với mảng, for…in sẽ lặp qua chỉ số (index) chứ không phải giá trị trực tiếp.

Khi làm việc với mảng hoặc muốn chỉ lặp giá trị, bạn nên cân nhắc dùng for…of hoặc Array.forEach().

Tránh thay đổi cấu trúc đối tượng trong khi dùng for…in, vì có thể dẫn tới lỗi hoặc khối lặp không mong muốn.