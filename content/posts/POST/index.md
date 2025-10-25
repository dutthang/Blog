---
title: " Kinh nghiệm và các sai lầm khi code "
draft: false
---
## 1. Dùng == (so sánh lỏng) thay vì === (so sánh nghiêm ngặt)
Đây là lỗi cơ bản và phổ biến nhất.

Vấn đề: == sẽ cố gắng ép kiểu (type coercion) hai giá trị về chung một kiểu trước khi so sánh. Điều này gây ra các kết quả rất khó lường.

Ví dụ Lỗi:

```JavaScript
console.log(0 == false);       // true (vì 0 bị ép kiểu thành false)
console.log("" == false);      // true (vì "" bị ép kiểu thành false)
console.log("10" == 10);       // true (vì "10" bị ép kiểu thành số 10)
console.log(null == undefined); // true (một trường hợp đặc biệt)
```
Nếu bạn dùng if (value == false) để kiểm tra, bạn có thể nhận kết quả sai khi value là 0 hoặc "".

Cách khắc phục: Hãy luôn dùng ===. Phép so sánh === (nghiêm ngặt) sẽ kiểm tra cả giá trị và kiểu dữ liệu. Nó không ép kiểu.

Ví dụ Đúng:

```JavaScript
console.log(0 === false);       // false
console.log("" === false);      // false
console.log("10" === 10);       // false
console.log(null === undefined); // false

// Nếu bạn thực sự muốn so sánh giá trị "10" và 10,
// hãy tự chuyển kiểu một cách rõ ràng:
let input = "10";
console.log(Number(input) === 10); // true
```
## 2. Lỗi "Cannot read properties of undefined" (hoặc "null")
Đây là lỗi runtime (lỗi khi chạy) phổ biến nhất trong JavaScript.

Vấn đề: Lỗi này xảy ra khi bạn cố gắng truy cập một thuộc tính (ví dụ: .name, .length) của một biến mà giá trị của nó đang là undefined hoặc null. Điều này thường xảy ra khi:

Bạn gọi một hàm quên return giá trị.

Bạn truy vấn một phần tử DOM không tồn tại (document.getElementById("...")).

Bạn chờ kết quả từ API nhưng nó chưa về kịp.

Ví dụ Lỗi:

```JavaScript

// Ví dụ 1: DOM không tìm thấy
const btn = document.getElementById("button-khong-ton-tai");
// 'btn' sẽ là null
// btn.addEventListener("click", () => {}); // -> Lỗi! "Cannot read properties of null"

// Ví dụ 2: Object không tồn tại
function findUser(id) {
  // Giả sử không tìm thấy user
  return undefined;
}

const user = findUser(123);
console.log(user.name); // -> Lỗi! "Cannot read properties of undefined (reading 'name')"
```
Cách khắc phục: Luôn kiểm tra sự tồn tại của biến trước khi dùng. Cách hiện đại là dùng Optional Chaining (?.).

Ví dụ Đúng:

```JavaScript
// Cách 1: Dùng 'if' (cổ điển)
const user = findUser(123);
if (user) {
  console.log(user.name);
} else {
  console.log("Không tìm thấy user.");
}

// Cách 2: Dùng Optional Chaining (?.
// Nếu 'user' là undefined/null, nó sẽ dừng lại và trả về 'undefined'
// thay vì văng lỗi.
console.log(user?.name); // In ra "undefined" (không bị lỗi)

// Áp dụng cho cả DOM
const btn = document.getElementById("button-khong-ton-tai");
btn?.addEventListener("click", () => {}); // Sẽ không làm gì cả và không báo lỗi
```
## 3. Hiểu sai ngữ cảnh của this
this là một trong những khái niệm "hack não" nhất của JavaScript.

Vấn đề: Ngữ cảnh của this không được xác định lúc bạn viết code, mà là lúc hàm đó được gọi. Nó rất dễ bị "mất" khi bạn dùng trong callback, setTimeout, hoặc event listener.

Ví dụ Lỗi:

```JavaScript
const counter = {
  count: 0,
  start: function() {
    console.log("Bắt đầu đếm...");
    // 'this' ở đây là 'counter' (đúng)

    setInterval(function() {
      // 'this' ở đây là 'window' (hoặc global)
      // vì hàm này được gọi bởi 'setInterval', không phải 'counter'
      this.count++; // -> Sẽ tăng 'window.count' (là NaN)
      console.log(this.count);
    }, 1000);
  }
};

// counter.start(); // Sẽ in ra NaN, NaN, NaN...
```
Cách khắc phục: Dùng Arrow Function (=>). Arrow function không có this của riêng nó, nó sẽ "thừa hưởng" this từ ngữ cảnh bên ngoài (nơi nó được định nghĩa).

Ví dụ Đúng:

```JavaScript
const counter = {
  count: 0,
  start: function() {
    console.log("Bắt đầu đếm...");

    // Dùng Arrow Function ở đây!
    setInterval(() => {
      // 'this' ở đây sẽ "nhìn" ra ngoài và lấy 'this' của hàm 'start'
      // chính là 'counter'
      this.count++;
      console.log(this.count);
    }, 1000);
  }
};

// counter.start(); // Sẽ in ra 1, 2, 3... (đúng)
```
## 4. Xử lý Bất đồng bộ (Async) như code Đồng bộ
JavaScript là ngôn ngữ chạy đơn luồng (single-threaded) và bất đồng bộ.

Vấn đề: Khi bạn gọi một hàm tốn thời gian (như fetch để lấy API, setTimeout), JavaScript sẽ không chờ nó xong. Nó sẽ chạy tiếp các lệnh bên dưới ngay lập tức. Bạn sẽ cố gắng sử dụng kết quả "trước khi" nó có.

Ví dụ Lỗi:

```JavaScript
function layDuLieuUser() {
  let data = null;

  // Giả lập gọi API mất 2 giây
  setTimeout(() => {
    data = { id: 1, name: "Duy Thang" };
    console.log("1. Đã lấy data xong!");
  }, 2000);

  // Lệnh này chạy ngay, không chờ 2 giây
  return data;
}

const user = layDuLieuUser();
console.log("2. Dữ liệu user:", user); 

// Kết quả in ra:
// "2. Dữ liệu user:", null
// (2 giây sau)
// "1. Đã lấy data xong!"
```
Cách khắc phục: Sử dụng Promise và cú pháp async/await.

Ví dụ Đúng:

```JavaScript
// Bước 1: Hàm của bạn phải trả về một Promise
function layDuLieuUser() {
  // Promise "hứa" rằng nó sẽ trả về kết quả trong tương lai
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      const data = { id: 1, name: "Duy Thang" };
      console.log("1. Đã lấy data xong!");
      resolve(data); // "Trả về" dữ liệu khi đã xong
    }, 2000);
  });
}

// Bước 2: Dùng async/await để "chờ" Promise hoàn thành
async function hienThiUser() {
  console.log("Chuẩn bị gọi hàm...");
  const user = await layDuLieuUser(); // 'await' sẽ tạm dừng hàm hienThiUser
                                      // cho đến khi Promise được 'resolve'

  console.log("2. Dữ liệu user:", user); // Chạy sau khi có data
}

hienThiUser();

// Kết quả in ra:
// "Chuẩn bị gọi hàm..."
// (chờ 2 giây)
// "1. Đã lấy data xong!"
// "2. Dữ liệu user:", { id: 1, name: 'Duy Thang' }
```
## 5. Dùng var thay vì let và const (Lỗi Scope)
Đây là lỗi của JavaScript "cũ" nhưng vẫn rất phổ biến.

Vấn đề: var có phạm vi (scope) là "function-scope" và bị "hoisting" (được đưa lên đầu hàm). Nó không tôn trọng các khối {...} như if hay for. Điều này gây ra lỗi logic rất khó chịu, đặc biệt trong vòng lặp for với setTimeout.

Ví dụ Lỗi:

```JavaScript
for (var i = 0; i < 3; i++) {
  setTimeout(function() {
    // Khi hàm này chạy (sau 100ms), vòng lặp 'for' đã chạy xong.
    // Biến 'i' (dùng chung cho cả hàm) đã có giá trị là 3.
    console.log(i);
  }, 100);
}

// Kết quả in ra: 3, 3, 3 (chứ không phải 0, 1, 2)
```
 - Cách khắc phục: Không bao giờ dùng var nữa. Luôn dùng let và const.

     - let: Dùng cho biến sẽ thay đổi giá trị (như biến đếm i).

     - const: Dùng cho biến không thay đổi giá trị (hằng số, object, array).

Ví dụ Đúng:

```JavaScript
// Chỉ cần thay 'var' bằng 'let'
for (let i = 0; i < 3; i++) {
  // 'let' là 'block-scoped', nghĩa là mỗi lần lặp
  // một biến 'i' MỚI với giá trị mới được tạo ra.
  setTimeout(function() {
    // Hàm setTimeout này sẽ "nhớ" giá trị 'i' của lần lặp đó.
    console.log(i);
  }, 100);
}
```
// Kết quả in ra: 0, 1, 2
Mẹo cuối cùng: Luôn bắt đầu file JavaScript của bạn với "use strict"; (chế độ nghiêm ngặt) và sử dụng một Linter (như ESLint) để tự động phát hiện các lỗi này khi bạn gõ code.