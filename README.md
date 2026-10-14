# JMeter-Wikipedia-Test
# Báo cáo: Kiểm thử hiệu năng (Performance Testing) với Apache JMeter

📌 **Thông tin sinh viên**
- **Họ và tên:** Nguyễn Văn Hưng 
- **Mã sinh viên:** 23010095


---

## 1. Mục tiêu kiểm thử
Thực hiện kiểm thử chịu tải (Load Testing) trang chủ của Wikipedia để đánh giá thời gian phản hồi và khả năng xử lý của hệ thống máy chủ.
- **URL mục tiêu:** https://www.wikipedia.org/
- **Công cụ sử dụng:** Apache JMeter 5.6.3

## 2. Thiết lập Kịch bản (Test Plan)
Kịch bản được thiết lập để giả lập nhiều người dùng cùng truy cập vào hệ thống:
- **Number of Threads (Users):** 20 (Giả lập 20 người dùng ảo)
- **Ramp-up period:** 5 giây (Hệ thống đưa toàn bộ 20 người dùng vào trang web trong 5 giây)
- **Loop Count:** 1 (Mỗi người dùng truy cập 1 lần)

**Cấu hình đặc biệt:**
Thêm phần tử `HTTP Header Manager` chứa `User-Agent` của trình duyệt Chrome để giả lập người dùng thật, giúp vượt qua lớp bảo mật chống Bot của Wikipedia (Khắc phục lỗi 403 Forbidden).

<img width="1515" height="842" alt="Screenshot 2026-10-14 111110" src="https://github.com/user-attachments/assets/16079e26-4375-4681-a272-a6ada2b6cbf8" />

## 3. Kết quả kiểm thử
Sau khi thực thi kịch bản, các kết quả thu nhận được hiển thị qua các Listener như sau:

### 3.1. View Results Tree (Chi tiết Request)
Tất cả các request gửi đến Wikipedia đều trả về thành công với `Response code: 200` và `Response message: OK`.

<img width="1513" height="850" alt="Screenshot 2026-10-14 111047" src="https://github.com/user-attachments/assets/5e6ff8ea-fdb4-4d5d-9f9b-2da087e5c830" />

### 3.2. Summary Report (Báo cáo Thống kê)
Bảng dưới đây thống kê các chỉ số hiệu năng tổng quan:
- **Total Samples:** 20 (Tổng số request đã gửi)
- **Error %:** 0.00% (Không có lỗi kết nối nào xảy ra)

<img width="1520" height="847" alt="Screenshot 2026-10-14 111058" src="https://github.com/user-attachments/assets/2e187fa0-c457-485b-9055-2790203202e0" />

## 4. Kết luận
Máy chủ của Wikipedia hoạt động cực kỳ ổn định. Khi giả lập 20 người dùng truy cập đồng thời, hệ thống không phát sinh bất kỳ lỗi nào (Tỉ lệ lỗi 0%). Thời gian phản hồi nhanh và đáp ứng tốt.

