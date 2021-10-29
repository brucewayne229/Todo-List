# Web54-homeWork
Câu 1 :Sử dụng typeof để kiểm tra một biến x cho trước là function, array, number, string, undefined

Câu 2 :
Event Loop là cơ chế giúp Javascript có thể thực hiện nhiều thao tác cùng một lúc (concurrent model), trước giờ vẫn nghe nói NodeJs có thể xử lý cả hàng ngàn request cùng một lúc mặc dù nó chỉ dùng một thread duy nhất (Single Threaded)

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
 Deep copy (sao chép sâu 😂) tức là tạo mới một biến có cùng giá trị và được cắt đứt quan hệ hoàn toàn với biến được copy. 

Shallow copy có ý nghĩa rằng sau khi copy, biến mới hoặc các thành phần của biến mới vẫn còn quan hệ  với biến ban đầu 


Tại vì đoạn code này là kiểu dữ liệu hỗn hợp, vậy nên khi được gán giá trị sẽ không được gắn chặt với biến, chúng ta có thể đổi giá trị bản gốc 

<!-- const macbooks = ['macbook2015', { model: 'macbook2014' }, 'macbook2017'];
const apples = [...macbooks];
apples[0] = 'air';
apples[1].model = 'm1';
console.log(macbooks) // ['macbook2015', { model: 'm1' }, 'macbook2017']
console.log(apples) // ['air', { model: 'm1' }, 'macbook2017'] -->
