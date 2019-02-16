Hướng dẫn cài đặt docker
========================================

#I. Giới thiệu docker

  - Docker là 1 dự án mã nguồn mở trên github

  - Docker tạo ra các container cho các ứng dụng phần mềm

  -  Vận chuyển container

  - Chia sẽ container

  - Khẩu quyết 1 của Docker: `Build, ship, deploy, any application, any where`:
    
    + Build: Đóng gói ứng dụng trong một container

    + Ship: vận chuyển container

    + Deploy: triển khai, chạy container

    + Bất cứ ứng dụng nào chạy được trên linux

    + Tất cả mọi nơi: laptop, máy chủ, máy ảo, cloud instance,...

    + Đóng gói phần mềm dể dàng

    + Deploy nhanh

    + Không cần cấu hình và cài đặt môi trường rườm rà.

    + Image: component để triển khai ứng dụng bao gồm mã nguồn, thư viện, framework, file,...

    + Trừu tượng hóa giải pháp và đóng gói vào một image kèm dependencies

      - => Tránh conflict môi trường triển khai

  - Khẩu quyết 2 của docker:

    + Batteries included but replaceable:

      - Một componet có thể được thay thế bằng cách implement cùng một interface có sẵn

      - Docker framework được phân chia thành các modun có khả năng mở rộng cao

  - Một số thuật ngữ 

    + Image: 

      - Khuôn mẫu, lớp chứa các file cần thiết để tạo nên 1 container

      - Chứa những tài nguyên có sẵn

      - Không được tiếp cận vào CPU, memory, storage,...

    + Container:

      - Tồn tại trên host với 1 IP

      - Được deploy, chạy, và xóa bỏ thông qua remote client     

    + Docker engine là 1 phần của docker

      - Dùng để tạo và chạy container

      - Chạy lệnh trong chế độ deamon

      - Linux trở thành máy chủ docker

      - Container được deploy, chạy, xóa bỏ thông qua remote client

    + Docker deamon

      - Tiến trình chạy ngầm quản lý các container

    + Docker client

      - Kiểm soát hầu hết các workfow của docker

      - Giao tiếp với các máy chủ Docker thông qua deamon

    + Docker Hub (Registry)

      - Chứa các component Docker

      - Cho phép lưu, sử dụng, tìm kiếm image

      - Vai trò "ship" trong "build, ship, deploy"

II. Điểm mạnh của Docker

  - Deploy nhanh hơn:

    + Hệ thống augmented file system

    + Thêm các layer bên trên root kernel

    + Dễ dàng tổng hợp các layer lại thành 1

  - TÍnh cơ động:

    + Tránh conflict môi trường

  - Tính đọc lập:

    + Lỗi xảy ra với 1 container không ảnh hưởng các container khác

  - CHụp ảnh sự lẫn nhau giữa các ứng dụng

    + Lưu snapshot thành contaoner hoặc image 

    + Tag

    + Tạo container y hệt từ snapshot

  - Kiểm soát việt sử dụng tài nguyên (CPU, RAM, storage,...)

  - Đơn giản hóa sự phụ thuộc lẫn nhau giữa các ứng dụng (dependency)

    + Xác định dependency ở Dockerfile

  - Thuận tiện cho việc chia sẻ

    + Docker hub (public / private registry) 

    + Dockerfile
#III. Một số lầm tưởng về Docker

  - Không phải công cụ quản lý thiết lập hay thiết lập tự động (puppet, Chef,..)

  - Không phải giải pháp ảo hóa phần cứng (VMware, KVM,...)

  - Không phải là 1 nền tảng điện toán đám mây (Open stack, Cloud Stack,...)

  - Không phải là một deployment framework (Capistrano, Fabric,...)

  - Không phải là công cụ quản lú workload (Mesos, Fleet,...)

  - Không phải là một môi trường phát triển (Vagrant,...)

#IV. SO sánh docker và Virtual Machine
  
  |           VM                                                  |                                                          Docker                               |
  |---------------------------------------------------------------|-----------------------------------------------------------------------------------------------|
  |Công nghệ ảo hóa                                               | Công nghệ container hóa                                                                       |
  |Chạy hệ điều hành reeng bên trong một môi trường phần cứng giả lập được cung cấp bởi hypervisor chạy trên phần cứng vật lý |Contianer hóa cho phép nhiều ứng dụng chạy trên partition đọc lập trên Linux kernel, và chạy trực tiếp trên phần cứng vật lý                                                                |
  |Kernel riêng                                                   |Kernel chung với hệ điều hành|
  |Khởi động cả hệ điều hành  | Khởi động một số process|
  |TỐc độ chậm| Tốc độ nhanh|
  |Cần nhiều tài nguyên|Tiết kiệm tài nguyên|

  - Lựa chọn giữa Docker và VM:
    
    + VM: phân tach tài nguyên phần cứng rõ ràng

    + Docker: phân tách tài nguyên tương đối, ứng dụng đóng gói dể dàng kèm dependency

#V. Kiến trúc Docker

  - Kiến trúc client-server

  - Ba thành phần chính:

    + Docker client

    + Docker Host

    + Docker Registry (Hub)

  - Docker Deamon nhận lệnh từ Docker Client thông qua CLI hoặc Rest API

  - Docker Client ở trên cùng host hoặc khác host với Docker Deamon

  - Docker Hub: Dịch vụ lưu trữ, chia sẽ image

  - Nhiều contianer có thể liên kết với nhau đê tạo kiến trức ứng dụng đa tầng

  - Nếu đóng gói contaienr và chưa commit thì mọi thay đổi trên contianer sẽ bị mất

#VI. Các công cụ

  - DOcker toolbox: Là một bộ cài đặt Docker cho môi trường windown và Mac dành riêng cho những thiết bị không đạt yêu cầu để cài bộ cài đặt mới

    + Bao gồm các công cụ: 

      - Docker machien: Quản lý host bằng các lệnh docker-machine

      - Docker Engine: Chạy các lệnh docker

      - Docker compose: thiết lập việc chạy nhiêu container trong docker

      - Kitematic: giao diện hiển thị cho Docker

      - Shell thiết lập sẵn để phục vụ cho môi trường command-line trên Docker

      - Oracel Virtualbox: giả lập môi trường linux để chạy docker

    + DOcker machine: 

      - Công cụ giúp cài đặt Docker Engine trên các host ảo
      
      - QUản lý các host đó bằng lệnh docker-machine

      - Từng là cách duy nhất để chạy Docker trên windowws và mac trước phiên bản Docker 1.12

        + Docker machine dùng để làm gì?

          - Máy thuộc hệ điều hành WIndown hoặc Mac đời cũ

          - Tạo docker host trên các hẹ thống remote

            + Cài đặt docker machine trên Windows, Linux, Mac

            + Mỗi host machine = 1 docker host + 1 docker client

  - So ssanh Docker Engine và Docker Machine

    | Docker engine | Docker machine |
    |---------------|----------------|
    | Mô hình client-server| Quản lí docker host|
    | Tạo bởi docker deamon, Rest API, Docker client cli| Cài đặt  Docker Engine lên một hoặc nhiều máy ảo trên máy|

  - Docker hub là gì ?

    + Dịch vụ registry trên cloud

    + Kết nối code reponsitory, build, test và deploy image

    + Cung cấp tài nguyên một cách tập trung cho việc tìm kiếm image, phân phối và quản lý thay đổi của image

    + Devops và developer có thể dùng các image một cách tự động và theo flow

  - Tính năng docker hub

    + Image repository: tìm kiếm, lưu trữ, push và pull image cho cộng ddoodngf người dùng docker

    + BUild tự động: Build những image khi có sự thay đổi code của sản phẩm

    + Webhook: là một tính năng của tự động build, webhoook thông báo cho bạn biết khi có push thành công lên một reponsitory

    + Tổ chức: tạo nhóm làm việc để quản lý truy cập vào image reponsitory

    + Tích hợp Github và bitbucket

