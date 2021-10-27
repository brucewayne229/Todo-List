Event Loop là cơ chế giúp Javascript có thể thực hiện nhiều thao tác cùng một lúc (concurrent model), trước giờ vẫn nghe nói NodeJs có thể xử lý cả hàng ngàn request cùng một lúc mặc dù nó chỉ dùng một thread duy nhất (Single Threaded)

Đoạn code sau chữ Một lại hiện sau chữ Hai tại vì đoạn code chữ Một là một web apis, nó sẽ đẩy qua xử lý ở web apis ( những tác vụ tốn thời gian nếu không xử lý ở web apis sẽ bị block ở Call stack , không thể làm cái khác được) và bắt đầu chạy timeout, cùng lúc đó dòng code sẽ tiếp tục chạy chữ Hai, sau khi chữ Một xong timeout thì sẽ bỏ vào Callback Queue và Event loop sẽ đưa nó vào lại Call stack để tiếp tục thực hiện dòng lệnh console.log đó . Chính vì thế mà chữ Một hiện sau chữ Hai

<!-- 
setTimeout(function() {
console.log('Một');
}, 0);
function second() {
console.log('Hai');
}
second();
 -->