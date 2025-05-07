# Part 2: Làm việc với Dữ liệu và Cấu trúc dữ liệu

Trong phần này, chúng ta sẽ khám phá cách JavaScript xử lý các tập hợp dữ liệu phức tạp hơn và cách tổ chức chúng một cách hiệu quả. Chúng ta sẽ đi sâu vào Arrays, Objects, các loại vòng lặp khác nhau để duyệt qua dữ liệu, và cách viết các hàm có thể tái sử dụng để thao tác với các cấu trúc dữ liệu này.

## Mục lục Part 2

1.  **Capture Collections of Data with Arrays (Thu thập tập hợp dữ liệu với Mảng)**
2.  **Objects - The Core of Javascript (Đối tượng - Cốt lõi của Javascript)**
3.  **The World of Loops (Thế giới của các vòng lặp)**
4.  **Writing Reusable Code with Functions (Viết mã có thể tái sử dụng với Hàm)**
5.  **An Advanced Look at Functions (Cái nhìn nâng cao về Hàm)**
6.  **Apply Functions to Collections of Data (Áp dụng Hàm cho các tập hợp dữ liệu)**

---

## Capture Collections of Data with Arrays (Thu thập tập hợp dữ liệu với Mảng)

Arrays (Mảng) là một trong những cấu trúc dữ liệu cơ bản và quan trọng nhất trong JavaScript. Chúng cho phép chúng ta lưu trữ một danh sách các giá trị (có thể thuộc nhiều kiểu dữ liệu khác nhau) trong một biến duy nhất. Việc hiểu rõ về mảng và các thao tác với mảng là rất cần thiết để làm việc hiệu quả với dữ liệu trong JavaScript.

### Giới thiệu về Arrays

#### Khái niệm cơ bản

Arrays là tập hợp các phần tử được sắp xếp theo một thứ tự nhất định. Mỗi phần tử trong mảng có một chỉ số (index) duy nhất, bắt đầu từ 0.

- **Đa dạng kiểu dữ liệu**: Mảng trong JavaScript có thể chứa các phần tử thuộc nhiều kiểu dữ liệu khác nhau trong cùng một mảng (ví dụ: numbers, strings, booleans, objects, thậm chí là các mảng khác).
- **Thứ tự**: Các phần tử trong mảng được duy trì theo thứ tự chúng được thêm vào.
- **Động (Dynamic)**: Kích thước của mảng trong JavaScript là động, có nghĩa là bạn có thể thêm hoặc bớt phần tử một cách dễ dàng.

#### Ứng dụng thực tế

Mảng được sử dụng rộng rãi trong lập trình để:

- Lưu trữ danh sách các mục (ví dụ: danh sách sản phẩm, danh sách người dùng, danh sách công việc).
- Quản lý dữ liệu có thứ tự (ví dụ: các bước trong một quy trình, lịch sử các hành động).
- Làm việc với các tập hợp dữ liệu lớn và thực hiện các thao tác lặp qua chúng.

Ví dụ:

- Danh sách các bài hát trong một playlist.
- Danh sách các bình luận dưới một bài đăng.
- Danh sách các sản phẩm trong giỏ hàng.

### Tạo Arrays

Có nhiều cách để tạo mảng trong JavaScript:

1.  **Array Literal (Khuyến nghị)**: Đây là cách phổ biến và đơn giản nhất.

    ```javascript
    const emptyArray = []; // Mảng rỗng
    const colors = ["red", "green", "blue"];
    const numbers = [1, 2, 3, 4, 5];
    const mixedData = [1, "hello", true, null, { name: "John" }];
    ```

2.  **Array Constructor**: Sử dụng từ khóa `new Array()`.
    ```javascript
    const numbers = new Array(1, 2, 3); // [1, 2, 3]
    const emptyWithLength = new Array(5); // Tạo mảng rỗng với length là 5 (chứa 5 phần tử undefined)
    ```
    _Lưu ý_: Việc sử dụng `new Array()` với một đối số số duy nhất sẽ tạo ra một mảng rỗng với thuộc tính `length` được chỉ định, chứ không phải một mảng chứa số đó.

#### Lưu ý quan trọng khi tạo mảng:

- Nên sử dụng `const` để khai báo mảng nếu bạn không có ý định gán lại toàn bộ mảng cho một mảng mới. Tuy nhiên, bạn vẫn có thể thay đổi nội dung của mảng (thêm, xóa, sửa phần tử).
- Mảng có thể chứa các kiểu dữ liệu hỗn hợp.

### Chỉ số và Truy cập phần tử trong Array (Array Indexing and Access)

Mỗi phần tử trong mảng được gán một chỉ số (index), bắt đầu từ `0` cho phần tử đầu tiên.

```javascript
const fruits = ["apple", "banana", "orange", "grape"];

// Truy cập phần tử
console.log(fruits[0]); // "apple"
console.log(fruits[1]); // "banana"
console.log(fruits[fruits.length - 1]); // "grape" (phần tử cuối cùng)
console.log(fruits[3]); // "grape"
console.log(fruits[4]); // undefined (chỉ số không tồn tại)
```

- **Truy cập bằng chỉ số**: Bạn sử dụng dấu ngoặc vuông `[]` và chỉ số của phần tử để truy cập.
- **`length` property**: Thuộc tính `length` của mảng trả về số lượng phần tử trong mảng. `arrayName.length - 1` là chỉ số của phần tử cuối cùng.
- **Truy cập ngoài phạm vi**: Nếu bạn cố gắng truy cập một chỉ số không tồn tại, JavaScript sẽ trả về `undefined`.

### Sửa đổi Arrays (Modifying Arrays)

Arrays trong JavaScript là _mutable_, có nghĩa là bạn có thể thay đổi nội dung của chúng sau khi đã tạo.

```javascript
const numbers = [10, 20, 30, 40];

// Thay đổi giá trị của một phần tử
numbers[1] = 25; // numbers bây giờ là [10, 25, 30, 40]

// Thêm phần tử mới bằng cách gán vào một chỉ số mới
numbers[4] = 50; // numbers bây giờ là [10, 25, 30, 40, 50]
numbers[numbers.length] = 60; // Cách khác để thêm vào cuối mảng

// Thêm phần tử vào chỉ số vượt xa length hiện tại sẽ tạo ra "lỗ hổng" (empty slots)
numbers[7] = 80; // numbers: [10, 25, 30, 40, 50, 60, <1 empty item>, 80]
console.log(numbers[6]); // undefined
```

### Các phương thức Array phổ biến

JavaScript cung cấp nhiều phương thức tích hợp sẵn để thao tác với mảng một cách hiệu quả.

#### 1. Thêm/Xóa phần tử ở cuối mảng: `push()` và `pop()`

- **`push()`**: Thêm một hoặc nhiều phần tử vào cuối mảng và trả về `length` mới của mảng.
  ```javascript
  const sports = ["soccer", "basketball"];
  sports.push("tennis"); // sports: ["soccer", "basketball", "tennis"], trả về 3
  sports.push("baseball", "volleyball"); // sports: ["soccer", "basketball", "tennis", "baseball", "volleyball"], trả về 5
  ```
- **`pop()`**: Xóa phần tử cuối cùng của mảng, trả về phần tử đã xóa, và giảm `length` của mảng.
  ```javascript
  const sports = ["soccer", "basketball", "tennis"];
  const lastSport = sports.pop(); // lastSport: "tennis", sports: ["soccer", "basketball"]
  ```

#### 2. Thêm/Xóa phần tử ở đầu mảng: `unshift()` và `shift()`

- **`unshift()`**: Thêm một hoặc nhiều phần tử vào đầu mảng và trả về `length` mới của mảng.
  ```javascript
  const sports = ["soccer", "basketball"];
  sports.unshift("tennis"); // sports: ["tennis", "soccer", "basketball"], trả về 3
  sports.unshift("baseball", "volleyball"); // sports: ["baseball", "volleyball", "tennis", "soccer", "basketball"], trả về 5
  ```
- **`shift()`**: Xóa phần tử đầu tiên của mảng, trả về phần tử đã xóa, và giảm `length` của mảng.
  ```javascript
  const sports = ["tennis", "soccer", "basketball"];
  const firstSport = sports.shift(); // firstSport: "tennis", sports: ["soccer", "basketball"]
  ```

#### 3. Nối mảng: `concat()`

Tạo một mảng mới bằng cách nối các mảng đã cho (hoặc các giá trị) lại với nhau. Phương thức này không thay đổi mảng gốc.

```javascript
const arr1 = [1, 2];
const arr2 = [3, 4];
const arr3 = ["a", "b"];
const combined = arr1.concat(arr2, arr3, 5); // combined: [1, 2, 3, 4, "a", "b", 5]
console.log(arr1); // [1, 2] (không thay đổi)
```

#### 4. Kiểm tra sự tồn tại của phần tử: `includes()` và `indexOf()`

- **`includes()`**: Kiểm tra xem một mảng có chứa một giá trị cụ thể hay không, trả về `true` hoặc `false`.
  ```javascript
  const numbers = [1, 2, 3, 2, 4];
  console.log(numbers.includes(2)); // true
  console.log(numbers.includes(5)); // false
  console.log(numbers.includes(2, 3)); // true (tìm từ index 3)
  ```
- **`indexOf()`**: Trả về chỉ số đầu tiên của một phần tử được tìm thấy trong mảng. Nếu không tìm thấy, trả về `-1`.
  ```javascript
  const numbers = [1, 2, 3, 2, 4];
  console.log(numbers.indexOf(2)); // 1 (chỉ số đầu tiên của số 2)
  console.log(numbers.indexOf(5)); // -1 (không tìm thấy)
  console.log(numbers.indexOf(2, 2)); // 3 (tìm từ index 2)
  ```
- **`lastIndexOf()`**: Tương tự `indexOf()`, nhưng tìm từ cuối mảng về đầu.

#### 5. Đảo ngược và nối chuỗi: `reverse()` và `join()`

- **`reverse()`**: Đảo ngược thứ tự các phần tử trong mảng. Phương thức này thay đổi mảng gốc.
  ```javascript
  const letters = ["a", "b", "c"];
  letters.reverse(); // letters: ['c', 'b', 'a']
  ```
- **`join()`**: Nối tất cả các phần tử của một mảng thành một chuỗi. Bạn có thể chỉ định một ký tự phân tách (separator).
  ```javascript
  const elements = ["Fire", "Air", "Water"];
  console.log(elements.join()); // "Fire,Air,Water" (mặc định là dấu phẩy)
  console.log(elements.join("")); // "FireAirWater"
  console.log(elements.join("-")); // "Fire-Air-Water"
  ```

#### 6. Trích xuất một phần của mảng: `slice()`

Tạo một mảng mới (shallow copy) chứa một phần của mảng gốc, được chọn từ `start` index đến `end` index (không bao gồm `end`). Mảng gốc không bị thay đổi.

```javascript
const animals = ["ant", "bison", "camel", "duck", "elephant"];
console.log(animals.slice(2)); // ["camel", "duck", "elephant"] (từ index 2 đến hết)
console.log(animals.slice(2, 4)); // ["camel", "duck"] (từ index 2 đến trước index 4)
console.log(animals.slice(1, 5)); // ["bison", "camel", "duck", "elephant"]
console.log(animals.slice(-2)); // ["duck", "elephant"] (2 phần tử cuối)
console.log(animals.slice(2, -1)); // ["camel", "duck"] (từ index 2 đến trước phần tử cuối)
```

#### 7. Thêm/Xóa/Thay thế phần tử một cách linh hoạt: `splice()`

Thay đổi nội dung của một mảng bằng cách xóa hoặc thay thế các phần tử hiện có và/hoặc thêm các phần tử mới vào đúng vị trí. Phương thức này thay đổi mảng gốc và trả về một mảng chứa các phần tử đã xóa.
Cú pháp: `array.splice(start, deleteCount, item1, item2, ...)`

- `start`: Chỉ số bắt đầu thay đổi mảng.
- `deleteCount` (tùy chọn): Số lượng phần tử cần xóa.
- `item1, item2, ...` (tùy chọn): Các phần tử cần thêm vào mảng.

```javascript
const months = ["Jan", "March", "April", "June"];

// Thêm 'Feb' vào vị trí 1
months.splice(1, 0, "Feb");
// months: ["Jan", "Feb", "March", "April", "June"]

// Thay thế 'June' bằng 'May', 'June'
months.splice(4, 1, "May", "June");
// months: ["Jan", "Feb", "March", "April", "May", "June"]

// Xóa 'March' (tại index 2)
const removed = months.splice(2, 1);
// removed: ["March"], months: ["Jan", "Feb", "April", "May", "June"]
```

#### 8. Sắp xếp mảng: `sort()`

Sắp xếp các phần tử của một mảng tại chỗ (thay đổi mảng gốc) và trả về mảng đã sắp xếp.

- Mặc định, `sort()` chuyển đổi các phần tử thành chuỗi và sắp xếp chúng theo thứ tự từ điển (Unicode code points).
- Để sắp xếp số hoặc các kiểu dữ liệu phức tạp khác, bạn cần cung cấp một hàm so sánh (compare function).

```javascript
const fruitNames = ["cherries", "apple", "banana"];
fruitNames.sort(); // fruitNames: ["apple", "banana", "cherries"]

const numberList = [4, 2, 5, 1, 3, 10];
numberList.sort(); // Kết quả có thể không như mong đợi: [1, 10, 2, 3, 4, 5] (vì sắp xếp theo chuỗi)

// Sắp xếp số đúng cách với compare function
numberList.sort(function (a, b) {
  return a - b; // Sắp xếp tăng dần
});
// numberList: [1, 2, 3, 4, 5, 10]

numberList.sort((a, b) => b - a); // Sắp xếp giảm dần (sử dụng arrow function)
// numberList: [10, 5, 4, 3, 2, 1]
```

Hàm so sánh `(a, b)` nên trả về:

- Giá trị âm nếu `a` nên đứng trước `b`.
- Giá trị dương nếu `a` nên đứng sau `b`.
- `0` nếu thứ tự của `a` và `b` không thay đổi.

### Reference Types và Arrays (Kiểu tham chiếu và Mảng)

Trong JavaScript, Arrays (cùng với Objects và Functions) là _reference types_ (kiểu tham chiếu), khác với _primitive types_ (kiểu nguyên thủy như numbers, strings, booleans).

- **Primitive Types**: Khi bạn gán một biến kiểu nguyên thủy cho một biến khác, giá trị thực sự được sao chép.
  ```javascript
  let x = 10;
  let y = x; // y nhận giá trị 10
  y = 20;
  console.log(x); // 10 (x không thay đổi)
  ```
- **Reference Types**: Khi bạn gán một biến kiểu tham chiếu (ví dụ: mảng) cho một biến khác, thực chất là bạn đang sao chép _tham chiếu_ (địa chỉ bộ nhớ) đến cùng một đối tượng mảng, chứ không phải sao chép chính mảng đó.

  ````javascript
  const arrA = [1, 2, 3];
  const arrB = arrA; // arrB bây giờ tham chiếu đến cùng một mảng với arrA

      arrB.push(4);
      console.log(arrA); // [1, 2, 3, 4] (arrA cũng thay đổi)
      console.log(arrB); // [1, 2, 3, 4]
      ```

  Điều này có nghĩa là nếu bạn thay đổi mảng thông qua một biến, thay đổi đó sẽ được phản ánh ở tất cả các biến khác cùng trỏ đến mảng đó.
  ````

#### So sánh Arrays

Vì mảng là kiểu tham chiếu, việc so sánh hai biến mảng bằng `==` hoặc `===` sẽ chỉ trả về `true` nếu cả hai biến cùng tham chiếu đến _cùng một đối tượng mảng trong bộ nhớ_.

```javascript
const nums1 = [1, 2, 3];
const nums2 = [1, 2, 3];
const nums3 = nums1;

console.log(nums1 === nums2); // false (mặc dù nội dung giống nhau, chúng là 2 đối tượng mảng khác nhau)
console.log(nums1 == nums2); // false
console.log(nums1 === nums3); // true (nums1 và nums3 tham chiếu đến cùng 1 mảng)
```

Để so sánh nội dung của hai mảng, bạn cần duyệt qua từng phần tử và so sánh chúng.

### Làm việc với `const` và Arrays

Khi bạn khai báo một mảng bằng `const`, điều đó có nghĩa là biến đó sẽ luôn tham chiếu đến _cùng một đối tượng mảng_. Bạn không thể gán lại biến đó cho một mảng mới.

```javascript
const MY_ARRAY = [1, 2, 3];
// MY_ARRAY = [4, 5, 6]; // Lỗi! TypeError: Assignment to constant variable.
```

Tuy nhiên, vì mảng là mutable, bạn _vẫn có thể thay đổi nội dung_ của mảng đó (thêm, xóa, sửa phần tử):

```javascript
const MY_ARRAY = [1, 2, 3];
MY_ARRAY.push(4); // Hoạt động! MY_ARRAY bây giờ là [1, 2, 3, 4]
MY_ARRAY[0] = 100; // Hoạt động! MY_ARRAY bây giờ là [100, 2, 3, 4]
```

Sử dụng `const` với mảng là một thực hành tốt để tránh việc vô tình gán lại toàn bộ mảng.

### Nested Arrays (Mảng lồng nhau)

Mảng có thể chứa các mảng khác làm phần tử, tạo ra cấu trúc mảng lồng nhau (còn gọi là mảng đa chiều).

```javascript
const gameBoard = [
  ["X", "O", "X"],
  ["O", "X", "O"],
  ["X", "O", "X"],
];

// Truy cập phần tử trong mảng lồng nhau
console.log(gameBoard[0][0]); // 'X' (hàng 0, cột 0)
console.log(gameBoard[1][2]); // 'O' (hàng 1, cột 2)

// Thay đổi phần tử
gameBoard[1][1] = " "; // Thay đổi ô giữa thành rỗng
```

Mảng lồng nhau rất hữu ích để biểu diễn các cấu trúc dữ liệu dạng bảng, ma trận, hoặc các lưới (grids).

---

## Objects - The Core of Javascript (Đối tượng - Cốt lõi của Javascript)

Objects (Đối tượng) là một cấu trúc dữ liệu cực kỳ quan trọng và là nền tảng của JavaScript. Nếu Arrays cho phép lưu trữ một danh sách các giá trị có thứ tự, thì Objects cho phép lưu trữ một tập hợp các cặp _key-value_ (khóa-giá trị) không có thứ tự cụ thể. Keys thường là chuỗi (hoặc Symbols), và values có thể là bất kỳ kiểu dữ liệu nào, bao gồm cả các objects hoặc arrays khác.

### Tạo Object trong JS

#### Khái niệm cơ bản

- **Key-Value Pairs**: Mỗi thuộc tính (property) của một object bao gồm một key và một value tương ứng.
- **Unordered**: Các thuộc tính trong object không được đảm bảo có một thứ tự cụ thể khi duyệt (mặc dù các phiên bản JavaScript gần đây có xu hướng duy trì thứ tự chèn cho các key là chuỗi và số nguyên).
- **Dynamic**: Bạn có thể thêm, sửa đổi, hoặc xóa các thuộc tính của object sau khi nó được tạo.

#### Cú pháp Object Literal

Cách phổ biến và dễ đọc nhất để tạo object là sử dụng object literal `{}`.

```javascript
// Đối tượng rỗng
const emptyObject = {};

// Đối tượng mô tả một cuốn sách
const book = {
  title: "The Great Gatsby",
  author: "F. Scott Fitzgerald",
  yearPublished: 1925,
  genres: ["Novel", "Tragedy"],
  isAvailable: true,
  getSummary: function () {
    return `${this.title} by ${this.author}`;
  },
};
```

#### Cấu trúc của Object

- **Keys (Khóa)**: Là tên của thuộc tính. JavaScript sẽ tự động chuyển đổi keys thành chuỗi. Nếu key là một định danh JavaScript hợp lệ (không chứa khoảng trắng, không bắt đầu bằng số, không phải từ khóa), bạn có thể viết nó mà không cần dấu nháy. Nếu không, bạn phải đặt key trong dấu nháy đơn hoặc kép.
  ```javascript
  const person = {
    name: "Alice", // Key hợp lệ không cần nháy
    "full name": "Alice Wonderland", // Key chứa khoảng trắng, cần nháy
    "age-in-years": 30, // Key chứa gạch nối, cần nháy
    123: "one two three", // Key là số, sẽ được chuyển thành chuỗi "123"
  };
  ```
- **Values (Giá trị)**: Có thể là bất kỳ kiểu dữ liệu nào: number, string, boolean, array, object khác, function (khi đó được gọi là method).
- **Dấu phẩy**: Phân tách các cặp key-value.

### Truy cập Thuộc tính (Accessing Properties)

Có hai cách chính để truy cập các thuộc tính của một object:

#### 1. Dot Notation (Ký hiệu dấu chấm)

Sử dụng khi key của thuộc tính là một định danh JavaScript hợp lệ.

```javascript
const car = {
  make: "Toyota",
  model: "Camry",
  year: 2022,
};

console.log(car.make); // "Toyota"
console.log(car.year); // 2202

// car.nonExistentProperty; // undefined
```

- **Ưu điểm**: Ngắn gọn, dễ đọc.
- **Hạn chế**: Không dùng được với key không hợp lệ (ví dụ, có khoảng trắng) hoặc key là biến.

#### 2. Bracket Notation (Ký hiệu dấu ngoặc vuông)

Luôn luôn hoạt động, kể cả với các key không phải là định danh hợp lệ hoặc khi key là một biến.

```javascript
const person = {
  name: "Bob",
  "job title": "Developer",
  age: 28,
};

console.log(person["name"]); // "Bob"
console.log(person["job title"]); // "Developer"

let propertyName = "age";
console.log(person[propertyName]); // 28 (truy cập bằng biến)

console.log(person["na" + "me"]); // "Bob" (truy cập bằng biểu thức)
```

- **Ưu điểm**: Linh hoạt, có thể dùng với mọi loại key (chuỗi, biến, biểu thức trả về chuỗi).
- **Khi nào nên dùng Bracket Notation?**
  - Khi key chứa khoảng trắng hoặc ký tự đặc biệt.
  - Khi key là giá trị của một biến.
  - Khi key là kết quả của một biểu thức.

### Thêm và Cập nhật Thuộc tính

Bạn có thể dễ dàng thêm thuộc tính mới vào một object hoặc cập nhật giá trị của thuộc tính hiện có.

```javascript
const userProfile = {
  username: "coder123",
};

// Thêm thuộc tính mới
userProfile.email = "coder123@example.com"; // Dot notation
userProfile["country"] = "USA"; // Bracket notation

// Cập nhật thuộc tính
userProfile.username = "super_coder";
userProfile.country = "Canada";

console.log(userProfile);
// {
//   username: "super_coder",
//   email: "coder123@example.com",
//   country: "Canada"
// }
```

Nếu bạn gán giá trị cho một key chưa tồn tại, JavaScript sẽ tạo mới thuộc tính đó. Nếu key đã tồn tại, giá trị của nó sẽ được cập nhật.

### Lồng Đối tượng và Mảng (Nested Objects and Arrays)

Objects có thể chứa các objects khác hoặc arrays làm giá trị cho các thuộc tính của chúng, tạo ra các cấu trúc dữ liệu phức tạp.

```javascript
const student = {
  firstName: "David",
  lastName: "Jones",
  contactInfo: {
    email: "david.jones@email.com",
    phone: "555-1234",
  },
  courses: [
    { title: "Math 101", grade: "A" },
    { title: "History 202", grade: "B+" },
  ],
};

// Truy cập dữ liệu lồng nhau
console.log(student.firstName); // "David"
console.log(student.contactInfo.email); // "david.jones@email.com"
console.log(student.courses[0].title); // "Math 101"
console.log(student["courses"][1]["grade"]); // "B+"
```

#### Mảng các Đối tượng

Một trường hợp phổ biến là có một mảng chứa nhiều đối tượng, mỗi đối tượng đại diện cho một thực thể.

```javascript
const products = [
  { id: 1, name: "Laptop", price: 1200 },
  { id: 2, name: "Mouse", price: 25 },
  { id: 3, name: "Keyboard", price: 75 },
];

console.log(products[1].name); // "Mouse"
```

### Reference Types và Objects (Kiểu tham chiếu và Đối tượng)

Tương tự như Arrays, Objects trong JavaScript cũng là _reference types_.

```javascript
const obj1 = { value: 10 };
const obj2 = obj1; // obj2 tham chiếu đến cùng một đối tượng như obj1

obj2.value = 20;

console.log(obj1.value); // 20 (obj1 cũng bị thay đổi)
console.log(obj2.value); // 20
```

Khi bạn gán một biến object cho một biến khác, bạn đang sao chép tham chiếu, không phải bản thân object. Do đó, thay đổi object thông qua một biến sẽ ảnh hưởng đến tất cả các biến khác cùng trỏ đến object đó.

#### So sánh Objects

Việc so sánh hai biến object bằng `==` hoặc `===` chỉ trả về `true` nếu cả hai biến cùng tham chiếu đến _cùng một đối tượng trong bộ nhớ_.

```javascript
const person1 = { name: "Alice" };
const person2 = { name: "Alice" };
const person3 = person1;

console.log(person1 === person2); // false (hai đối tượng khác nhau, dù nội dung giống hệt)
console.log(person1 === person3); // true (cùng tham chiếu đến một đối tượng)
```

Để so sánh nội dung của hai object, bạn cần so sánh từng cặp key-value của chúng.

#### `const` và Objects

Khi khai báo một object bằng `const`, biến đó sẽ luôn tham chiếu đến cùng một object. Bạn không thể gán lại biến đó cho một object mới.

```javascript
const CONFIG = { apiKey: "xyz123" };
// CONFIG = { newKey: "abc456" }; // Lỗi! Assignment to constant variable.
```

Tuy nhiên, bạn _vẫn có thể thay đổi các thuộc tính_ bên trong object đó:

```javascript
CONFIG.apiKey = "updatedKey789"; // Hoạt động!
CONFIG.user = "admin"; // Hoạt động! (Thêm thuộc tính mới)
```

Objects là một phần không thể thiếu của JavaScript, được sử dụng để mô hình hóa dữ liệu trong thế giới thực, cấu hình ứng dụng, và nhiều hơn nữa. Hiểu rõ cách tạo, truy cập và thao tác với objects là một kỹ năng quan trọng.

---

## The World of Loops (Thế giới của các vòng lặp)

Vòng lặp là một khái niệm cơ bản trong lập trình, cho phép chúng ta thực thi một khối code lặp đi lặp lại nhiều lần. Điều này cực kỳ hữu ích khi bạn cần xử lý các tập hợp dữ liệu (như arrays hoặc objects) hoặc thực hiện một hành động nào đó một số lần nhất định.

### Tại sao cần vòng lặp?

- **Tránh lặp lại code**: Thay vì viết cùng một đoạn code nhiều lần, bạn chỉ cần viết nó một lần trong vòng lặp.
- **Xử lý dữ liệu động**: Duyệt qua các phần tử của mảng hoặc thuộc tính của đối tượng mà không cần biết trước số lượng của chúng.
- **Tự động hóa tác vụ**: Thực hiện các tác vụ lặp đi lặp lại một cách tự động.

JavaScript cung cấp nhiều loại vòng lặp khác nhau, mỗi loại phù hợp với các tình huống cụ thể.

### Vòng lặp `for`

Vòng lặp `for` là loại vòng lặp phổ biến nhất và linh hoạt nhất. Nó thường được sử dụng khi bạn biết trước số lần lặp hoặc cần một bộ đếm để theo dõi tiến trình.

#### Cú pháp

```javascript
for (khởi_tạo; điều_kiện; biểu_thức_cập_nhật) {
  // Khối code sẽ được thực thi trong mỗi lần lặp
}
```

- **`khởi_tạo`**: Thực thi một lần duy nhất trước khi vòng lặp bắt đầu. Thường dùng để khai báo và khởi tạo biến đếm (ví dụ: `let i = 0`).
- **`điều_kiện`**: Biểu thức boolean được kiểm tra trước mỗi lần lặp. Nếu là `true`, khối code bên trong sẽ thực thi. Nếu là `false`, vòng lặp kết thúc.
- **`biểu_thức_cập_nhật`**: Thực thi sau mỗi lần lặp. Thường dùng để cập nhật biến đếm (ví dụ: `i++`, `i--`, `i += 2`).

#### Ví dụ cơ bản

```javascript
// In ra các số từ 0 đến 4
for (let i = 0; i < 5; i++) {
  console.log("Số hiện tại là:", i);
}

// In ra các số chẵn từ 0 đến 10
for (let i = 0; i <= 10; i += 2) {
  console.log(i);
}

// Đếm ngược từ 5 về 1
for (let i = 5; i >= 1; i--) {
  console.log(i);
}
```

#### Lặp qua Mảng (Arrays)

Vòng lặp `for` cổ điển rất hữu ích để duyệt qua các phần tử của mảng bằng chỉ số.

```javascript
const fruits = ["apple", "banana", "cherry"];

for (let i = 0; i < fruits.length; i++) {
  console.log(`Phần tử thứ ${i}: ${fruits[i]}`);
}

// Lặp ngược qua mảng
for (let i = fruits.length - 1; i >= 0; i--) {
  console.log(fruits[i]);
}
```

#### Lồng vòng lặp `for` (Nested For Loops)

Bạn có thể đặt một vòng lặp `for` bên trong một vòng lặp `for` khác. Điều này hữu ích khi làm việc với các cấu trúc dữ liệu đa chiều như mảng lồng nhau.

```javascript
const matrix = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9],
];

for (let i = 0; i < matrix.length; i++) {
  console.log(`Hàng ${i}:`);
  for (let j = 0; j < matrix[i].length; j++) {
    console.log(`  Phần tử [${i}][${j}]: ${matrix[i][j]}`);
  }
}
```

Trong ví dụ này, vòng lặp bên ngoài duyệt qua từng hàng (mảng con), và vòng lặp bên trong duyệt qua từng phần tử trong hàng đó.

#### Infinite Loops (Vòng lặp vô hạn)

Một lỗi phổ biến là tạo ra vòng lặp vô hạn, xảy ra khi điều kiện dừng của vòng lặp không bao giờ trở thành `false`.

```javascript
// Ví dụ về vòng lặp vô hạn (KHÔNG chạy code này!)
// for (let i = 1; i > 0; i++) {
//   console.log(i);
// }
```

Trong ví dụ trên, `i` luôn lớn hơn 0 và tiếp tục tăng, nên điều kiện `i > 0` sẽ không bao giờ sai.

**Cách tránh vòng lặp vô hạn:**

- Đảm bảo rằng điều kiện dừng cuối cùng sẽ trở thành `false`.
- Kiểm tra cẩn thận biểu thức cập nhật biến đếm.
- Sử dụng từ khóa `break` nếu cần thiết để thoát khỏi vòng lặp dựa trên một điều kiện khác.

### Vòng lặp `while`

Vòng lặp `while` thực thi một khối code lặp đi lặp lại _chừng nào_ một điều kiện cụ thể còn đúng.

#### Cú pháp

```javascript
while (điều_kiện) {
  // Khối code sẽ thực thi
  // Cần có cơ chế cập nhật để điều_kiện cuối cùng thành false
}
```

- **`điều_kiện`**: Được kiểm tra _trước_ mỗi lần lặp. Nếu `true`, khối code thực thi. Nếu `false` ngay từ đầu, khối code không bao giờ thực thi.

#### Ví dụ

```javascript
// Tương đương vòng lặp for(let i = 0; i < 5; i++)
let i = 0;
while (i < 5) {
  console.log("Số hiện tại là:", i);
  i++;
}

// Ví dụ về đoán số
const SECRET_NUMBER = 7;
let guess = Math.floor(Math.random() * 10) + 1; // Đoán số ngẫu nhiên từ 1-10

while (guess !== SECRET_NUMBER) {
  console.log(`Đoán: ${guess}... Sai rồi!`);
  guess = Math.floor(Math.random() * 10) + 1;
}
console.log(`Đoán: ${guess}... Chính xác!`);
```

#### Khi nào dùng `while`?

- Khi bạn không biết trước chính xác số lần lặp.
- Khi vòng lặp phụ thuộc vào một điều kiện có thể thay đổi bên trong vòng lặp (ví dụ: đầu vào của người dùng, trạng thái của game).

### Vòng lặp `for...of` (ES6+)

Được giới thiệu trong ES6, vòng lặp `for...of` cung cấp một cách đơn giản và dễ đọc hơn để lặp qua các phần tử của các _iterable objects_ (đối tượng có thể lặp) như Arrays, Strings, Maps, Sets, v.v.

#### Cú pháp

```javascript
for (let element of iterable) {
  // Khối code thực thi cho mỗi element
}
```

- **`element`**: Một biến sẽ nhận giá trị của từng phần tử trong `iterable` ở mỗi lần lặp.
- **`iterable`**: Đối tượng có thể lặp (ví dụ: một mảng, một chuỗi).

#### Ví dụ với Array

```javascript
const colors = ["red", "green", "blue"];

for (let color of colors) {
  console.log(color);
}
// Output:
// red
// green
// blue
```

So sánh với vòng lặp `for` cổ điển, `for...of` gọn gàng hơn vì bạn không cần quản lý chỉ số (`i`).

#### Ví dụ với String

```javascript
const message = "Hello";

for (let char of message) {
  console.log(char);
}
// Output:
// H
// e
// l
// l
// o
```

#### `for...of` với Objects?

**Quan trọng**: Vòng lặp `for...of` **không** hoạt động trực tiếp với các plain objects (đối tượng thông thường) vì chúng không phải là iterable theo mặc định.

```javascript
const user = { name: "Alice", age: 30 };

// for (let value of user) { // Lỗi! user is not iterable
//   console.log(value);
// }
```

Để lặp qua các thuộc tính của object, bạn có thể sử dụng `for...of` kết hợp với các phương thức như `Object.keys()`, `Object.values()`, hoặc `Object.entries()`:

```javascript
const movieRatings = {
  Arrival: 9.5,
  Alien: 9,
  Amelie: 8.5,
  "In Bruges": 9,
};

// Lặp qua keys
for (let key of Object.keys(movieRatings)) {
  console.log(`Key: ${key}`);
}

// Lặp qua values
for (let value of Object.values(movieRatings)) {
  console.log(`Value: ${value}`);
}

// Lặp qua key-value pairs
for (let [key, value] of Object.entries(movieRatings)) {
  console.log(`Phim: ${key}, Đánh giá: ${value}`);
}
```

### Vòng lặp `for...in`

Vòng lặp `for...in` được sử dụng để lặp qua các _keys_ (thuộc tính có thể liệt kê - enumerable properties) của một object.

#### Cú pháp

```javascript
for (let key in object) {
  // Khối code thực thi cho mỗi key
  // Sử dụng object[key] để truy cập value
}
```

- **`key`**: Một biến sẽ nhận tên (key) của từng thuộc tính trong `object` ở mỗi lần lặp.
- **`object`**: Đối tượng cần lặp qua các thuộc tính.

#### Ví dụ với Object

```javascript
const studentGrades = {
  math: 90,
  science: 85,
  history: 92,
};

for (let subject in studentGrades) {
  console.log(`Môn học: ${subject}, Điểm: ${studentGrades[subject]}`);
}
// Output:
// Môn học: math, Điểm: 90
// Môn học: science, Điểm: 85
// Môn học: history, Điểm: 92
```

#### `for...in` với Array?

**Cảnh báo**: Mặc dù về mặt kỹ thuật bạn _có thể_ sử dụng `for...in` để lặp qua các chỉ số của một mảng (vì chỉ số cũng được coi là key dạng chuỗi), **đây không phải là cách làm được khuyến khích**. Lý do:

- Nó có thể lặp qua cả các thuộc tính không phải chỉ số nếu mảng có thêm thuộc tính tùy chỉnh.
- Thứ tự lặp không được đảm bảo.
- Nó chậm hơn so với các vòng lặp `for` hoặc `for...of`.

> **Thực hành tốt**: Sử dụng `for...of` hoặc `for` cổ điển để lặp qua mảng. Sử dụng `for...in` chủ yếu để lặp qua các thuộc tính của object.

### Từ khóa `break`

Từ khóa `break` được sử dụng để thoát khỏi một vòng lặp (`for`, `while`, `for...of`, `for...in`) hoặc một câu lệnh `switch` ngay lập tức, bất kể điều kiện dừng của vòng lặp đã được đáp ứng hay chưa.

```javascript
// Tìm phần tử đầu tiên lớn hơn 5
const numbers = [1, 3, 8, 2, 6];
let foundNumber = -1;

for (let num of numbers) {
  if (num > 5) {
    foundNumber = num;
    break; // Thoát khỏi vòng lặp ngay khi tìm thấy
  }
  console.log("Đang kiểm tra:", num);
}

console.log("Số đầu tiên lớn hơn 5 là:", foundNumber); // 8
```

Trong ví dụ trên, vòng lặp dừng ngay khi gặp số `8`, và các số `2`, `6` không được kiểm tra nữa.

### So sánh các loại vòng lặp

| Loại vòng lặp         | Trường hợp sử dụng chính                                       | Ưu điểm                                | Nhược điểm                                                              |
| --------------------- | -------------------------------------------------------------- | -------------------------------------- | ----------------------------------------------------------------------- |
| **`for`**             | Biết trước số lần lặp, cần truy cập chỉ số                     | Linh hoạt, kiểm soát chặt chẽ biến đếm | Cú pháp dài dòng hơn                                                    |
| **`while`**           | Không biết trước số lần lặp, lặp dựa trên điều kiện            | Đơn giản khi điều kiện phức tạp        | Dễ tạo vòng lặp vô hạn nếu quên cập nhật điều kiện                      |
| **`for...of`** (ES6+) | Lặp qua các phần tử của iterable (Arrays, Strings, Maps, Sets) | Cú pháp gọn gàng, dễ đọc               | Không truy cập trực tiếp chỉ số, không dùng trực tiếp cho plain objects |
| **`for...in`**        | Lặp qua các keys của object                                    | Cách chính thống để duyệt keys object  | Không nên dùng cho arrays, thứ tự không đảm bảo                         |

Vòng lặp là công cụ mạnh mẽ để xử lý dữ liệu và tự động hóa tác vụ. Việc chọn đúng loại vòng lặp cho từng tình huống sẽ giúp code của bạn hiệu quả và dễ đọc hơn.

---

## Writing Reusable Code with Functions (Viết mã có thể tái sử dụng với Hàm)

Khi chương trình của bạn trở nên phức tạp hơn, bạn sẽ thấy mình lặp lại các đoạn code giống nhau ở nhiều nơi. Functions (Hàm) là một khái niệm cơ bản trong lập trình cho phép bạn đóng gói một khối code có thể tái sử dụng, đặt tên cho nó, và gọi nó thực thi bất cứ khi nào cần.

### Tại sao cần Hàm?

- **Tái sử dụng (Reusability)**: Viết code một lần và gọi nó nhiều lần từ các nơi khác nhau.
- **Tổ chức (Organization)**: Chia nhỏ code thành các đơn vị logic nhỏ hơn, dễ quản lý và dễ hiểu hơn.
- **Trừu tượng hóa (Abstraction)**: Che giấu chi tiết triển khai phức tạp bên trong hàm, chỉ cần biết hàm làm gì và cách gọi nó.
- **Bảo trì (Maintainability)**: Khi cần sửa lỗi hoặc thay đổi logic, bạn chỉ cần cập nhật ở một nơi duy nhất (trong hàm).

### Định nghĩa Hàm (Defining Functions)

Cách phổ biến nhất để định nghĩa hàm trong JavaScript là sử dụng từ khóa `function`.

#### Cú pháp cơ bản (Function Declaration)

```javascript
function functionName(parameter1, parameter2, ...) {
  // Khối code thực thi khi hàm được gọi
  // (có thể chứa lệnh return để trả về giá trị)
}
```

- **`function`**: Từ khóa để bắt đầu định nghĩa hàm.
- **`functionName`**: Tên của hàm (tuân theo quy tắc đặt tên biến). Tên nên mang tính mô tả về chức năng của hàm.
- **`(parameter1, parameter2, ...)`**: Danh sách các tham số (parameters) - là các biến đại diện cho dữ liệu đầu vào mà hàm sẽ nhận khi được gọi. Đây là phần tùy chọn.
- **`{ ... }`**: Thân hàm (function body) - chứa các câu lệnh JavaScript sẽ được thực thi khi hàm được gọi.

#### Ví dụ về Function Declaration

```javascript
// Hàm đơn giản không có tham số
function greet() {
  console.log("Xin chào!");
}

// Hàm có một tham số
function greetPerson(name) {
  console.log(`Xin chào, ${name}!`);
}

// Hàm có nhiều tham số và trả về giá trị
function add(num1, num2) {
  const sum = num1 + num2;
  return sum; // Trả về kết quả
}
```

### Gọi Hàm (Calling/Invoking Functions)

Sau khi định nghĩa, bạn có thể gọi hàm để thực thi khối code bên trong nó bằng cách sử dụng tên hàm theo sau là cặp dấu ngoặc đơn `()`.

```javascript
greet(); // Output: Xin chào!

greetPerson("Alice"); // Output: Xin chào, Alice!

const result = add(5, 3); // Gọi hàm add và lưu kết quả vào biến result
console.log(result); // Output: 8
```

### Tham số và Đối số (Parameters vs Arguments)

- **Parameters (Tham số)**: Là các biến được liệt kê trong phần định nghĩa hàm `function(parameter1, parameter2)`. Chúng hoạt động như các biến cục bộ bên trong hàm, nhận giá trị từ các đối số được truyền vào khi hàm được gọi.
- **Arguments (Đối số)**: Là các giá trị thực tế được truyền vào hàm khi nó được gọi `myFunction(argument1, argument2)`.

```javascript
function introduce(name, age) {
  // name và age là parameters
  console.log(`Tôi là ${name}, ${age} tuổi.`);
}

introduce("Bob", 30); // "Bob" và 30 là arguments
```

#### Giá trị mặc định cho Tham số (Default Parameters - ES6+)

Bạn có thể gán giá trị mặc định cho tham số. Nếu đối số không được truyền vào cho tham số đó khi gọi hàm, giá trị mặc định sẽ được sử dụng.

```javascript
function multiply(a, b = 1) {
  // b có giá trị mặc định là 1
  return a * b;
}

console.log(multiply(5, 2)); // 10 (b nhận giá trị 2)
console.log(multiply(5)); // 5  (b sử dụng giá trị mặc định 1)
```

### Lệnh `return`

Lệnh `return` được sử dụng bên trong hàm để:

1.  Kết thúc việc thực thi hàm.
2.  Trả về một giá trị cụ thể từ hàm ra nơi nó được gọi.

```javascript
function calculateArea(width, height) {
  if (width < 0 || height < 0) {
    return undefined; // Trả về undefined nếu đầu vào không hợp lệ
  }
  const area = width * height;
  return area; // Trả về diện tích tính được
}

const area1 = calculateArea(10, 5);
console.log(area1); // 50

const area2 = calculateArea(-5, 5);
console.log(area2); // undefined
```

- Một hàm có thể có nhiều lệnh `return` (ví dụ, trong các nhánh `if...else`). Khi một lệnh `return` được thực thi, hàm sẽ ngay lập tức dừng lại.
- Nếu một hàm không có lệnh `return` rõ ràng, hoặc có lệnh `return;` mà không có giá trị theo sau, hàm đó sẽ mặc định trả về `undefined`.

```javascript
function logMessage(message) {
  console.log(message);
  // Không có return
}

const returnValue = logMessage("Test");
console.log(returnValue); // undefined
```

### Phạm vi của Hàm (Function Scope)

Các biến được khai báo bên trong một hàm (sử dụng `var`, `let`, hoặc `const`) có _phạm vi hàm_ (hoặc _phạm vi khối_ đối với `let`/`const` bên trong các khối `{}` của hàm). Điều này có nghĩa là chúng chỉ có thể được truy cập từ bên trong hàm đó, không phải từ bên ngoài.

```javascript
function exampleScope() {
  const functionVariable = "Tôi ở trong hàm";
  console.log(functionVariable);
}

exampleScope(); // Output: Tôi ở trong hàm

// console.log(functionVariable); // Lỗi! functionVariable is not defined
```

Các tham số của hàm cũng được coi là các biến cục bộ trong phạm vi của hàm đó.

### Ví dụ: Viết các hàm có thể tái sử dụng

```javascript
// Hàm kiểm tra số chẵn
function isEven(number) {
  return number % 2 === 0;
}

// Hàm tính tổng một mảng số
function sumArray(arr) {
  let total = 0;
  for (let i = 0; i < arr.length; i++) {
    total += arr[i];
  }
  return total;
}

// Hàm tìm ký tự đầu tiên của chuỗi
function getFirstChar(str) {
  if (str.length === 0) {
    return undefined;
  }
  return str[0];
}

// Sử dụng các hàm
console.log(isEven(4)); // true
console.log(isEven(7)); // false

const numbers = [1, 2, 3, 4, 5];
console.log(sumArray(numbers)); // 15

console.log(getFirstChar("JavaScript")); // "J"
console.log(getFirstChar("")); // undefined
```

Hàm là một trong những khái niệm cốt lõi của JavaScript, giúp bạn viết code sạch hơn, dễ quản lý hơn và hiệu quả hơn. Việc thành thạo cách định nghĩa và sử dụng hàm là bước quan trọng để trở thành một lập trình viên JavaScript giỏi.

---

## An Advanced Look at Functions (Cái nhìn nâng cao về Hàm)

Sau khi nắm vững những kiến thức cơ bản về hàm, chúng ta sẽ đi sâu hơn vào một số khái niệm và tính năng nâng cao liên quan đến hàm trong JavaScript. Hiểu rõ những khái niệm này sẽ giúp bạn viết code linh hoạt, mạnh mẽ và hiện đại hơn.

### Function Scope (Phạm vi Hàm) và Block Scope (Phạm vi Khối)

Chúng ta đã đề cập đến phạm vi (scope) trước đó, nhưng hãy xem xét kỹ hơn sự khác biệt giữa function scope và block scope, đặc biệt là trong bối cảnh của hàm.

- **Function Scope**: Biến được khai báo bằng `var` bên trong một hàm chỉ có thể truy cập được ở bất kỳ đâu bên trong hàm đó, kể cả bên trong các khối `if` hoặc `for` lồng nhau.

  ```javascript
  function exampleVarScope() {
    if (true) {
      var message = "Var có function scope";
    }
    console.log(message); // "Var có function scope" - Có thể truy cập ở đây
  }
  exampleVarScope();
  // console.log(message); // Lỗi! message is not defined (Ngoài phạm vi hàm)
  ```

- **Block Scope (ES6+)**: Biến được khai báo bằng `let` và `const` bên trong một khối code `{...}` (ví dụ: trong `if`, `for`, `while`, hoặc thậm chí chỉ là một cặp ngoặc nhọn đơn lẻ) chỉ có thể truy cập được bên trong khối đó.
  ```javascript
  function exampleLetConstScope() {
    if (true) {
      let blockMessage = "Let/Const có block scope";
      const alsoBlock = true;
      console.log(blockMessage); // Hoạt động
    }
    // console.log(blockMessage); // Lỗi! blockMessage is not defined (Ngoài phạm vi khối if)
    // console.log(alsoBlock);    // Lỗi!
  }
  exampleLetConstScope();
  ```
  > **Thực hành tốt**: Ưu tiên sử dụng `let` và `const` để tận dụng block scope, giúp hạn chế phạm vi của biến và tránh các lỗi không mong muốn do `var` gây ra.

### Lexical Scope (Phạm vi Từ vựng)

Lexical Scope (còn gọi là Static Scope) có nghĩa là phạm vi của một biến được xác định bởi vị trí của nó trong code khi code được _viết_ (tại thời điểm biên dịch hoặc định nghĩa), chứ không phải khi hàm được _gọi_.

Nói cách khác, một hàm lồng nhau (nested function) có thể truy cập các biến được định nghĩa trong phạm vi của hàm cha (outer function) chứa nó.

```javascript
function outerFunction() {
  const outerVariable = "Tôi ở bên ngoài";

  function innerFunction() {
    const innerVariable = "Tôi ở bên trong";
    console.log(outerVariable); // Có thể truy cập outerVariable từ innerFunction
    console.log(innerVariable);
  }

  innerFunction();
  // console.log(innerVariable); // Lỗi! Không thể truy cập innerVariable từ outerFunction
}

outerFunction();
// Output:
// Tôi ở bên ngoài
// Tôi ở bên trong
```

Khả năng truy cập biến từ phạm vi cha này là nền tảng cho các khái niệm quan trọng khác như Closures.

### Function Expressions (Biểu thức Hàm)

Ngoài cách khai báo hàm bằng `function` declaration (ví dụ: `function myFunction() {}`), bạn còn có thể tạo hàm bằng cách sử dụng function expression. Function expression là việc gán một hàm (thường là hàm ẩn danh - anonymous function) cho một biến.

```javascript
// Function Declaration
function addDeclaration(x, y) {
  return x + y;
}

// Function Expression
const addExpression = function (x, y) {
  return x + y;
};

// Gọi hàm được tạo bằng function expression
const sum = addExpression(10, 5);
console.log(sum); // 15
```

#### Sự khác biệt chính giữa Declaration và Expression:

- **Hoisting**: Function declarations được _hoisted_ hoàn toàn (cả tên và thân hàm được đưa lên đầu phạm vi), nghĩa là bạn có thể gọi hàm declaration trước khi nó được định nghĩa trong code.
  ```javascript
  sayHello(); // Hoạt động!
  function sayHello() {
    console.log("Xin chào từ Declaration!");
  }
  ```
  Function expressions _không được hoisted_ theo cách này. Chỉ có phần khai báo biến (ví dụ `const sayHi;`) được hoisted (nếu dùng `var`, nó sẽ được hoisted với giá trị `undefined`), nhưng việc gán hàm cho biến đó thì không. Bạn không thể gọi hàm expression trước khi dòng gán được thực thi.
  ```javascript
  // sayHi(); // Lỗi! TypeError: sayHi is not a function (hoặc ReferenceError nếu dùng let/const)
  const sayHi = function () {
    console.log("Xin chào từ Expression!");
  };
  sayHi(); // Hoạt động!
  ```
- **Tính linh hoạt**: Function expressions có thể được sử dụng ở những nơi mà function declarations không thể, ví dụ như làm đối số cho hàm khác hoặc trong các biểu thức điều kiện.

### Higher-Order Functions (Hàm bậc cao)

Trong JavaScript, hàm được coi là "first-class citizens" (công dân hạng nhất), nghĩa là chúng có thể được:

- Gán cho biến (như function expressions).
- Truyền làm đối số (arguments) cho các hàm khác.
- Trả về từ các hàm khác.

Một hàm được gọi là **Higher-Order Function** nếu nó thỏa mãn ít nhất một trong hai điều kiện sau:

1.  Nhận một hoặc nhiều hàm khác làm đối số.
2.  Trả về một hàm.

#### 1. Functions as Arguments (Truyền hàm làm đối số)

Đây là nền tảng của khái niệm _callback functions_. Bạn truyền một hàm (callback) vào một hàm khác (higher-order function) để hàm đó có thể gọi lại (call back) hàm bạn đã truyền vào tại một thời điểm thích hợp.

```javascript
// Higher-order function: nhận một hàm làm đối số
function callTwice(func) {
  func();
  func();
}

// Callback function
function laugh() {
  console.log("HAHAHA!");
}

callTwice(laugh); // Truyền hàm laugh làm đối số
// Output:
// HAHAHA!
// HAHAHA!

// Ví dụ khác: Thực hiện một hành động n lần
function repeatAction(action, times) {
  for (let i = 0; i < times; i++) {
    action(i); // Gọi hàm action với chỉ số lần lặp
  }
}

function logNumber(index) {
  console.log(`Lần lặp thứ ${index}`);
}

repeatAction(logNumber, 3);
// Output:
// Lần lặp thứ 0
// Lần lặp thứ 1
// Lần lặp thứ 2
```

Các phương thức mảng như `forEach`, `map`, `filter`, `reduce` đều là higher-order functions vì chúng nhận callback function làm đối số.

#### 2. Functions as Return Values (Trả về hàm từ hàm khác)

Một hàm có thể tạo và trả về một hàm khác. Hàm được trả về này thường "nhớ" phạm vi (lexical scope) của hàm cha nơi nó được tạo ra (đây chính là khái niệm Closure).

```javascript
// Hàm trả về một hàm khác
function makeMultiplier(multiplier) {
  // Hàm được trả về "nhớ" giá trị của multiplier
  const innerFunc = function (x) {
    return x * multiplier;
  };
  return innerFunc; // Trả về hàm bên trong
}

// Tạo các hàm nhân cụ thể
const multiplyByTwo = makeMultiplier(2);
const multiplyByTen = makeMultiplier(10);

// Sử dụng các hàm đã tạo
console.log(multiplyByTwo(5)); // 10 (5 * 2)
console.log(multiplyByTen(7)); // 70 (7 * 10)

console.log(makeMultiplier(3)(6)); // 18 (Cách gọi trực tiếp hàm được trả về)
```

Ví dụ này minh họa khái niệm Closure. Hàm `innerFunc` vẫn có thể truy cập biến `multiplier` của `makeMultiplier` ngay cả sau khi `makeMultiplier` đã thực thi xong và trả về `innerFunc`.

### Callback Functions (Hàm Callback)

Như đã đề cập, callback function là một hàm được truyền vào một hàm khác như một đối số, và được hàm đó gọi lại sau này.

Callbacks rất phổ biến trong JavaScript, đặc biệt là trong các tình huống:

- **Xử lý bất đồng bộ (Asynchronous Operations)**: Ví dụ như khi đợi dữ liệu từ server về, đợi người dùng click chuột, hoặc đợi một khoảng thời gian (`setTimeout`).
- **Các phương thức mảng**: `forEach`, `map`, `filter`, `reduce`, `sort`, `find`, etc.
- **Xử lý sự kiện (Event Handling)**: Gắn các hàm xử lý (event listeners) cho các sự kiện DOM.

```javascript
// Ví dụ với setTimeout (bất đồng bộ)
console.log("Bắt đầu!");

setTimeout(function () {
  // Hàm ẩn danh này là callback
  console.log("Đã đợi 2 giây!");
}, 2000); // Thực thi callback sau 2000ms (2 giây)

console.log("Kết thúc (nhưng setTimeout vẫn đang chạy ngầm)!");

// Ví dụ với forEach (phương thức mảng)
const names = ["Alice", "Bob", "Charlie"];

names.forEach(function (name, index) {
  // Hàm này là callback
  console.log(`Vị trí ${index}: ${name}`);
});
```

### Hoisting Revisited (Xem lại về Hoisting)

Chúng ta đã nói về hoisting đối với biến (`var`, `let`, `const`) và function expressions.

- **Function Declarations**: Được hoisted hoàn toàn. Cả tên và thân hàm đều được đưa lên đầu phạm vi trước khi code thực thi.
- **`var` Variables**: Chỉ khai báo (`var variableName;`) được hoisted và được gán giá trị mặc định là `undefined`. Phép gán giá trị không được hoisted.
- **`let` and `const` Variables**: Được hoisted nhưng không được khởi tạo (nằm trong Temporal Dead Zone - TDZ). Bạn không thể truy cập chúng trước dòng khai báo.
- **Function Expressions**: Nếu gán cho biến `var`, biến đó được hoisted với giá trị `undefined`. Nếu gán cho `let` hoặc `const`, biến đó được hoisted nhưng nằm trong TDZ. Bản thân hàm (phần `function(...) {...}`) không được hoisted cùng với tên biến.

```javascript
console.log(a); // undefined (var a được hoisted)
// console.log(b); // Lỗi! ReferenceError: Cannot access 'b' before initialization (let b ở trong TDZ)
// console.log(c); // Lỗi! ReferenceError: Cannot access 'c' before initialization (const c ở trong TDZ)

// funcD();        // Lỗi! TypeError: funcD is not a function (var funcD được hoisted là undefined)
// funcE();        // Lỗi! ReferenceError (let funcE ở trong TDZ)
funcF(); // Hoạt động! (Function declaration funcF được hoisted)

var a = 1;
let b = 2;
const c = 3;

var funcD = function () {
  console.log("D");
};
let funcE = function () {
  console.log("E");
};
function funcF() {
  console.log("F");
}
```

Hiểu rõ hoisting giúp bạn tránh các lỗi bất ngờ và viết code có cấu trúc tốt hơn.

Các khái niệm nâng cao về hàm như scope, closures, higher-order functions, và callbacks là những công cụ mạnh mẽ trong JavaScript, cho phép bạn viết code mô-đun, linh hoạt và biểu cảm hơn.

---

## Apply Functions to Collections of Data (Áp dụng Hàm cho các tập hợp dữ liệu)

Một trong những ứng dụng mạnh mẽ nhất của hàm trong JavaScript là khả năng áp dụng chúng để xử lý tập hợp dữ liệu. JavaScript cung cấp nhiều phương thức mảng tiện ích có thể nhận các hàm làm đối số để thực hiện các thao tác phức tạp trên dữ liệu một cách ngắn gọn và rõ ràng.

### Phương thức `forEach`

Phương thức `forEach` thực thi một hàm đã cho một lần cho mỗi phần tử của mảng. Đây là cách đơn giản để duyệt qua tất cả các phần tử mà không cần dùng vòng lặp truyền thống.

#### Cú pháp:

```javascript
array.forEach(function (currentValue, index, array) {
  // code thực thi cho mỗi phần tử
});
```

- **`currentValue`**: Giá trị của phần tử hiện tại đang được xử lý.
- **`index`** (tùy chọn): Chỉ số của phần tử hiện tại.
- **`array`** (tùy chọn): Mảng gốc đang được duyệt.

#### Ví dụ:

```javascript
const numbers = [1, 2, 3, 4, 5];

numbers.forEach(function (number) {
  console.log(number * 2);
});
// Output: 2, 4, 6, 8, 10

// Viết gọn hơn với arrow function
numbers.forEach((number) => console.log(number * 2));

// Sử dụng tham số index
numbers.forEach((number, index) => {
  console.log(`Phần tử tại vị trí ${index} là: ${number}`);
});
```

#### Lưu ý:

- `forEach` không trả về giá trị (hoặc chính xác là trả về `undefined`).
- `forEach` không thể dừng giữa chừng (không thể dùng `break` hoặc `return` để thoát khỏi vòng lặp).
- `forEach` là phương pháp thay thế tiện lợi cho vòng lặp `for` khi bạn chỉ muốn thực thi một đoạn code cho mỗi phần tử mà không quan tâm đến giá trị trả về.

### Phương thức `map`

Phương thức `map` tạo ra một mảng mới bằng cách áp dụng một hàm cho mỗi phần tử của mảng gốc. Điều này cho phép "biến đổi" dữ liệu của mảng mà không thay đổi mảng gốc.

#### Cú pháp:

```javascript
const newArray = array.map(function (currentValue, index, array) {
  // trả về giá trị biến đổi
  return transformedValue;
});
```

#### Ví dụ:

```javascript
const numbers = [1, 2, 3, 4, 5];

// Tạo mảng mới với mỗi phần tử nhân đôi
const doubled = numbers.map(function (num) {
  return num * 2;
});
console.log(doubled); // [2, 4, 6, 8, 10]
console.log(numbers); // [1, 2, 3, 4, 5] (mảng gốc không đổi)

// Viết gọn với arrow function
const squared = numbers.map((num) => num * num);
console.log(squared); // [1, 4, 9, 16, 25]

// Biến đổi mảng đối tượng
const users = [
  { name: "Alice", age: 25 },
  { name: "Bob", age: 30 },
  { name: "Charlie", age: 35 },
];

const usernames = users.map((user) => user.name);
console.log(usernames); // ['Alice', 'Bob', 'Charlie']
```

#### Khi nào dùng `map`:

- Khi bạn cần tạo một mảng mới dựa trên mảng hiện có.
- Khi bạn muốn áp dụng cùng một biến đổi cho tất cả các phần tử của mảng.
- Khi bạn muốn giữ nguyên mảng gốc.

### Phương thức `filter`

Phương thức `filter` tạo ra một mảng mới chứa các phần tử vượt qua được điều kiện kiểm tra do hàm callback cung cấp. Chỉ những phần tử mà callback trả về `true` (hoặc giá trị truthy) mới được đưa vào mảng mới.

#### Cú pháp:

```javascript
const filteredArray = array.filter(function (currentValue, index, array) {
  // trả về true để giữ lại phần tử, false để loại bỏ
  return condition;
});
```

#### Ví dụ:

```javascript
const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

// Lọc ra các số chẵn
const evenNumbers = numbers.filter(function (num) {
  return num % 2 === 0;
});
console.log(evenNumbers); // [2, 4, 6, 8, 10]

// Viết gọn với arrow function
const greaterThanFive = numbers.filter((num) => num > 5);
console.log(greaterThanFive); // [6, 7, 8, 9, 10]

// Lọc mảng đối tượng
const products = [
  { name: "Laptop", price: 1200, inStock: true },
  { name: "Phone", price: 800, inStock: true },
  { name: "Tablet", price: 600, inStock: false },
  { name: "Headphones", price: 200, inStock: true },
];

const availableProducts = products.filter((product) => product.inStock);
console.log(availableProducts); // [Laptop, Phone, Headphones]

const expensiveProducts = products.filter((product) => product.price > 700);
console.log(expensiveProducts); // [Laptop, Phone]
```

#### Khi nào dùng `filter`:

- Khi bạn cần loại bỏ các phần tử không phù hợp với một điều kiện nào đó.
- Khi bạn muốn trích xuất một tập con từ mảng ban đầu dựa trên một hoặc nhiều tiêu chí.
- Khi bạn muốn giữ nguyên mảng gốc.

### Phương thức `find`

Phương thức `find` trả về phần tử đầu tiên trong mảng thỏa mãn hàm kiểm tra được cung cấp. Nếu không tìm thấy phần tử nào, nó trả về `undefined`.

#### Cú pháp:

```javascript
const foundElement = array.find(function (currentValue, index, array) {
  // trả về true khi tìm thấy phần tử cần tìm
  return condition;
});
```

#### Ví dụ:

```javascript
const numbers = [1, 2, 3, 4, 5, 6];

// Tìm số đầu tiên lớn hơn 3
const firstOverThree = numbers.find((num) => num > 3);
console.log(firstOverThree); // 4 (không phải [4, 5, 6])

// Tìm đối tượng trong mảng
const users = [
  { id: 1, name: "Alice", role: "admin" },
  { id: 2, name: "Bob", role: "user" },
  { id: 3, name: "Charlie", role: "user" },
];

const admin = users.find((user) => user.role === "admin");
console.log(admin); // { id: 1, name: 'Alice', role: 'admin' }

const userWithId2 = users.find((user) => user.id === 2);
console.log(userWithId2); // { id: 2, name: 'Bob', role: 'user' }

const user404 = users.find((user) => user.id === 99);
console.log(user404); // undefined (không tìm thấy)
```

#### So sánh với `filter`:

- `find` trả về phần tử đầu tiên thỏa mãn điều kiện (hoặc `undefined`), `filter` trả về tất cả các phần tử thỏa mãn (hoặc mảng rỗng).
- `find` dừng việc tìm kiếm khi phát hiện phần tử đầu tiên phù hợp, nên có thể hiệu quả hơn khi chỉ cần một kết quả.

### Phương thức `some` và `every`

Hai phương thức này kiểm tra mảng dựa trên điều kiện và trả về giá trị boolean.

#### `some`: Kiểm tra xem có ít nhất một phần tử thỏa mãn điều kiện hay không.

```javascript
const numbers = [1, 2, 3, 4, 5];

// Kiểm tra xem có số nào lớn hơn 3 không
const hasNumberGreaterThan3 = numbers.some((num) => num > 3);
console.log(hasNumberGreaterThan3); // true

// Kiểm tra xem có số nào lớn hơn 10 không
const hasNumberGreaterThan10 = numbers.some((num) => num > 10);
console.log(hasNumberGreaterThan10); // false
```

#### `every`: Kiểm tra xem tất cả các phần tử có thỏa mãn điều kiện hay không.

```javascript
const numbers = [1, 2, 3, 4, 5];

// Kiểm tra xem tất cả các số có dương không
const allPositive = numbers.every((num) => num > 0);
console.log(allPositive); // true

// Kiểm tra xem tất cả các số có lớn hơn 2 không
const allGreaterThan2 = numbers.every((num) => num > 2);
console.log(allGreaterThan2); // false (vì 1 và 2 không > 2)
```

### Phương thức `reduce`

Phương thức `reduce` là một trong những phương thức mạnh mẽ nhất. Nó thực hiện một hàm lên mỗi phần tử của mảng (từ trái sang phải) để giảm mảng xuống một giá trị duy nhất.

#### Cú pháp:

```javascript
const result = array.reduce(function (accumulator, currentValue, index, array) {
  // trả về giá trị mới cho accumulator
  return updatedAccumulator;
}, initialValue);
```

- **`accumulator`**: Tích lũy giá trị trả về từ các lần gọi callback trước (hoặc `initialValue` nếu được cung cấp).
- **`currentValue`**: Phần tử hiện tại đang được xử lý.
- **`initialValue`** (tùy chọn): Giá trị để sử dụng làm `accumulator` đầu tiên. Nếu không cung cấp, phần tử đầu tiên của mảng sẽ được sử dụng.

#### Ví dụ:

```javascript
const numbers = [1, 2, 3, 4, 5];

// Tính tổng các số
const sum = numbers.reduce(function (total, current) {
  return total + current;
}, 0);
console.log(sum); // 15

// Viết gọn với arrow function
const product = numbers.reduce((total, current) => total * current, 1);
console.log(product); // 120 (1*2*3*4*5)

// Tìm số lớn nhất
const max = numbers.reduce((maxValue, current) => {
  return Math.max(maxValue, current);
}, numbers[0]);
console.log(max); // 5

// Gộp mảng đối tượng thành một đối tượng
const pets = [
  { name: "Rex", type: "dog", age: 4 },
  { name: "Felix", type: "cat", age: 7 },
  { name: "Buddy", type: "dog", age: 2 },
];

const petsByType = pets.reduce((groupedPets, pet) => {
  if (!groupedPets[pet.type]) {
    groupedPets[pet.type] = [];
  }
  groupedPets[pet.type].push(pet);
  return groupedPets;
}, {});

console.log(petsByType);
/*
{
  dog: [
    { name: 'Rex', type: 'dog', age: 4 },
    { name: 'Buddy', type: 'dog', age: 2 }
  ],
  cat: [
    { name: 'Felix', type: 'cat', age: 7 }
  ]
}
*/
```

#### Khi nào dùng `reduce`:

- Khi bạn cần tổng hợp một mảng thành một giá trị duy nhất, như tính tổng, tích, thống kê, v.v.
- Khi bạn muốn biến đổi mảng thành một cấu trúc dữ liệu khác (object, map, set, v.v.)
- Khi bạn cần thực hiện các phép biến đổi phức tạp mà các phương thức mảng khác không dễ dàng xử lý.

### Kết hợp các Phương thức Mảng

Một trong những điểm mạnh của JavaScript là khả năng kết hợp (chain) các phương thức mảng với nhau để tạo thành các hoạt động xử lý dữ liệu mạnh mẽ.

```javascript
const products = [
  { name: "Laptop", price: 1200, category: "Electronics", inStock: true },
  { name: "Phone", price: 800, category: "Electronics", inStock: false },
  { name: "Shirt", price: 40, category: "Clothing", inStock: true },
  { name: "Pants", price: 60, category: "Clothing", inStock: true },
  { name: "Headphones", price: 200, category: "Electronics", inStock: true },
];

// Lấy tên của tất cả sản phẩm Electronics có sẵn trong kho
const availableElectronicsNames = products
  .filter((product) => product.category === "Electronics") // Lọc danh mục Electronics
  .filter((product) => product.inStock) // Lọc tiếp theo tình trạng kho
  .map((product) => product.name); // Map để lấy tên

console.log(availableElectronicsNames); // ['Laptop', 'Headphones']

// Tính tổng giá trị của tất cả sản phẩm có trong kho
const totalValueInStock = products
  .filter((product) => product.inStock)
  .reduce((total, product) => total + product.price, 0);

console.log(totalValueInStock); // 1500 (1200 + 40 + 60 + 200)
```

### Tóm tắt phương pháp áp dụng Hàm cho tập hợp dữ liệu

| Phương thức | Mục đích                                             | Trả về                   | Khi nào sử dụng                                       |
| ----------- | ---------------------------------------------------- | ------------------------ | ----------------------------------------------------- |
| `forEach()` | Thực thi một hàm cho mỗi phần tử                     | `undefined`              | Khi bạn chỉ muốn duyệt qua và thực hiện một hành động |
| `map()`     | Tạo mảng mới bằng cách biến đổi từng phần tử         | Mảng mới                 | Khi bạn muốn biến đổi mọi phần tử theo cùng một cách  |
| `filter()`  | Tạo mảng mới chỉ chứa các phần tử thỏa mãn điều kiện | Mảng mới                 | Khi bạn cần lọc mảng theo một hoặc nhiều điều kiện    |
| `find()`    | Tìm phần tử đầu tiên thỏa mãn điều kiện              | Phần tử hoặc `undefined` | Khi bạn cần tìm một phần tử cụ thể                    |
| `some()`    | Kiểm tra xem có phần tử nào thỏa mãn điều kiện       | Boolean                  | Khi bạn cần biết "có ít nhất một" phần tử thỏa mãn    |
| `every()`   | Kiểm tra xem tất cả phần tử có thỏa mãn điều kiện    | Boolean                  | Khi bạn cần biết "tất cả" đều thỏa mãn                |
| `reduce()`  | Giảm mảng thành một giá trị duy nhất                 | Giá trị duy nhất         | Khi bạn cần tổng hợp dữ liệu thành kết quả cuối cùng  |

Việc thành thạo các phương thức mảng này và cách kết hợp chúng sẽ giúp bạn viết code xử lý dữ liệu ngắn gọn, dễ đọc và hiệu quả hơn. Thay vì viết những vòng lặp phức tạp với nhiều biến tạm, bạn có thể áp dụng lập trình hàm (functional programming) để biến đổi dữ liệu theo cách khai báo (declarative) thay vì mệnh lệnh (imperative).

---
