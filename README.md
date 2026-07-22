# ỨNG DỤNG CÁC KỸ THUẬT REVERSE ENINEERING VÀO PHẦN MỀM HTMLPAD 2025

Dự án tập trung vào việc nghiên cứu cơ chế bảo mật bản quyền cục bộ và kỹ thuật kiểm tra tính toàn vẹn (Integrity Check) trên ứng dụng Windows 32-bit, cụ thể là phần mềm biên tập mã nguồn HTMLPad 2025. Thông qua việc phân tích động và áp dụng kỹ thuật vá mã nhị phân (Binary Patching), dự án hướng tới mục tiêu vô hiệu hóa giới hạn dùng thử mà vẫn đảm bảo tính toàn vẹn và ổn định của hệ thống.

---

##  Mục tiêu Đề tài

* **Kiến thức cốt lõi:** Hệ thống hóa và củng cố nền tảng về Dịch ngược phần mềm (Reverse Engineering), cấu trúc cấu trúc tệp thực thi `PE` (Portable Executable) trên Windows và ngôn ngữ hợp ngữ (`Assembly`).
* **Kỹ năng thực hành:** Nghiên cứu và ứng dụng thành thạo trình gỡ rối x32dbg trong việc phân tích động, theo dõi luồng thực thi hệ thống, giám sát bộ nhớ và các thanh ghi.
* **Ứng dụng thực tiễn:** Đánh giá cơ chế bảo mật của phần mềm thương mại thực tế; thấu hiểu và đưa ra giải pháp vô hiệu hóa cơ chế giới hạn dùng thử (`Trial limit`) cũng như cơ chế tự bảo vệ chống can thiệp (`Anti-tampering / Integrity check`).

##  Phạm vi & Giới hạn Kỹ thuật

* **Đối tượng & Môi trường:** Phân tích các tệp thực thi định dạng PE32 (32-bit) trên hệ điều hành Windows. Đối tượng thực nghiệm chính là HTMLPad 2025.
* **Phương pháp tiếp cận:** Phân tích động bằng Debugger (x32dbg) và sửa đổi trực tiếp mã Hex (Binary Patching) tại các lệnh nhảy (Jump instructions) và thanh ghi cờ (Flag registers).
* **Giới hạn nghiên cứu:** Tập trung vào bẻ khóa giới hạn cấp phép cục bộ (Local license checking) và vô hiệu hóa cơ chế tự kiểm tra toàn vẹn tệp. Dự án không đi sâu vào các kỹ thuật bảo vệ nâng cao như ảo hóa mã lệnh (Themida, VMProtect), làm rối mã sâu (Obfuscation), hoặc xác thực qua mạng (Network Authentication).

##  Kết quả Đạt được

* **Sản phẩm thực nghiệm (`htmlpad-1.exe`):** Định vị thành công các hàm kiểm tra bản quyền. Tệp thực thi sau khi vá mã hoạt động ổn định, mở khóa toàn bộ tính năng biên tập, loại bỏ hoàn toàn giới hạn 30 lần sử dụng và không bị thoát đột ngột bởi cơ chế chống sửa đổi ("corrupt file").
* **Giải pháp kỹ thuật tiêu biểu:** Vận dụng tư duy linh hoạt trong xử lý cơ chế thoát ẩn của phần mềm thông qua việc chuyển đổi phương pháp tìm kiếm luồng lệnh từ bắt sự kiện Windows Messages sang phân tích cấu trúc Call Stack với điểm dừng tại hàm `ExitProcess`.
* **Tài liệu hóa:** Hoàn thiện báo cáo học thuật chi tiết với hình ảnh minh họa từng bước thao tác, đóng vai trò làm tài liệu tham khảo cho việc học tập và nghiên cứu Reverse Engineering cơ bản.
