Deep copy (sao chép sâu 😂) tức là tạo mới một biến có cùng giá trị và được cắt đứt quan hệ hoàn toàn với biến được copy. 

Shallow copy có ý nghĩa rằng sau khi copy, biến mới hoặc các thành phần của biến mới vẫn còn quan hệ  với biến ban đầu 


Tại vì đoạn code này là kiểu dữ liệu hỗn hợp, vậy nên khi được gán giá trị sẽ không được gắn chặt với biến, chúng ta có thể đổi giá trị bản gốc 

<!-- const macbooks = ['macbook2015', { model: 'macbook2014' }, 'macbook2017'];
const apples = [...macbooks];
apples[0] = 'air';
apples[1].model = 'm1';
console.log(macbooks) // ['macbook2015', { model: 'm1' }, 'macbook2017']
console.log(apples) // ['air', { model: 'm1' }, 'macbook2017'] -->
