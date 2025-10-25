---
title: "Bài viết 2 - Lệnh if…else trong JavaScript"
date: 2025-10-24
draft: false
---

# Lệnh if…else trong JavaScript

Trong khi viết chương trình, đôi khi bạn sẽ gặp tình huống cần chọn một trong nhiều lựa chọn. Khi đó bạn cần sử dụng cấu trúc điều kiện để điều khiển luồng thực thi của chương trình.

JavaScript cung cấp các lệnh điều kiện để thực hiện các hành động khác nhau dựa vào điều kiện. Hãy cùng tìm hiểu lệnh **if…else**.

---

## 1. Sơ đồ hoạt động của if…else  
![Profile cá nhân](post2.jpg)

---

## 2. Các dạng lệnh điều kiện trong JavaScript  
JavaScript hỗ trợ các dạng sau:  
- Lệnh **if**  
- Lệnh **if…else**  
- Lệnh **if…else if…**

---

## 3. Lệnh if  
Lệnh `if` là dạng cơ bản cho phép JavaScript kiểm tra điều kiện và chỉ thực thi khối lệnh nếu điều kiện đúng.

### Cú pháp  
```js
if (expression) {
  // Các lệnh sẽ thực thi nếu biểu thức là true
}
Ở đây expression là biểu thức được đánh giá. Nếu kết quả là true, khối lệnh bên trong if sẽ chạy; nếu false, không có gì xảy ra.

Ví dụ
<html>
  <body>
    <script type="text/javascript">
      var age = 20;
      if (age > 18) {
        document.write("<b>Qualifies for driving</b>");
      }
    </script>
    <p>Thay đổi giá trị biến và thử lại...</p>
  </body>
</html>
```

Kết quả sẽ là:

Qualifies for driving

## 4. Lệnh if…else

Lệnh if…else cho phép bạn thực thi khối lệnh khác nếu điều kiện là false.

Cú pháp
```js
if (expression) {
  // khối lệnh nếu điều kiện đúng
} else {
  // khối lệnh nếu điều kiện sai
}
```

Ví dụ
```html
<html>
  <body>
    <script type="text/javascript">
      var age = 15;
      if (age > 18) {
        document.write("<b>Qualifies for driving</b>");
      } else {
        document.write("<b>Does not qualify for driving</b>");
      }
    </script>
    <p>Thay đổi giá trị biến và thử lại...</p>
  </body>
</html>
```
Kết quả sẽ là:
```rust
Does not qualify for driving

## 5. Lệnh if…else if…

Khi bạn cần kiểm tra nhiều điều kiện tuần tự, bạn sử dụng if…else if….
```
Cú pháp
```js
if (expression1) {
  // lệnh khi expression1 true
} else if (expression2) {
  // lệnh khi expression2 true
} else {
  // lệnh khi tất cả điều kiện trên đều sai
}
```

Ví dụ
```html
<html>
  <body>
    <script type="text/javascript">
      var book = "maths";
      if (book == "history") {
        document.write("<b>History Book</b>");
      } else if (book == "maths") {
        document.write("<b>Maths Book</b>");
      } else if (book == "economics") {
        document.write("<b>Economics Book</b>");
      } else {
        document.write("<b>Unknown Book</b>");
      }
    </script>
    <p>Thay đổi biến và thử lại...</p>
  </body>
</html>
```