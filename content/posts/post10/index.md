---
title: "Bài viết 9 - Sự kiện trong JavaScript"
date: 2025-10-24
draft: false
---

# Sự kiện trong JavaScript

## 1. Sự kiện là gì?  
Sự kiện (event) trong JavaScript là **những tương tác** mà người dùng hoặc trình duyệt thực hiện trên một trang web — ví dụ như tải trang, click chuột, nhập phím, thay đổi kích thước, v.v. Khi một sự kiện xảy ra, JavaScript có thể **lắng nghe** và **phản hồi** bằng các hàm xử lý tương ứng.
Các phần tử HTML (khi được trình duyệt chuyển thành DOM) **chứa một tập hợp các sự kiện** mà bạn có thể gắn hàm xử lý.

---

## 2. Các kiểu sự kiện phổ biến  
### **onclick**  
Đây là kiểu sự kiện thường dùng nhất — khi người dùng click chuột trái. Bạn có thể gắn một hàm để thực thi khi sự kiện xảy ra.

**Ví dụ:**
```html
<html>
  <head>
    <script type="text/javascript">
      function sayHello(){
        alert("Hello World");
      }
    </script>
  </head>
  <body>
    <p>Nhấn nút dưới để xem kết quả:</p>
    <input type="button" onclick="sayHello()" value="Xin chào!" />
  </body>
</html>
``` 

### **onsubmit**  
Được kích hoạt khi người dùng submit (gửi) một form. Bạn có thể kiểm tra form trước khi gửi bằng cách gắn hàm xử lý cho sự kiện này.

**Ví dụ:**
```html
<html>
  <head>
    <script type="text/javascript">
      function validate(){
         // thực hiện kiểm tra ở đây
         return false;  // nếu không hợp lệ thì ngăn gửi form
      }
    </script>
  </head>
  <body>
    <form action="t.cgi" method="POST" onsubmit="return validate()">
       …  
       <input type="submit" value="Submit" />
    </form>
  </body>
</html>
``` 

- `onmouseover` xảy ra khi người dùng di chuyển chuột **vào** một phần tử.  
- `onmouseout` xảy ra khi người dùng di chuyển chuột **ra khỏi** phần tử đó.

**Ví dụ:**
```html
<html>
  <head>
    <script type="text/javascript">
      function over(){
        document.write("Mouse Over");
      }
      function out(){
        document.write("Mouse Out");
      }
    </script>
  </head>
  <body>
    <p>Di chuyển chuột vào vùng dưới để xem kết quả:</p>
    <div onmouseover="over()" onmouseout="out()">
      <h2>Di chuột vào đây</h2>
    </div>
  </body>
</html>
``` 

---

## 3. Sự kiện trong HTML5 chuẩn  
HTML5 mở rộng thêm rất nhiều loại sự kiện mới để xử lý tương tác và trạng thái của trang web — như `onload`, `onresize`, `onoffline`, `ononline`, `onstorage` và nhiều hơn nữa.   
Bạn nên tìm hiểu thêm khi lập trình ở mức nâng cao hoặc xây dựng ứng dụng web tương tác mạnh.

---

## 4. Vì sao cần hiểu rõ về sự kiện?  
- Sự kiện cho phép bạn **tương tác với người dùng** một cách linh hoạt và lập trình được các phản hồi ngay khi người dùng thao tác.  
- Khi bạn hiểu cách sử dụng đúng các sự kiện, bạn có thể viết mã JavaScript cho các ứng dụng web trở nên **mượt mà**, **nhanh chóng** và **trải nghiệm tốt hơn**.  
- Biết nhiều loại sự kiện đồng nghĩa bạn có thể xử lý được nhiều tình huống: form, chuột, phím, thay đổi giao diện, … và nâng cao khả năng tác động lên DOM và tương tác người dùng.

---

## 5. Kết luận  
Sự kiện là thành phần không thể thiếu trong lập trình web với JavaScript. Việc nắm bắt đúng cách định nghĩa, gắn xử lý và phản hồi các sự kiện sẽ giúp bạn viết ứng dụng có tính **tương tác cao** và **chuyên nghiệp hơn**.