# Web54-homeWork
Câu 1 :
 * Cách kiểm tra một biến x cho trước là function, array, number, string, undefined
1. String
Sử dụng toán tử typeof var a = "helo" console.log(typeof a); //=> String
2. Null và Undefined
Null luôn được đặt rõ ràng thành một biến
Undefined là giá trị mặc định cho biến chưa được khởi tạo TH sử dụng toá tử typeof console.log(typeof undefined); //=> "undefined" console.log(typeof null); //=> "object" => Lỗi Để kiểm tra Null hoặc Undefined sử dụng toán tử đẳng thức nghiêm ngặt (===) if(a === undefined) {} if(a === null) {}
3. Array Mảng là đối tượng . Nếu sử dụng toán tử typeof sẽ nhận được kết quả là đối tượng. Cách để kiểm tra xem một biến có phải là một mảng hay không bằng cách sử dụng phương thức tĩnh _Array.isArray () _ (IE9 +):
Array.isArray(someVar); Array.isArray([11, 22, 33]); //=> true Array.isArray({}); //=> false

4. Function Function cũng là đối tượng. Tuy nhiên, khác với mảng, có thể kiểm tra các hàm bằng cách sử dụng toán tử typeof: const f = function() {}; console.log(typeof f === 'function'); //=> true

5. Objects So sánh nó với biến tương ứng const a = {}; console.log(a === Object(a)); //=> true

const b = []; console.log(b === Object(b)); //=> true

const c = function() {}; console.log(c === Object(c)); //=> true

const d = 123; console.log(d === Object(d)); //=> false

const e = ''; console.log(e === Object(e)); //=> false

6. Numbers và Booleans Sử dụng toán tử typeof: if (typeof a === 'string') {} if (typeof b === 'boolean') {}

Câu 2 :
Event Loop là cơ chế giúp Javascript có thể thực hiện nhiều thao tác cùng một lúc (concurrent model)

Đoạn code sau chữ Một lại hiện sau chữ Hai tại vì đoạn code chữ Một là một web apis, nó sẽ đẩy qua xử lý ở web apis ( những tác vụ tốn thời gian nếu không xử lý ở web apis sẽ bị block ở Call stack , không thể làm cái khác được) và bắt đầu chạy timeout, cùng lúc đó dòng code sẽ tiếp tục chạy chữ Hai, sau khi chữ Một xong timeout thì sẽ bỏ vào Callback Queue và Event loop sẽ đưa nó vào lại Call stack để tiếp tục thực hiện dòng lệnh console.log đó . Chính vì thế mà chữ Một hiện sau chữ Hai

```
setTimeout(function() {
console.log('Một');
}, 0);
function second() {
console.log('Hai');
}
second();
```

 Câu 3 :
Deep copy tức là tạo mới một biến có cùng giá trị và được cắt đứt quan hệ hoàn toàn với biến được copy : 
```
const obj = {a:1,b:2,c:{d:3}};
const deepClone = JSON.parse(JSON.stringify(obj));
console.log(deepClone); // {a:1,b:2,c:3};
```
Sự hạn chế khi dùng deep copy trong JSON
 Thêm một chi tiết nữa đó là một nhược điểm khi sử dụng deep copy JSON.parse() và JSON.stringify() đó là đôi khi bị miss những tham số của bạn, nêu tham số đó bạn gán underfined hoặc NaN...

 Ví dụ: 
 ```
JSON.parse(
  JSON.stringify({
    a: new Date(),
    b: NaN,
    c: new Function(),
    d: undefined,
    e: function() {},
    f: Number,
    g: false,
    h: Infinity
  })
)
```

Shallow copying nhiệm vụ của nó chỉ copy những giá trị nông nghĩa là nó chỉ sao chép các giá trị đối tượng bình thường nhưng các giá trị lồng nhau vẫn sử dụng reference đến một đối tượng ban đầu : 
```
const obj = {a:1,b:2,c:{d:3}};
const shallowClone = {...obj};
obj.c.d = 34; // chúng ta thay đổi giá trị d của object gốc
console.log(obj); // kết quả cho chúng ta thấy {a:1,b:2,c:{d:34}} 
console.log(shallowClone); // nhưng object mà chúng ta clone ra cũng bị thay đổi theo {a:1,b:2,c:{d:34}} ```



