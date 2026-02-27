# **Chạy một job đơn giản**

### **Dùng `srun` chạy trực tiếp:**

`srun` là lệnh được dùng để chạy một chương trình hoặc lệnh trực tiếp trên hệ thống tính toán sử dụng SLURM. Khi dùng `srun`, bạn sẽ yêu cầu tài nguyên (CPU, RAM, GPU,...) và SLURM sẽ cấp phát tài nguyên tương ứng để chạy chương trình. `srun` phù hợp cho các tác vụ nhanh, thử nghiệm hoặc chạy tương tác trong môi trường dòng lệnh. Ví dụ được minh họa bên dưới.

- Yêu cầu 4GB RAM và 1 GPU:

```
srun --mem=4G --gres=gpu:1 --pty bash
```
Khi chạy lệnh trên, yêu cầu sẽ vào hàng đợi, nếu SLURM tìm đủ tài nguyên để cấp phát, job này sẽ được khởi chạy và khi đó người dùng sẽ được kết nối đến một trong các compute nodes và truy cập tới vùng tài nguyên được yêu cầu bao gồm 4GB RAM và 1 GPU.

### **Dùng `sbatch` để gửi script:**

`sbatch` là lệnh dùng để gửi một script (thường là file .sh) vào hệ thống SLURM để chạy không đồng bộ. Nghĩa là bạn không cần chờ kết quả ngay trên terminal - hệ thống sẽ xếp hàng, cấp phát tài nguyên khi có thể và chạy script của bạn. `sbatch` phù hợp cho các tác vụ dài, tốn nhiều thời gian, phức tạp hoặc cần nhiều tài nguyên.

Một script SLURM cần phải bao gồm ba phần chính:

- Quy định tài nguyên: Kích thước bộ nhớ, số lượng CPU cores, số nút, thời gian chạy tối đa.

- Thiết lập môi trường: Tải các module cần thiết hoặc kích hoạt môi trường ảo.

- Lệnh thực thi: Lệnh mà người dùng muốn chạy.

Dưới đây là một ví dụ về script SLURM để chạy một chương trình Python:
```
#!/bin/bash
#SBATCH --job-name=myjob           # Tên job
#SBATCH --nodes=1                   # Số lượng compute node cần dùng
#SBATCH --ntasks=1                  # Số lượng tác vụ
#SBATCH --cpus-per-task=1           # Số CPU core trên mỗi tác vụ
#SBATCH --mem-per-cpu=2G            # Bộ nhớ trên mỗi core
#SBATCH --time=00:01:00             # Thời gian chạy tối đa (HH:MM:SS)
module purge
conda activate myenv
python myscript.py                  # Chạy chương trình Python
```

Để gửi một job, người dùng sử dụng lệnh `sbatch`:

```
$ sbatch job.slurm
```

Trong đó `job.slurm` là tên của file script SLURM.
Để kiểm tra kết quả của quá trình chạy script bằng lệnh `sbatch`, các output của các câu lệnh trong script sẽ được ghi vào 1 file `<job_id>.out`.

Lưu ý quan trọng: Để tiến hành huấn luyện một mô hình AI hoặc chạy một script nào đó trên SLURM, bạn nên chạy các câu lệnh của mình bằng lệnh `srun` trước và đảm bảo rằng toàn bộ các câu lệnh trong script của bạn chạy đúng và trả ra kết quả, sau đó bạn đưa các câu lệnh theo đúng trình tự vào script của lệnh sbatch và nộp lên để SLURM xử lý ngầm.