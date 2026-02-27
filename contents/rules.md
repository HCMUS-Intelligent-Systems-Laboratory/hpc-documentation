---
order: -800
---
# **Lưu ý quan trọng khi sử dụng hệ thống**

- Toàn bộ source code và dữ liệu cần được lưu ở đường dẫn `/media/{username}` hoặc `/media02/{username}`
- Tuyệt đối không lưu dữ liệu ở `/home/{username}` do không có nhiều dung lượng lưu trữ tại đây.
- **Lưu ý:** đối với thư mục ẩn (ví dụ như `/home/{username}/.cache`) cũng phải được chuyển qua `/media/{username}`.
- Không chạy bất kỳ chương trình xử lý data / huấn luyện mô hình nào trên các login nodes, vì login nodes không có cấu hình cao, và được nhiều nhóm nghiên cứu sử dụng chung.
- Sau khi hoàn tất sử dụng, ngắt kết nối (ssh), đặc biệt đối với các nhóm sử dụng VSCode, vì nếu không ngắt kết nối sẽ làm chậm kết nối chung của tất cả các nhóm sử dụng.
- Đảm bảo rằng các yêu cầu về tài nguyên được chỉ định chính xác và vừa đủ trước khi gửi job.
- Tính toán thêm 20% cho thời gian dự kiến của job để tránh việc job bị hủy do vượt quá giới hạn thời gian.
- Kiểm tra các thông báo từ SLURM để tối ưu hóa yêu cầu tài nguyên cho các job trong tương lai.
- Thường xuyên backup mã nguồn và dữ liệu (2 ngày / lần), hệ thống có thể sẽ xóa dữ liệu định kỳ (có thông báo trước 3-5 ngày làm việc).
