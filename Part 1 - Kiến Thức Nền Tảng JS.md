# Part 1: Kiến Thức Nền Tảng JavaScript

## Giới thiệu

Khi bắt đầu học JavaScript, bạn có thể gặp nhiều thuật ngữ khác nhau như JavaScript, ES5, ES6, ECMA, TC39... Đây là những thuật ngữ quan trọng cần hiểu rõ:

#### JavaScript và ECMAScript

- **JavaScript** không phải là một ngôn ngữ "đơn lẻ" mà là một triển khai của một đặc tả gọi là ECMAScript
- **ECMAScript** là một đặc tả (specification) - một tài liệu mô tả chi tiết cách ngôn ngữ lập trình nên hoạt động
- Khác với phần mềm thông thường, JavaScript không có một "phiên bản" duy nhất để tải xuống, mà được triển khai bởi các trình duyệt khác nhau

#### ECMA International và TC39

- **ECMA International** là tổ chức quốc tế chịu trách nhiệm chuẩn hóa nhiều tiêu chuẩn công nghệ, bao gồm ECMAScript
- **TC39** (Technical Committee 39) là ủy ban kỹ thuật thuộc ECMA International, chịu trách nhiệm phát triển và duy trì đặc tả ECMAScript
- Hàng năm, các đại biểu trong ủy ban TC39 họp lại, thảo luận và quyết định các tính năng mới sẽ được thêm vào đặc tả

#### Các phiên bản ECMAScript

- Ban đầu, ECMAScript được cập nhật không thường xuyên với các phiên bản như **ES5** (2009)
- **ES6/ES2015** đánh dấu sự thay đổi lớn khi ECMA chuyển sang chu kỳ cập nhật hàng năm
- Từ năm 2015, ECMAScript áp dụng quy ước đặt tên theo năm: ES2015, ES2016, ES2017, v.v.
- Việc hiểu về các phiên bản giúp bạn biết được khi nào các tính năng được thêm vào ngôn ngữ và mức độ hỗ trợ của chúng trên các trình duyệt

Khi một tính năng mới được thêm vào ECMAScript, các trình duyệt phải cập nhật để hỗ trợ tính năng đó. Điều này giải thích tại sao một số tính năng có thể hoạt động trên trình duyệt này nhưng không hoạt động trên trình duyệt khác (đặc biệt là các trình duyệt cũ).

## Primitive Types - Giá trị nguyên thủy

JavaScript có 7 kiểu dữ liệu nguyên thủy, nhưng 5 kiểu sau đây là phổ biến nhất và cần nắm vững:

1. **Number**: Biểu diễn cả số nguyên và số thập phân
2. **String**: Biểu diễn văn bản
3. **Boolean**: Giá trị đúng (true) hoặc sai (false)
4. **Null**: Biểu thị sự vắng mặt có chủ ý của giá trị
5. **Undefined**: Biểu thị biến chưa được gán giá trị

Hai kiểu nguyên thủy ít phổ biến hơn là:

- **Symbol**: Giá trị duy nhất và không thay đổi (thêm từ ES2015)
- **BigInt**: Số nguyên có độ chính xác tùy ý (thêm gần đây)

Chúng ta sẽ tập trung vào 5 kiểu dữ liệu nguyên thủy phổ biến trước, vì chúng xuất hiện trong hầu hết mọi đoạn code JavaScript.

### Number - Kiểu số trong JavaScript

Khác với nhiều ngôn ngữ lập trình khác, JavaScript chỉ có một kiểu dữ liệu số duy nhất gọi là **Number**. Kiểu Number trong JavaScript có thể biểu diễn:

- Số nguyên (integers): `42`, `-10`, `0`
- Số thập phân (floating-point): `3.14`, `-0.5`, `2.0`
- Số âm (negative numbers): `-42`, `-3.14`

#### Đặc điểm của kiểu số trong JavaScript

JavaScript sử dụng chuẩn IEEE 754 để biểu diễn số, cụ thể là định dạng double-precision 64-bit. Điều này có một số đặc điểm quan trọng:

1. **Giới hạn độ chính xác**: Với số thập phân có nhiều chữ số sau dấu phẩy, JavaScript có thể làm tròn hoặc mất độ chính xác:

```javascript
0.1 + 0.2; // Kết quả là 0.30000000000000004, không phải 0.3 như mong đợi
```

2. **Giới hạn của số**: JavaScript có thể biểu diễn số trong khoảng từ ±5 × 10^(-324) đến ±1.7976931348623157 × 10^308

3. **Giá trị đặc biệt**: Number trong JavaScript có một số giá trị đặc biệt:
   - `Infinity`: Biểu diễn vô cực dương
   - `-Infinity`: Biểu diễn vô cực âm
   - `NaN`: "Not a Number" - biểu diễn kết quả của phép tính không hợp lệ

#### Các phép toán cơ bản với số

JavaScript hỗ trợ tất cả các phép toán cơ bản mà bạn mong đợi từ một ngôn ngữ lập trình:

1. **Phép cộng** (+): `5 + 2` // 7
2. **Phép trừ** (-): `5 - 2` // 3
3. **Phép nhân** (_): `5 _ 2` // 10
4. **Phép chia** (/): `5 / 2` // 2.5
5. **Phép chia lấy phần dư** (%): `5 % 2` // 1
6. **Phép lũy thừa** (**): `5 ** 2` // 25 (ES2016+)

#### NaN và Infinity

`NaN` (Not a Number) là một giá trị đặc biệt trong JavaScript, biểu thị kết quả của một phép tính không hợp lệ:

```javascript
0 / 0; // NaN
"abc" / 4; // NaN
Math.sqrt(-1); // NaN
```

Đặc điểm của NaN:

- `NaN` không bằng bất kỳ giá trị nào, kể cả chính nó: `NaN === NaN` // false
- Để kiểm tra một giá trị có phải là NaN không, sử dụng `isNaN()` hoặc `Number.isNaN()`

`Infinity` biểu diễn giá trị vô cùng, xuất hiện khi:

- Một số dương chia cho 0: `5 / 0` // Infinity
- Một số vượt quá giới hạn biểu diễn của JavaScript

#### Phương thức Math

JavaScript cung cấp đối tượng `Math` với nhiều phương thức hữu ích để thực hiện các phép tính phức tạp:

```javascript
Math.round(4.7); // 5 - làm tròn đến số nguyên gần nhất
Math.floor(4.7); // 4 - làm tròn xuống
Math.ceil(4.2); // 5 - làm tròn lên
Math.abs(-5); // 5 - giá trị tuyệt đối
Math.pow(2, 3); // 8 - lũy thừa (2^3)
Math.sqrt(16); // 4 - căn bậc hai
Math.min(2, 5, 1); // 1 - giá trị nhỏ nhất
Math.max(2, 5, 1); // 5 - giá trị lớn nhất
Math.random(); // Số ngẫu nhiên từ 0 đến 1 (không bao gồm 1)
```

Đối tượng Math có rất nhiều phương thức khác cho các phép tính toán học phức tạp như logarithm, lượng giác, và nhiều hơn nữa.

### String - Chuỗi trong JavaScript

**String** (chuỗi) là một kiểu dữ liệu cơ bản trong JavaScript, dùng để biểu diễn văn bản. Chuỗi là một tập hợp các ký tự như chữ cái, số, dấu câu, và ký tự đặc biệt.

#### Cách tạo chuỗi

Trong JavaScript, bạn có thể tạo chuỗi bằng cách sử dụng:

1. **Dấu nháy đơn** ('...'): `'Hello, world!'`
2. **Dấu nháy kép** ("..."): `"Hello, world!"`
3. **Dấu backtick (Template literals - ES6)** (`` `....` ``): `` `Hello, world!` ``

```javascript
const singleQuotes = "Đây là chuỗi với dấu nháy đơn";
const doubleQuotes = "Đây là chuỗi với dấu nháy kép";
const backticks = `Đây là chuỗi với dấu backtick`;
```

Các dấu nháy đơn và nháy kép hoạt động tương tự nhau, nhưng backtick cung cấp các tính năng bổ sung như chuỗi đa dòng và nội suy chuỗi (string interpolation).

#### Lưu ý khi sử dụng dấu nháy

Khi bạn cần sử dụng dấu nháy trong chuỗi, bạn có một số lựa chọn:

1. **Sử dụng loại dấu nháy khác**:

```javascript
const quote = "Cô ấy nói 'Xin chào!'";
const anotherQuote = 'Anh ấy nói "Tạm biệt!"';
```

2. **Sử dụng ký tự escape (\)**:

```javascript
const quote = "Cô ấy nói 'Xin chào!'";
const anotherQuote = 'Anh ấy nói "Tạm biệt!"';
```

#### Truy cập các ký tự trong chuỗi

Chuỗi trong JavaScript là một tập hợp các ký tự được lập chỉ mục (indexed), bắt đầu từ 0:

```javascript
const greeting = "Hello";
greeting[0]; // "H"
greeting[1]; // "e"
greeting[4]; // "o"
```

Chuỗi trong JavaScript là bất biến (immutable), có nghĩa là bạn không thể thay đổi giá trị của một ký tự riêng lẻ:

```javascript
let str = "Hello";
str[0] = "J"; // Điều này không hoạt động
console.log(str); // Vẫn là "Hello"
```

#### Thuộc tính và phương thức chuỗi quan trọng

1. **Thuộc tính length**: Trả về độ dài của chuỗi

```javascript
"Hello".length; // 5
```

2. **Các phương thức trích xuất chuỗi**:

```javascript
const str = "Hello, world!";

// Lấy một phần của chuỗi
str.slice(0, 5); // "Hello"
str.substring(7, 12); // "world"
str.substr(7, 5); // "world" (từ vị trí 7, lấy 5 ký tự)
```

3. **Các phương thức tìm kiếm**:

```javascript
const str = "Hello, world!";

str.indexOf("world"); // 7 (vị trí đầu tiên)
str.lastIndexOf("o"); // 8 (vị trí cuối cùng)
str.includes("Hello"); // true (kiểm tra sự tồn tại)
str.startsWith("Hello"); // true
str.endsWith("!"); // true
```

4. **Các phương thức biến đổi chuỗi**:

```javascript
const str = "Hello, world!";

str.toUpperCase(); // "HELLO, WORLD!"
str.toLowerCase(); // "hello, world!"
str.trim(); // Loại bỏ khoảng trắng ở đầu và cuối
str.replace("world", "JavaScript"); // "Hello, JavaScript!"
```

5. **Nối chuỗi**:

```javascript
const firstName = "John";
const lastName = "Doe";

// Sử dụng toán tử +
const fullName = firstName + " " + lastName; // "John Doe"

// Sử dụng phương thức concat()
const greeting = "Hello, ".concat(firstName, "!"); // "Hello, John!"
```

#### Template Literals (ES6)

Một tính năng mạnh mẽ được giới thiệu trong ES6 là Template Literals, cho phép:

1. **Chuỗi đa dòng** dễ dàng:

```javascript
const multiline = `Dòng 1
Dòng 2
Dòng 3`;
```

2. **Nội suy chuỗi** (embedding expressions):

```javascript
const name = "Alice";
const age = 30;
const greeting = `Xin chào, tôi là ${name} và tôi ${age} tuổi.`;
// "Xin chào, tôi là Alice và tôi 30 tuổi."
```

3. **Tagged templates** - cho phép xử lý template literals bằng một hàm:

```javascript
function highlight(strings, ...values) {
  return strings.reduce(
    (result, str, i) =>
      `${result}${str}${values[i] ? `<strong>${values[i]}</strong>` : ""}`,
    ""
  );
}

const name = "Alice";
const highlighted = highlight`Xin chào, ${name}!`;
// "Xin chào, <strong>Alice</strong>!"
```

#### Ký tự escape trong chuỗi

JavaScript hỗ trợ nhiều ký tự đặc biệt trong chuỗi, được biểu diễn bằng cách sử dụng dấu gạch chéo ngược (\):

- `\n`: Xuống dòng mới
- `\t`: Tab
- `\r`: Carriage return
- `\'`: Dấu nháy đơn
- `\"`: Dấu nháy kép
- `\\`: Dấu gạch chéo ngược
- `\uXXXX`: Ký tự Unicode (ví dụ: `\u00A9` là ký tự bản quyền ©)

```javascript
const text = "Dòng 1\nDòng 2";
console.log(text);
// Hiển thị:
// Dòng 1
// Dòng 2
```

Chuỗi là một trong những kiểu dữ liệu được sử dụng nhiều nhất trong JavaScript, đặc biệt là trong phát triển web, nơi mà xử lý và hiển thị văn bản là rất quan trọng.

### Boolean - Giá trị logic trong JavaScript

**Boolean** là một kiểu dữ liệu nguyên thủy trong JavaScript biểu diễn một trong hai giá trị: `true` (đúng) hoặc `false` (sai). Boolean được sử dụng rộng rãi trong lập trình để thực hiện các quyết định logic và điều khiển luồng chương trình.

#### Tạo giá trị Boolean

Có hai cách chính để tạo giá trị Boolean trong JavaScript:

1. **Sử dụng trực tiếp giá trị Boolean**:

```javascript
const isLoggedIn = true;
const gameOver = false;
```

2. **Sử dụng biểu thức so sánh** (sẽ trả về giá trị Boolean):

```javascript
const isGreater = 5 > 3; // true
const isEqual = 5 === 10; // false
```

#### Biểu thức Boolean và toán tử so sánh

JavaScript cung cấp các toán tử so sánh để tạo biểu thức Boolean:

1. **Toán tử so sánh bằng**:

   - `==`: So sánh bằng (chuyển đổi kiểu)
   - `===`: So sánh bằng nghiêm ngặt (không chuyển đổi kiểu)
   - `!=`: Không bằng (chuyển đổi kiểu)
   - `!==`: Không bằng nghiêm ngặt (không chuyển đổi kiểu)

2. **Toán tử so sánh số học**:
   - `>`: Lớn hơn
   - `<`: Nhỏ hơn
   - `>=`: Lớn hơn hoặc bằng
   - `<=`: Nhỏ hơn hoặc bằng

```javascript
5 == "5"; // true (chuyển đổi kiểu dữ liệu trước khi so sánh)
5 === "5"; // false (không chuyển đổi kiểu dữ liệu)
5 != "6"; // true
5 !== "5"; // true
10 > 5; // true
10 < 5; // false
10 >= 10; // true
5 <= 10; // true
```

#### Truthy và Falsy

Trong JavaScript, mọi giá trị đều có thể được chuyển đổi thành Boolean khi được sử dụng trong ngữ cảnh Boolean (như trong câu lệnh if). Chúng được chia thành hai loại:

1. **Falsy**: Các giá trị sẽ được chuyển thành `false` khi ép kiểu thành Boolean:

   - `false`
   - `0` (số không)
   - `''` (chuỗi rỗng)
   - `null`
   - `undefined`
   - `NaN`

2. **Truthy**: Mọi giá trị khác sẽ được chuyển thành `true` khi ép kiểu thành Boolean, bao gồm:
   - Bất kỳ số nào khác 0: `1`, `-1`, `0.1`, ...
   - Chuỗi không rỗng: `'hello'`, `'0'`, `' '` (chuỗi chỉ chứa khoảng trắng)
   - Mảng (ngay cả mảng rỗng): `[]`, `[1, 2, 3]`
   - Đối tượng (ngay cả đối tượng rỗng): `{}`, `{name: 'John'}`
   - Hàm: `function() {}`

```javascript
// Ví dụ về chuyển đổi thành Boolean
Boolean(0); // false
Boolean(""); // false
Boolean(null); // false
Boolean(undefined); // false
Boolean(NaN); // false

Boolean(1); // true
Boolean("hello"); // true
Boolean(" "); // true (chuỗi chỉ chứa khoảng trắng)
Boolean([]); // true
Boolean({}); // true
```

#### Toán tử logic

JavaScript hỗ trợ ba toán tử logic cơ bản:

1. **AND** (`&&`): Trả về `true` nếu cả hai toán hạng đều là `true`

```javascript
true && true; // true
true && false; // false
false && true; // false
false && false; // false

// Với các giá trị non-Boolean
5 > 3 && 10 > 5; // true (cả hai điều kiện đều đúng)
5 > 3 && 10 < 5; // false (điều kiện thứ hai sai)
```

2. **OR** (`||`): Trả về `true` nếu ít nhất một trong hai toán hạng là `true`

```javascript
true || true; // true
true || false; // true
false || true; // true
false || false; // false

// Với các giá trị non-Boolean
5 > 3 || 10 < 5; // true (điều kiện đầu tiên đúng)
5 < 3 || 10 > 5; // true (điều kiện thứ hai đúng)
5 < 3 || 10 < 5; // false (cả hai điều kiện đều sai)
```

3. **NOT** (`!`): Đảo ngược giá trị Boolean

```javascript
!true; // false
!false; // true

!5; // false (5 là truthy, nên !5 là false)
!""; // true (chuỗi rỗng là falsy, nên !'' là true)
```

#### Đánh giá short-circuit (đoản mạch)

Các toán tử logic `&&` và `||` trong JavaScript thực hiện đánh giá đoản mạch, có nghĩa là chúng dừng đánh giá ngay khi có thể xác định kết quả:

1. **`&&`** dừng và trả về giá trị đầu tiên là falsy, hoặc giá trị cuối cùng nếu tất cả đều truthy:

```javascript
0 && "hello"; // 0 (dừng tại 0 vì nó là falsy)
"hello" && "world"; // 'world' (cả hai đều truthy, trả về giá trị cuối)
```

2. **`||`** dừng và trả về giá trị đầu tiên là truthy, hoặc giá trị cuối cùng nếu tất cả đều falsy:

```javascript
"hello" || "world"; // 'hello' (dừng tại 'hello' vì nó là truthy)
0 || ""; // '' (cả hai đều falsy, trả về giá trị cuối)
```

Tính năng này thường được sử dụng để:

- **Gán giá trị mặc định**:

```javascript
const name = username || "Guest"; // Nếu username là falsy, name sẽ là 'Guest'
```

- **Ngăn chặn lỗi khi truy cập thuộc tính của đối tượng có thể là null/undefined**:

```javascript
const displayName = user && user.name; // Chỉ truy cập user.name nếu user tồn tại
```

#### Độ ưu tiên của toán tử

Toán tử logic có thứ tự ưu tiên khác nhau:

- `!` có độ ưu tiên cao nhất
- `&&` có độ ưu tiên cao hơn `||`

```javascript
// Ví dụ về độ ưu tiên
!true && false; // false (đầu tiên !true thành false, sau đó false && false là false)
true || (false && false); // true (đầu tiên false && false là false, sau đó true || false là true)
```

Boolean là kiểu dữ liệu cực kỳ quan trọng trong JavaScript, đặc biệt là khi thực hiện các câu lệnh điều kiện và xử lý logic. Việc hiểu rõ cách hoạt động của Boolean và các toán tử logic là nền tảng để viết code hiệu quả và tránh lỗi logic.

### Null và Undefined trong JavaScript

`null` và `undefined` là hai kiểu dữ liệu nguyên thủy đặc biệt trong JavaScript. Chúng đều biểu thị "sự vắng mặt của giá trị", nhưng có những điểm khác biệt quan trọng về ngữ nghĩa và cách sử dụng.

#### Undefined

`undefined` là một giá trị được JavaScript gán tự động trong các trường hợp sau:

1. **Biến được khai báo nhưng chưa được gán giá trị**:

```javascript
let name;
console.log(name); // undefined
```

2. **Khi truy cập thuộc tính không tồn tại của một đối tượng**:

```javascript
const person = { name: "John" };
console.log(person.age); // undefined
```

3. **Khi một hàm không trả về giá trị rõ ràng**:

```javascript
function doNothing() {
  // Không có lệnh return
}
console.log(doNothing()); // undefined
```

4. **Khi một hàm được gọi với ít tham số hơn số lượng tham số khai báo**:

```javascript
function greet(name) {
  return `Hello, ${name}!`;
}
console.log(greet()); // "Hello, undefined!"
```

`undefined` thuộc kiểu dữ liệu `undefined`:

```javascript
typeof undefined; // "undefined"
```

#### Null

`null` là một giá trị đặc biệt biểu thị "không có gì", "rỗng" hoặc "giá trị không biết". Khác với `undefined`, `null` thường được gán một cách rõ ràng bởi lập trình viên để chỉ ra rằng một biến cố ý không có giá trị.

```javascript
let user = null; // người dùng không tồn tại hoặc chưa đăng nhập
```

Một trong những điểm đặc biệt của `null` là mặc dù nó là một giá trị nguyên thủy, nhưng toán tử `typeof` lại trả về "object" cho `null`. Đây là một lỗi thiết kế từ những ngày đầu của JavaScript:

```javascript
typeof null; // "object" - đây là một lỗi trong JavaScript
```

Để kiểm tra một giá trị có phải là `null` không, bạn nên sử dụng phép so sánh nghiêm ngặt `===`:

```javascript
let value = null;
console.log(value === null); // true
```

#### So sánh null và undefined

1. **Giống nhau**:

   - Cả hai đều biểu thị sự vắng mặt của một giá trị
   - Cả hai đều là falsy (chuyển thành `false` trong ngữ cảnh Boolean)
   - Khi so sánh bằng lỏng lẻo (`==`), chúng được coi là bằng nhau:
     ```javascript
     null == undefined; // true
     ```

2. **Khác nhau**:
   - `undefined` thường là do JavaScript tự động gán, còn `null` thường được gán rõ ràng bởi lập trình viên
   - `typeof undefined` trả về "undefined", còn `typeof null` trả về "object" (một lỗi thiết kế)
   - Khi so sánh nghiêm ngặt (`===`), chúng khác nhau:
     ```javascript
     null === undefined; // false
     ```

#### Khi nào sử dụng null và khi nào sử dụng undefined?

- **Sử dụng `null` khi**:

  - Bạn muốn chỉ ra rằng một biến không có giá trị một cách có chủ ý
  - Bạn muốn reset giá trị của một biến

- **Sử dụng `undefined` khi**:
  - Bạn muốn kiểm tra xem một biến đã được khởi tạo chưa
  - Bạn muốn kiểm tra xem một thuộc tính có tồn tại trong đối tượng hay không

#### Cách kiểm tra null và undefined

1. **Kiểm tra strict equality**:

```javascript
// Kiểm tra null
if (value === null) {
  // code xử lý khi value là null
}

// Kiểm tra undefined
if (value === undefined) {
  // code xử lý khi value là undefined
}
```

2. **Kiểm tra cả hai**:

```javascript
// Cách 1: Sử dụng toán tử == (không khuyến khích trong hầu hết trường hợp)
if (value == null) {
  // code xử lý khi value là null hoặc undefined
}

// Cách 2: Kiểm tra rõ ràng (khuyến khích)
if (value === null || value === undefined) {
  // code xử lý khi value là null hoặc undefined
}
```

3. **Sử dụng toán tử `?` trong ES2020+**:

```javascript
// Optional chaining
const name = user?.name; // Trả về undefined nếu user là null hoặc undefined

// Nullish coalescing
const username = user?.name ?? "Guest"; // Sử dụng 'Guest' nếu user?.name là null hoặc undefined
```

Hiểu rõ sự khác biệt giữa `null` và `undefined` giúp bạn tránh những lỗi tinh vi và làm cho code của bạn rõ ràng, dễ đọc hơn.

## Variables - Biến trong JavaScript

Biến là một khái niệm cơ bản trong mọi ngôn ngữ lập trình, cho phép chúng ta lưu trữ và thao tác với dữ liệu. Trong JavaScript, biến hoạt động như những "container" (hộp chứa) cho các giá trị, cho phép chúng ta lưu trữ, truy cập và thay đổi dữ liệu trong quá trình chương trình chạy.

### Khai báo biến trong JavaScript

JavaScript cung cấp ba từ khóa để khai báo biến:

1. **`var`**: Cách truyền thống để khai báo biến (trước ES6)
2. **`let`**: Khai báo biến có thể thay đổi giá trị (thêm vào từ ES6)
3. **`const`**: Khai báo hằng số - không thể gán lại sau khi khởi tạo (thêm vào từ ES6)

#### Cú pháp khai báo biến

```javascript
// Sử dụng var
var age = 25;

// Sử dụng let
let name = "John";

// Sử dụng const
const PI = 3.14159;
```

Bạn có thể khai báo biến mà không gán giá trị ban đầu (trừ const):

```javascript
var country; // undefined
let city; // undefined
// const TAX_RATE;   // Lỗi: const phải được khởi tạo khi khai báo
```

### Let vs Const: Khi nào sử dụng cái nào?

- **Sử dụng `let`** khi bạn cần một biến có thể thay đổi giá trị:

  ```javascript
  let score = 0;
  score = 10; // Hợp lệ
  score = score + 5; // Hợp lệ
  ```

- **Sử dụng `const`** khi bạn cần một biến không thay đổi giá trị:
  ```javascript
  const API_KEY = "abc123xyz";
  // API_KEY = "new_key"; // Lỗi: không thể gán lại giá trị cho hằng số
  ```

Lưu ý rằng với `const`, nếu giá trị là một đối tượng hoặc mảng, các thuộc tính hoặc phần tử bên trong vẫn có thể thay đổi:

```javascript
const person = { name: "John" };
person.name = "Jane"; // Hợp lệ - chúng ta chỉ thay đổi thuộc tính, không gán lại biến
// person = { name: "Jane" }; // Lỗi - không thể gán lại biến
```

### Quy tắc đặt tên biến

Khi đặt tên biến trong JavaScript, bạn cần tuân theo các quy tắc sau:

1. Tên biến phải bắt đầu bằng chữ cái, dấu gạch dưới (\_), hoặc dấu đô la ($)
2. Tên biến có thể chứa chữ cái, số, dấu gạch dưới, và dấu đô la
3. Tên biến phân biệt chữ hoa và chữ thường (`name` và `Name` là hai biến khác nhau)
4. Không được sử dụng từ khóa dành riêng của JavaScript (như `var`, `function`, `return`, v.v.)

```javascript
// Hợp lệ
let name = "John";
let _private = "Secret";
let $special = "Dollar sign";
let camelCase = "Standard convention in JavaScript";
let _123 = "Starts with underscore";

// Không hợp lệ
// let 123abc = "Cannot start with number";
// let my-var = "Hyphen not allowed";
// let var = "Cannot use reserved keyword";
```

Quy ước đặt tên phổ biến trong JavaScript:

- **camelCase** cho biến và hàm (`firstName`, `calculateTotal`)
- **PascalCase** cho class và constructor (`Person`, `ReactComponent`)
- **UPPER_SNAKE_CASE** cho hằng số (`MAX_SIZE`, `API_KEY`)

### Phạm vi của biến (Variable Scope)

Phạm vi biến xác định nơi mà biến có thể được truy cập trong code. JavaScript có các loại phạm vi chính:

#### 1. Block Scope (Phạm vi khối)

Biến được khai báo bằng `let` và `const` có phạm vi khối - chỉ có thể truy cập trong khối code (giữa `{` và `}`) nơi chúng được khai báo:

```javascript
{
  let blockScoped = "I am block-scoped";
  const alsoBlockScoped = "So am I";
  console.log(blockScoped); // Hoạt động
}
// console.log(blockScoped); // Lỗi: blockScoped không được định nghĩa
```

#### 2. Function Scope (Phạm vi hàm)

Biến được khai báo bằng `var` có phạm vi hàm - chỉ có thể truy cập trong hàm nơi chúng được khai báo:

```javascript
function myFunction() {
  var functionScoped = "I am function-scoped";
  console.log(functionScoped); // Hoạt động
}
// console.log(functionScoped); // Lỗi: functionScoped không được định nghĩa
```

#### 3. Global Scope (Phạm vi toàn cục)

Biến được khai báo bên ngoài bất kỳ hàm hoặc khối nào có phạm vi toàn cục - có thể truy cập từ bất kỳ đâu trong code:

```javascript
var globalVar = "I am global (var)";
let globalLet = "I am global (let)";
const globalConst = "I am global (const)";

function myFunction() {
  console.log(globalVar); // Hoạt động
  console.log(globalLet); // Hoạt động
  console.log(globalConst); // Hoạt động
}
```

### Hoisting (Kéo lên)

Hoisting là một hành vi của JavaScript khi các khai báo biến và hàm được "kéo lên" đầu phạm vi của chúng trước khi code được thực thi. Tuy nhiên, cách biến được hoisted phụ thuộc vào cách khai báo:

#### Hoisting với var

```javascript
console.log(hoistedVar); // undefined (không lỗi)
var hoistedVar = "I am hoisted";
```

Code trên tương đương với:

```javascript
var hoistedVar; // khai báo được hoisted
console.log(hoistedVar); // undefined
hoistedVar = "I am hoisted"; // phép gán không được hoisted
```

#### Hoisting với let và const

Biến khai báo bằng `let` và `const` cũng được hoisted, nhưng không được khởi tạo. Chúng nằm trong "Temporal Dead Zone" (TDZ) cho đến khi dòng khai báo được thực thi:

```javascript
// console.log(hoistedLet); // Lỗi: Cannot access 'hoistedLet' before initialization
let hoistedLet = "I am hoisted differently";
```

### The Legacy of var - Di sản của var

Trước ES6 (2015), `var` là cách duy nhất để khai báo biến trong JavaScript. Nó có một số đặc điểm khiến nó dễ gây ra lỗi:

1. **Function-scoped, không phải block-scoped**:

```javascript
if (true) {
  var x = 10;
}
console.log(x); // 10 - vẫn truy cập được x bên ngoài khối if
```

2. **Có thể khai báo lại**:

```javascript
var user = "John";
var user = "Jane"; // Hợp lệ - không có lỗi
```

3. **Hoisting** (như đã giải thích ở trên)

Do những vấn đề này, **khuyến nghị hiện nay là sử dụng `let` và `const` thay vì `var`** cho hầu hết các trường hợp. Điều này giúp tránh những lỗi tinh vi và làm cho code dễ đọc, dễ dự đoán hơn.

### So sánh var, let và const

| Tính năng    | var                                      | let                                            | const                                          |
| ------------ | ---------------------------------------- | ---------------------------------------------- | ---------------------------------------------- |
| Phạm vi      | Function scope                           | Block scope                                    | Block scope                                    |
| Hoisting     | Hoisted với giá trị mặc định `undefined` | Hoisted nhưng ở trong TDZ (không thể truy cập) | Hoisted nhưng ở trong TDZ (không thể truy cập) |
| Khai báo lại | Cho phép                                 | Không cho phép trong cùng phạm vi              | Không cho phép trong cùng phạm vi              |
| Gán lại      | Cho phép                                 | Cho phép                                       | Không cho phép                                 |
| Khởi tạo     | Không bắt buộc                           | Không bắt buộc                                 | Bắt buộc                                       |

### Khi nào sử dụng từng loại biến

1. **`const`** (default): Sử dụng cho hầu hết các biến nếu bạn biết rằng giá trị sẽ không thay đổi
2. **`let`**: Sử dụng cho các biến mà giá trị của chúng cần thay đổi
3. **`var`**: Tránh sử dụng trừ khi có lý do cụ thể (như tương thích ngược với code cũ)

Theo phương pháp tốt nhất hiện đại, hãy sử dụng `const` làm lựa chọn mặc định, và chỉ "giảm cấp" xuống `let` khi cần thiết. Điều này giúp hạn chế phạm vi của từng biến và tránh các lỗi do thay đổi giá trị ngoài ý muốn.

## Controlling Program Logic and Flow - Điều khiển luồng chương trình

Lập trình không chỉ đơn giản là thực thi các câu lệnh theo thứ tự. Để tạo ra những ứng dụng hữu ích, chúng ta cần khả năng đưa ra quyết định, thực hiện hành động khác nhau dựa trên các điều kiện, và tạo ra các kết quả khác nhau dựa trên đầu vào. Đây chính là nơi "logic điều khiển" (control flow) phát huy tác dụng.

### Tầm quan trọng của logic trong ứng dụng

Hầu hết mọi ứng dụng đều chứa vô số quyết định và nhánh điều kiện. Ví dụ:

- **Game**: Khi người chơi di chuyển quân cờ, ứng dụng cần kiểm tra xem nước đi có hợp lệ không
- **Website đăng nhập**: Khi người dùng cố gắng đăng nhập, hệ thống kiểm tra xem thông tin đăng nhập có chính xác không
- **Ứng dụng mua sắm**: Hiển thị các thông báo khác nhau dựa trên trạng thái đơn hàng

Các quyết định này được thực hiện thông qua các cấu trúc điều khiển luồng trong JavaScript.

### Toán tử so sánh

Trước khi đi vào các câu lệnh điều kiện, chúng ta cần hiểu về các toán tử so sánh. Đây là những toán tử trả về giá trị boolean (true/false) dựa trên so sánh giữa các giá trị.

#### Toán tử so sánh cơ bản

| Toán tử | Mô tả                                          | Ví dụ               |
| ------- | ---------------------------------------------- | ------------------- |
| `==`    | Bằng (với chuyển đổi kiểu)                     | `5 == "5"` (true)   |
| `===`   | Bằng nghiêm ngặt (không chuyển đổi kiểu)       | `5 === "5"` (false) |
| `!=`    | Không bằng (với chuyển đổi kiểu)               | `5 != "6"` (true)   |
| `!==`   | Không bằng nghiêm ngặt (không chuyển đổi kiểu) | `5 !== 5` (false)   |
| `>`     | Lớn hơn                                        | `10 > 5` (true)     |
| `<`     | Nhỏ hơn                                        | `10 < 5` (false)    |
| `>=`    | Lớn hơn hoặc bằng                              | `10 >= 10` (true)   |
| `<=`    | Nhỏ hơn hoặc bằng                              | `5 <= 10` (true)    |

#### So sánh bằng lỏng lẻo (`==`) vs nghiêm ngặt (`===`)

JavaScript cung cấp hai cách để so sánh bằng:

1. **So sánh lỏng lẻo** (`==` và `!=`) - Sẽ cố gắng chuyển đổi các giá trị sang cùng kiểu trước khi so sánh:

```javascript
5 == "5"; // true - chuyển chuỗi "5" thành số 5
0 == false; // true - false chuyển thành 0
null == undefined; // true - được coi là tương đương
```

2. **So sánh nghiêm ngặt** (`===` và `!==`) - So sánh cả giá trị và kiểu dữ liệu:

```javascript
5 === "5"; // false - khác kiểu dữ liệu
0 === false; // false - khác kiểu dữ liệu
null === undefined; // false - khác kiểu dữ liệu
```

> **Thực hành tốt**: Luôn ưu tiên sử dụng phép so sánh nghiêm ngặt (`===` và `!==`) thay vì phép so sánh lỏng lẻo (`==` và `!=`) để tránh những kết quả không mong muốn do chuyển đổi kiểu ngầm định.

### Câu lệnh điều kiện If

Câu lệnh `if` là cách cơ bản nhất để thực hiện code có điều kiện trong JavaScript. Nó cho phép bạn thực thi một khối code nếu một điều kiện nhất định là đúng.

#### Cú pháp cơ bản của if

```javascript
if (điều_kiện) {
  // Code sẽ chạy nếu điều_kiện là true
}
```

Ví dụ:

```javascript
const age = 18;

if (age >= 18) {
  console.log("Bạn đủ tuổi bỏ phiếu!");
}
```

#### If...Else

Câu lệnh `if...else` cho phép bạn thực thi một khối code nếu điều kiện là đúng và một khối code khác nếu điều kiện là sai:

```javascript
if (điều_kiện) {
  // Code sẽ chạy nếu điều_kiện là true
} else {
  // Code sẽ chạy nếu điều_kiện là false
}
```

Ví dụ:

```javascript
const age = 16;

if (age >= 18) {
  console.log("Bạn đủ tuổi bỏ phiếu!");
} else {
  console.log("Bạn chưa đủ tuổi bỏ phiếu!");
}
```

#### Else If

Khi bạn cần kiểm tra nhiều điều kiện, bạn có thể sử dụng `else if`:

```javascript
if (điều_kiện_1) {
  // Code sẽ chạy nếu điều_kiện_1 là true
} else if (điều_kiện_2) {
  // Code sẽ chạy nếu điều_kiện_1 là false và điều_kiện_2 là true
} else {
  // Code sẽ chạy nếu tất cả các điều kiện trên đều false
}
```

Ví dụ:

```javascript
const score = 85;

if (score >= 90) {
  console.log("A");
} else if (score >= 80) {
  console.log("B");
} else if (score >= 70) {
  console.log("C");
} else if (score >= 60) {
  console.log("D");
} else {
  console.log("F");
}
```

#### Lồng các câu lệnh điều kiện

Bạn có thể lồng các câu lệnh `if` bên trong nhau để tạo ra logic phức tạp hơn:

```javascript
const age = 25;
const hasTicket = true;

if (age >= 18) {
  if (hasTicket) {
    console.log("Bạn có thể vào xem concert!");
  } else {
    console.log("Bạn cần mua vé trước!");
  }
} else {
  console.log("Bạn chưa đủ tuổi để vào xem concert!");
}
```

### Truthy và Falsy Values

Trong JavaScript, khi một giá trị được sử dụng trong ngữ cảnh boolean (như trong câu lệnh `if`), nó sẽ được chuyển đổi thành `true` hoặc `false`. Hiểu về truthy và falsy values là rất quan trọng để viết code điều kiện hiệu quả.

#### Falsy Values

Những giá trị sau được coi là falsy trong JavaScript:

- `false`
- `0` (số không)
- `''` (chuỗi rỗng)
- `null`
- `undefined`
- `NaN`

#### Truthy Values

Tất cả các giá trị khác sẽ được chuyển thành `true` khi ép kiểu thành Boolean, bao gồm:

- Bất kỳ số nào khác 0: `1`, `-1`, `0.1`, ...
- Chuỗi không rỗng: `'hello'`, `"0"`, `' '` (chuỗi chỉ chứa khoảng trắng)
- Mảng (ngay cả mảng rỗng): `[]`, `[1, 2, 3]`
- Đối tượng (ngay cả đối tượng rỗng): `{}`, `{name: 'John'}`
- Hàm: `function() {}`

Ví dụ:

```javascript
// Sử dụng truthy/falsy trong câu lệnh if
const username = "";

if (username) {
  console.log(`Xin chào, ${username}!`);
} else {
  console.log("Xin chào, khách!");
}
// Output: "Xin chào, khách!" (vì username là chuỗi rỗng - falsy)

const items = [];
if (items) {
  console.log("Mảng có tồn tại!");
}
// Output: "Mảng có tồn tại!" (vì mảng rỗng vẫn là truthy)
```

### Toán tử logic

JavaScript có ba toán tử logic cơ bản để kết hợp hoặc đảo ngược các điều kiện:

#### 1. AND (&&)

Toán tử `&&` trả về `true` nếu cả hai toán hạng đều là `true`:

```javascript
true && true; // true
true && false; // false
false && true; // false
false && false; // false
```

Ví dụ thực tế:

```javascript
const age = 25;
const hasTicket = true;

if (age >= 18 && hasTicket) {
  console.log("Bạn có thể vào xem concert!");
} else {
  console.log("Bạn không thể vào xem concert!");
}
```

#### 2. OR (||)

Toán tử `||` trả về `true` nếu ít nhất một trong hai toán hạng là `true`:

```javascript
true || true; // true
true || false; // true
false || true; // true
false || false; // false
```

Ví dụ thực tế:

```javascript
const isMember = false;
const isAdmin = true;

if (isMember || isAdmin) {
  console.log("Bạn có quyền truy cập vào nội dung này!");
} else {
  console.log("Bạn không có quyền truy cập!");
}
```

#### 3. NOT (!)

Toán tử `!` đảo ngược giá trị boolean:

```javascript
!true; // false
!false; // true

!5; // false (5 là truthy, nên !5 là false)
!""; // true (chuỗi rỗng là falsy, nên !'' là true)
```

#### Đánh giá short-circuit (đoản mạch)

Các toán tử logic `&&` và `||` trong JavaScript thực hiện đánh giá đoản mạch, có nghĩa là chúng dừng đánh giá ngay khi có thể xác định kết quả:

1. **`&&`** dừng và trả về giá trị đầu tiên là falsy, hoặc giá trị cuối cùng nếu tất cả đều truthy:

```javascript
0 && "hello"; // 0 (dừng tại 0 vì nó là falsy)
"hello" && "world"; // 'world' (cả hai đều truthy, trả về giá trị cuối)
```

2. **`||`** dừng và trả về giá trị đầu tiên là truthy, hoặc giá trị cuối cùng nếu tất cả đều falsy:

```javascript
"hello" || "world"; // 'hello' (dừng tại 'hello' vì nó là truthy)
0 || ""; // '' (cả hai đều falsy, trả về giá trị cuối)
```

Tính năng này thường được sử dụng để:

- **Gán giá trị mặc định**:

```javascript
const name = username || "Guest"; // Nếu username là falsy, name sẽ là 'Guest'
```

- **Ngăn chặn lỗi khi truy cập thuộc tính của đối tượng có thể là null/undefined**:

```javascript
const displayName = user && user.name; // Chỉ truy cập user.name nếu user tồn tại
```

#### Độ ưu tiên của toán tử

Toán tử logic có thứ tự ưu tiên khác nhau:

- `!` có độ ưu tiên cao nhất
- `&&` có độ ưu tiên cao hơn `||`

```javascript
// Ví dụ về độ ưu tiên
!true && false; // false (đầu tiên !true thành false, sau đó false && false là false)
true || (false && false); // true (đầu tiên false && false là false, sau đó true || false là true)
```

Việc hiểu và sử dụng thành thạo các cơ chế điều khiển luồng trong JavaScript là nền tảng quan trọng để xây dựng ứng dụng phức tạp và tương tác với người dùng. Những khái niệm này được sử dụng liên tục trong mọi dự án lập trình JavaScript.

## Kết luận

Trong phần đầu tiên này, chúng ta đã tìm hiểu về những kiến thức nền tảng của JavaScript - những khối xây dựng cơ bản mà mọi lập trình viên JavaScript cần nắm vững. Chúng ta đã khám phá:

1. **Giới thiệu về JavaScript và ECMAScript** - Hiểu về bản chất của ngôn ngữ, lịch sử phát triển và vai trò của tổ chức ECMA trong việc chuẩn hóa JavaScript.

2. **Primitive Types (Kiểu dữ liệu nguyên thủy)** - Các kiểu dữ liệu cơ bản trong JavaScript bao gồm Number, String, Boolean, Null và Undefined, cách chúng hoạt động và cách sử dụng chúng.

3. **Variables (Biến)** - Cách khai báo và sử dụng biến với var, let và const, phạm vi biến, hoisting và các quy tắc đặt tên.

4. **Controlling Program Logic (Điều khiển luồng chương trình)** - Các cấu trúc điều kiện cơ bản như if-else, switch, toán tử logic, và các kỹ thuật khác để điều khiển luồng chương trình.

Những kiến thức này tạo nền tảng vững chắc để bạn tiếp tục học về các chủ đề phức tạp hơn trong JavaScript như hàm, mảng, đối tượng, bất đồng bộ, và các khái niệm nâng cao khác.

### Thực hành là chìa khóa

Để thành thạo JavaScript, việc đọc và hiểu lý thuyết là chưa đủ. Hãy thực hành thường xuyên bằng cách:

- Viết code và thử nghiệm các ví dụ trong console của trình duyệt
- Tạo các dự án nhỏ để áp dụng kiến thức đã học
- Giải quyết các bài tập trên các nền tảng học lập trình
- Đọc và phân tích code của người khác

### Tài nguyên học tập thêm

Để tìm hiểu sâu hơn về các chủ đề đã đề cập, bạn có thể tham khảo:

1. [MDN Web Docs - JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript) - Tài liệu tham khảo toàn diện từ Mozilla
2. [JavaScript.info](https://javascript.info/) - Hướng dẫn JavaScript hiện đại từ cơ bản đến nâng cao
3. [Eloquent JavaScript](https://eloquentjavascript.net/) - Cuốn sách miễn phí trực tuyến về JavaScript

Hãy nhớ rằng học lập trình là một hành trình dài, và việc xây dựng nền tảng vững chắc với những kiến thức cơ bản này sẽ giúp bạn tiến xa hơn trong sự nghiệp phát triển web.
