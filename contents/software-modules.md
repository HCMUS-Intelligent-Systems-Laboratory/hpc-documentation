---
label: Kiểm tra trạng thái job
order: 0
---

# **Kiểm tra trạng thái Job***
Sau khi nộp job lên SLURM bằng lệnh `sbatch`, nên kiểm tra danh sách các job đang chạy hoặc đang chờ trong hàng đợi, người dùng có thể sử dụng lệnh:
```
$ squeue -u <username>
```
Để xem thời gian bắt đầu dự kiến cho job đang chờ xử lý:
```
$ squeue -u <username> --start
```
Trường hợp ngay sau khi nộp job bằng `sbatch` mà không thấy job của mình nằm trong hàng đợi, khả năng cao là job đã bị lỗi và cần kiểm tra file output.

# **Các lệnh SLURM thường dùng***
Dưới đây là một số lệnh SLURM phổ biến cần sử dụng:
- `squeue`: Kiểm tra trạng thái của các job.
- `scancel`: Hủy một job đang chạy hoặc trong hàng đợi.
- `scontrol`: Hiển thị thông tin chi tiết về một job cụ thể.
- `sinfo`: Hiển thị thông tin các nodes.

