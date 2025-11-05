# baitap3laptrinhwed
# Bài tập 3 : môn Phát triển ứng dụng trên nền web Giảng viên : Đỗ Duy Cốp Lớp học phần: 58KTPM Ngày giao : 2025-10-24 13:50 Hạn nộp : 2025-11-05 00:00
# Yêu cầu : LẬP TRÌNH ỨNG DỤNG WEB trên nền linux

Cài đặt môi trường linux: SV chọn 1 trong các phương án
enable wsl: cài đặt docker desktop
enable wsl: cài đặt ubuntu
sử dụng Hyper-V: cài đặt ubuntu
sử dụng VMware : cài đặt ubuntu
sử dụng Virtual Box: cài đặt ubuntu
Cài đặt Docker (nếu dùng docker desktop trên windows thì nó có ngay)
Sử dụng 1 file docker-compose.yml để cài đặt các docker container sau: mariadb (3306), phpmyadmin (8080), nodered/node-red (1880), influxdb (8086), grafana/grafana (3000), nginx (80,443)
Lập trình web frontend+backend:
# Web thương mại điện tử
# Tạo web dạng Single Page Application (SPA), chỉ gồm 1 file index.html, toàn bộ giao diện do javascript sinh động.
Có tính năng login, lưu phiên đăng nhập vào cookie và session Thông tin login lưu trong cơ sở dữ liệu của mariadb, được dev quản trị bằng phpmyadmin, yêu cầu sử dụng mã hoá khi gửi login. Chỉ cần login 1 lần, bao giờ logout thì mới phải login lại.
Có tính năng liệt kê các sản phẩm bán chạy ra trang chủ
Có tính năng liệt kê các nhóm sản phẩm
Có tính năng liệt kê sản phẩm theo nhóm
Có tính năng tìm kiếm sản phẩm
Có tính năng chọn sản phẩm (đưa sản phẩm vào giỏ hàng, thay đổi số lượng sản phẩm trong giỏ, cập nhật tổng tiền)
Có tính năng đặt hàng, nhập thông tin giao hàng => được 1 đơn hàng.
Có tính năng dành cho admin: Thống kê xem có bao nhiêu đơn hàng, call để xác nhận và cập nhật thông tin đơn hàng. chuyển cho bộ phận đóng gói, gửi bưu điện, cập nhật mã COD, tình trạng giao hàng, huỷ hàng,...
Có tính năng dành cho admin: biểu đồ thống kê số lượng mặt hàng bán được trong từng ngày. (sử dụng grafana)
backend: sử dụng nodered xử lý request gửi lên từ javascript, phản hồi về json.
Nginx làm web-server
Cấu hình nginx để chạy được website qua url http://fullname.com (thay fullname bằng chuỗi ko dấu viết liền tên của bạn)
Cấu hình nginx để http://fullname.com/nodered truy cập vào nodered qua cổng 80, (dù nodered đang chạy ở port 1880)
Cấu hình nginx để http://fullname.com/grafana truy cập vào grafana qua cổng 80, (dù grafana đang chạy ở port 3000) Yêu cầu sinh viên lưu code trên github có file readme.md có hình ảnh + text: ghi lại nhật ký quá trình làm bài. CÁCH ĐÁNH GIÁ:
Cài đặt được môi trường: 1đ
Cài đặt được các docker container với cấu hình phù hợp: 1đ
Web chạy được, giao diện phù hợp, chạy trên web sever nginx: 2đ
nodered api trả về json, test được: 2đ
front-end có js gọi được api nodered, nhận về json, hiển thị được kết quả từ json này. 2đ
Bài làm có dấu ấn, giải thích rõ ràng, hiểu vấn đề: 2đ
# Bài Làm 
# 1.Cài đặt môi trường linux sử dụng VMware : cài đặt ubuntu
# <img width="578" height="277" alt="image" src="https://github.com/user-attachments/assets/484b9844-11bc-47bb-a739-422befbd9167" />
# 2. Cài đặt Docker
# <img width="443" height="251" alt="image" src="https://github.com/user-attachments/assets/f00702d9-cd16-4ecc-8697-bf45bc82e207" />
# - Kiểm tra docker có hoạt động hay không:
# <img width="1145" height="656" alt="Screenshot 2025-11-05 160214" src="https://github.com/user-attachments/assets/b462f5f5-2063-438e-b5bd-64d985a54bb7" />
# 3. Sử dụng 1 file docker-compose.yml để cài đặt các docker container sau: - Tạo file ocker-compose.yml:
# <img width="995" height="617" alt="Screenshot 2025-11-05 160311" src="https://github.com/user-attachments/assets/27e28d28-5dbb-4cbb-acba-cf272cd77e4c" />
# - cài đặt các docker container mariadb (3306), phpmyadmin (8080), nodered/node-red (1880), influxdb (8086), grafana/grafana (3000), nginx (80,443):
# <img width="1236" height="817" alt="Screenshot 2025-11-05 160411" src="https://github.com/user-attachments/assets/eb1410a4-4d26-478d-bcd6-2a0945f508b9" />
# 4. Lập trình web frontend+backend: # fontend - Tạo cơ sở dữ liệu trong phpMyAdmin:
# 5. Cấu hình nginx để chạy được website qua url http://fullname.com
# <img width="1280" height="592" alt="image" src="https://github.com/user-attachments/assets/67d5a581-9000-477d-9df7-893b2f34817b" />
# - Cấu hình nginx để chạy được website qua url http://fullname.com
# <img width="1280" height="592" alt="image" src="https://github.com/user-attachments/assets/74bea5fb-a67a-46b8-80b5-dad0c6f594e6" />
# - Cấu hình nginx để http://fullname.com/nodered truy cập vào nodered qua cổng 80
# <img width="1280" height="592" alt="image" src="https://github.com/user-attachments/assets/19857e62-3827-44d3-8b0e-525f2fcf4d61" /> 
# 
# 

