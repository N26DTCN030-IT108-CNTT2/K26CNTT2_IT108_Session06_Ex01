\#BÀI 1

\## Phần 1 Phân tích:

Giải thích tại sao lệnh cat hiển thị quá nhiều dữ liệu và lý do không nên mở file 500MB bằng Notepad:



Nguyên nhân lệnh cat (trong PowerShell thực chất là alias của Get-Content) hiển thị tràn màn hình: Lệnh này thực hiện việc đọc toàn bộ nội dung tệp tin rồi đổ trực tiếp ra luồng xuất chuẩn (stdout) một cách liên tục mà không có cơ chế ngắt trang hay phân đoạn. Đối với một tệp log dung lượng lớn (500MB), Terminal sẽ bị quá tải vì phải xử lý hàng triệu dòng văn bản cùng lúc, dẫn đến việc bị đơ (frozen) và người dùng không thể tìm thấy thông tin lỗi cần thiết.



Lý do không nên mở file 500MB bằng Notepad: Các trình soạn thảo văn bản giao diện đồ họa (GUI) như Notepad cố gắng nạp toàn bộ nội dung tệp (500MB) trực tiếp vào bộ nhớ RAM cùng một lúc để render giao diện. Điều này sẽ làm cạn kiệt tài nguyên RAM tức thời của máy tính, gây ra hiện tượng tràn bộ nhớ, treo cứng ứng dụng ("Not Responding") và làm sập chương trình.



Phần 2 Hoàn thiện:

Lệnh PowerShell để xem toàn bộ file theo từng trang (từng màn hình một):

Get-Content server\_log\_500MB.log | more

Lệnh PowerShell để chỉ xem 10 dòng cuối cùng nhằm tìm lỗi mới nhất:

Get-Content server\_log\_500MB.log -Tai

