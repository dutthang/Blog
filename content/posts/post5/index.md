---
title: "Bài viết 4 - Vòng lặp while trong JavaScript"
date: 2025-10-24
draft: false
---

# Vòng lặp while trong JavaScript

## 1. Giới thiệu

Vòng lặp `while` trong JavaScript cho phép bạn **lặp lại một khối lệnh** miễn là điều kiện được chỉ định là đúng (`true`).  
Khi điều kiện trở thành sai (`false`), vòng lặp sẽ dừng lại.

---

## 2. Cú pháp

```js
while (điều_kiện) {
   // khối lệnh sẽ thực hiện nếu điều_kiện đúng
}
```
Giải thích:

Trước khi mỗi vòng lặp được thực hiện, JavaScript sẽ kiểm tra điều kiện.

Nếu điều kiện đúng (true), khối lệnh trong vòng lặp được thực hiện.

Nếu điều kiện sai (false), vòng lặp kết thúc.

Nếu điều kiện luôn đúng, vòng lặp sẽ chạy vô hạn (infinite loop).

## 3. Ví dụ minh họa
```html
<html>
  <body>
    <script type="text/javascript">
      var count = 0;

      document.write("Starting Loop" + "<br />");

      while (count < 10) {
         document.write("Current Count : " + count + "<br />");
         count++;
      }

      document.write("Loop stopped!");
    </script>
  </body>
</html>
```
Kết quả hiển thị:

```yaml
Starting Loop
Current Count : 0
Current Count : 1
Current Count : 2
Current Count : 3
Current Count : 4
Current Count : 5
Current Count : 6
Current Count : 7
Current Count : 8
Current Count : 9
Loop stopped!
```
## 4. Lưu ý khi sử dụng vòng lặp while
Đảm bảo điều kiện lặp có thể trở thành sai tại một thời điểm nào đó, tránh lặp vô tận.

Biến dùng trong điều kiện nên được tăng hoặc giảm giá trị trong thân vòng lặp.

Vòng lặp while thường được dùng khi không biết trước số lần lặp.

## 5. So sánh với vòng lặp for
| Tiêu chí          | while                                 | for                              |
| ----------------- | ------------------------------------- | -------------------------------- |
| Khi dùng          | Khi không biết số lần lặp cụ thể      | Khi biết trước số lần lặp        |
| Khai báo biến     | Thường khai báo trước vòng lặp        | Khai báo ngay trong câu lệnh for |
| Tăng/giảm giá trị | Thực hiện thủ công bên trong vòng lặp | Nằm ngay trong cú pháp for       |
