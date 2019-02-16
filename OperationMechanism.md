Cơ chế hoạt động của Docker 
======================================

#I. Kernel

  - Phản hồi các thông điệp từ phần cứng

  - Khởi tạo và đặt lịch cho các chương trình

  - Quản lú và hệ thống các dịch vụ

  - Truyền tin giữa các chương trình

  - Phân chia tài nguyên, bộ nhơ, CPU, Mạng

#II. Docker

  - Viết bằn ngôn ngữ GO

  - Quản lí các đặt tính của kernel

    + `cgroup`: nhóm các tiến trình

    + `namespace`: chia tách các tầng network

    + `copy-on-write`: định nghĩa image

  - Hướng tiếp cận đã tồn tại vài năm trước khi có docker

  - Docker đơn giản hóa việc viết code cho các hệ thống phân tán

#III. Socket điểù khiển của Docker

  - Docker bao gồm 2 phần: Ckient và sserrver

  - Server nhận lệnh qua socket (qua mạng hoặc qua "file")

  - Client thậm chí có thể được chạy ở trong Docker
