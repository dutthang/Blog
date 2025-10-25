---
title: "Bài viết 1 - Biến trong JavaScript"
date: 2025-10-24
draft: false
---

Biến trong JavaScript là một trong những phần cơ bản nhất của ngôn ngữ, cho phép bạn lưu trữ và thao tác với dữ liệu trong chương trình.  
Bài viết này sẽ giúp bạn hiểu rõ hơn về các kiểu dữ liệu, cách khai báo biến, phạm vi biến và quy tắc đặt tên trong JavaScript.

---

## 1. Kiểu dữ liệu trong JavaScript

Một trong những đặc trưng quan trọng nhất của một ngôn ngữ lập trình là tập hợp các kiểu dữ liệu mà ngôn ngữ đó hỗ trợ — tức là những loại giá trị có thể được biểu diễn và thao tác trong chương trình.

JavaScript hỗ trợ ba kiểu dữ liệu cơ bản sau:

- **Số (Number):** ví dụ `123`, `120.50`, …
- **Chuỗi văn bản (String):** ví dụ `"This text string"`, `"Xin chào"`, …
- **Boolean:** giá trị `true` hoặc `false`.

Ngoài ra, JavaScript còn định nghĩa hai kiểu dữ liệu đặc biệt: **null** và **undefined**, mỗi kiểu chỉ chứa một giá trị duy nhất.  
Bên cạnh đó, JavaScript hỗ trợ kiểu dữ liệu hỗn hợp gọi là **object (đối tượng)** – kiểu dữ liệu quan trọng nhất của ngôn ngữ này.

> 💡 **Ghi chú:** JavaScript không phân biệt giữa số nguyên (integer) và số thực (floating-point).  
> Tất cả các số đều được biểu diễn bằng định dạng dấu chấm động 64 bit theo chuẩn **IEEE 754**.

---

## 2. Khái niệm về Biến trong JavaScript

Trong JavaScript, **biến (variable)** có thể hiểu là một “hộp chứa” có tên, dùng để lưu trữ dữ liệu.  
Bạn có thể gán dữ liệu vào biến, sau đó truy cập lại chỉ bằng cách gọi tên biến đó.

Trước khi sử dụng biến, bạn cần **khai báo** nó bằng từ khóa `var` như sau:

```html
<script type="text/javascript">
   var money;
   var name;
</script>
