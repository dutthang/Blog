---
title: "Bài viết 8 - Hàm trong JavaScript"
date: 2025-10-24
draft: false
---

# Hàm trong JavaScript

## 1. Khái niệm về hàm  
Một hàm (function) là một nhóm mã (code) có thể tái sử dụng trong chương trình của bạn — bạn chỉ cần định nghĩa một lần và sau đó gọi nhiều lần. Việc dùng hàm giúp chương trình trở nên **gọn gàng**, **dễ quản lý**, và dễ mở rộng hơn. 

## 2. Cách định nghĩa hàm  
Để sử dụng hàm, bạn phải **định nghĩa** nó trước. Một cách phổ biến để định nghĩa hàm trong JavaScript là sử dụng từ khóa `function`, theo sau là tên hàm, danh sách tham số (có thể trống), và thân hàm chứa các câu lệnh.

### Cú pháp:
```js
function functionName(parameter1, parameter2, ...) {
  // các lệnh được thực thi khi hàm được gọi
}
```
Ví dụ đơn giản:

```html
<script type="text/javascript">
  function sayHello() {
    alert("Hello there!");
  }
</script>
```


## 3. Gọi hàm
Sau khi định nghĩa hàm, bạn chỉ cần gọi hàm bằng tên hàm và dấu ngoặc (). Ví dụ:

```html
<script type="text/javascript">
  function sayHello() {
    document.write("Hello there!");
  }
</script>
<body>
  <button onclick="sayHello()">Nhấn vào đây</button>
</body>
```
Khi người dùng nhấn nút, hàm sayHello() sẽ được thực thi. 


## 4. Tham số của hàm
Hàm có thể nhận một hoặc nhiều tham số để xử lý dữ liệu đầu vào khác nhau — và từ đó có thể cho kết quả đầu ra khác.
Ví dụ:

```html
<script type="text/javascript">
  function sayHello(name, age) {
    document.write(name + " is " + age + " years old.");
  }
</script>
```
Trong ví dụ trên, hàm sayHello có hai tham số: name và age. Khi bạn gọi hàm với đối số thực tế khác nhau, kết quả sẽ khác nhau. 
`VietJack`

## 5. Lệnh return
Nếu bạn muốn hàm trả về một giá trị cho nơi gọi, bạn sử dụng từ khóa return. Khi return được gặp, hàm ngừng thực thi và trả giá trị theo sau nó (nếu có) ra ngoài.
Ví dụ:

```js
function add(a, b) {
  return a + b;
}

var sum = add(5, 3);  // sum sẽ là 8
```
Không có return thì hàm sẽ trả về undefined theo mặc định. 


## 6. Vai trò và lợi ích của hàm
 - Tái sử dụng mã: Viết một lần, gọi nhiều lần.

 - Tổ chức chương trình theo module: Mỗi hàm đảm nhiệm một nhiệm vụ cụ thể.

 - Dễ bảo trì và phát triển: Khi cần thay đổi logic, chỉ sửa hàm mà không cần tìm khắp nơi.

 - Giúp code rõ ràng, dễ đọc và dễ mở rộng.