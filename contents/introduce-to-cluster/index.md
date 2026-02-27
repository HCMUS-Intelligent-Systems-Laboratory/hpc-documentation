# **Khái niệm và yêu cầu cơ bản**

### **Các khái niệm cơ bản**

- Job: Tác vụ hoặc chương trình bạn muốn hệ thống chạy.

- Node: Một máy tính riêng biệt trong cụm máy (cluster).

### **Yêu cầu cơ bản để sử dụng SLURM**

Trước khi bắt đầu, người dùng cần nắm vững một số kiến thức cơ bản về Linux và cái nhìn tổng quan về hệ thống HPC.

Hệ thống server HPC hiện tại bao gồm: 

- 02 login nodes: chỉ dùng để đăng nhập thông qua ssh, lưu trữ mã nguồn và dữ liệu, nộp job lên các compute nodes, không dùng cho việc chạy task/job xử lý dữ liệu hoặc huấn luyện mô hình.

    + Node login01 có IP: 172.29.74.80

    + Node login02 có IP: 172.29.74.81

- 05 compute nodes: có nguồn tài nguyên lớn bao gồm CPUs, RAM và GPUs, được điều phối tự động thông qua SLURM để chạy các task/job, người dùng không thể đăng nhập hay kết nối trực tiếp đến các compute nodes.

    + gpu01, gpu02, gpu03, gpu04, gpu05