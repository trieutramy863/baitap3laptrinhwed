
# Bài tập 3 : môn Phát triển ứng dụng trên nền web
# Giảng viên : Đỗ Duy Cốp Lớp học phần
# 58KTPM Ngày giao : 2025-10-24 13:50 Hạn nộp : 2025-11-05 00:00
1. Cài đặt môi trường linux: SV chọn 1 trong các phương án
 - enable wsl: cài đặt docker desktop
 - enable wsl: cài đặt ubuntu
 - sử dụng Hyper-V: cài đặt ubuntu
 - sử dụng VMware : cài đặt ubuntu
 - sử dụng Virtual Box: cài đặt ubuntu
2. Cài đặt Docker (nếu dùng docker desktop trên windows thì nó có ngay)
3. Sử dụng 1 file docker-compose.yml để cài đặt các docker container sau: 
   mariadb (3306), phpmyadmin (8080), nodered/node-red (1880), influxdb (8086), grafana/grafana (3000), nginx (80,443)
4. Lập trình web frontend+backend:
 SV chọn 1 trong các web sau:
 4.1 Web thương mại điện tử
 - Tạo web dạng Single Page Application (SPA), chỉ gồm 1 file index.html, toàn bộ giao diện do javascript sinh động.
 - Có tính năng login, lưu phiên đăng nhập vào cookie và session
   Thông tin login lưu trong cơ sở dữ liệu của mariadb, được dev quản trị bằng phpmyadmin, yêu cầu sử dụng mã hoá khi gửi login.
   Chỉ cần login 1 lần, bao giờ logout thì mới phải login lại.
 - Có tính năng liệt kê các sản phẩm bán chạy ra trang chủ
 - Có tính năng liệt kê các nhóm sản phẩm
 - Có tính năng liệt kê sản phẩm theo nhóm
 - Có tính năng tìm kiếm sản phẩm
 - Có tính năng chọn sản phẩm (đưa sản phẩm vào giỏ hàng, thay đổi số lượng sản phẩm trong giỏ, cập nhật tổng tiền)
 - Có tính năng đặt hàng, nhập thông tin giao hàng => được 1 đơn hàng.
 - Có tính năng dành cho admin: Thống kê xem có bao nhiêu đơn hàng, call để xác nhận và cập nhật thông tin đơn hàng. chuyển cho bộ phận đóng gói, gửi bưu điện, cập nhật mã COD, tình trạng giao hàng, huỷ hàng,...
 - Có tính năng dành cho admin: biểu đồ thống kê số lượng mặt hàng bán được trong từng ngày. (sử dụng grafana)
 - backend: sử dụng nodered xử lý request gửi lên từ javascript, phản hồi về json.
 4.2 Web IOT: Giám sát dữ liệu IOT.
 - Tạo web dạng Single Page Application (SPA), chỉ gồm 1 file index.html, toàn bộ giao diện do javascript sinh động.
 - Có tính năng login, lưu phiên đăng nhập vào cookie và session
   Thông tin login lưu trong cơ sở dữ liệu của mariadb, được dev quản trị bằng phpmyadmin, yêu cầu sử dụng mã hoá khi gửi login.
   Chỉ cần login 1 lần, bao giờ logout thì mới phải login lại.
 - hiển thị giá trị mới nhất của các thông số đang giám sát, khi click vào thì hiển thị đồ thị lịch sử quá trình thay đổi (gọi grafana iframe để hiển thị)
 - backend: Sử dụng nodered để đọc dữ liệu từ các cảm biến (có thể dùng api online để lấy dữ liệu theo giời gian thực), 
   nodered sẽ lưu dữ liệu mới nhất (dạng update) vào cơ sở dữ liệu mariadb (sử dụng phpmyadmin để tạp table và quản trị lần đầu)
   nodered sẽ lưu dữ liệu (insert) vào influxdb để lưu giá trị lịch sử, để cho grafana dùng để hiển thị biểu đồ.
5. Nginx làm web-server
 - Cấu hình nginx để chạy được website qua url http://fullname.com  (thay fullname bằng chuỗi ko dấu viết liền tên của bạn)
 - Cấu hình nginx để http://fullname.com/nodered truy cập vào nodered qua cổng 80, (dù nodered đang chạy ở port 1880)
 - Cấu hình nginx để http://fullname.com/grafana truy cập vào grafana qua cổng 80, (dù grafana đang chạy ở port 3000)

Yêu cầu sinh viên lưu code trên github
có file readme.md có hình ảnh + text: ghi lại nhật ký quá trình làm bài.

CÁCH ĐÁNH GIÁ:
1. Cài đặt được môi trường: 1đ
2. Cài đặt được các docker container với cấu hình phù hợp: 1đ
3. Web chạy được, giao diện phù hợp, chạy trên web sever nginx: 2đ
4. nodered api trả về json, test được: 2đ
5. front-end có js gọi được api nodered, nhận về json, hiển thị được kết quả từ json này. 2đ
6. Bài làm có dấu ấn, giải thích rõ ràng, hiểu vấn đề: 2đ
# Bài Làm 
# 1.Cài đặt môi trường linux sử dụng VMware : cài đặt ubuntu
# <img width="578" height="277" alt="image" src="https://github.com/user-attachments/assets/484b9844-11bc-47bb-a739-422befbd9167" />
# 2. Cài đặt Docker
# <img width="443" height="251" alt="image" src="https://github.com/user-attachments/assets/f00702d9-cd16-4ecc-8697-bf45bc82e207" />
# - Kiểm tra docker có hoạt động hay không:
# <img width="1145" height="656" alt="Screenshot 2025-11-05 160214" src="https://github.com/user-attachments/assets/b462f5f5-2063-438e-b5bd-64d985a54bb7" />
# 3. Sử dụng 1 file docker-compose.yml để cài đặt các docker container sau: 
- Tạo file ocker-compose.yml:
```
services:
  mariadb:
    image: mariadb:latest
    container_name: mariadb
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: root
      MYSQL_DATABASE: iot_db
      MYSQL_USER: myuser
      MYSQL_PASSWORD: 12345
    ports:
      - "3306:3306"
    volumes:
      - mariadb_data:/var/lib/mysql

  phpmyadmin:
    image: phpmyadmin/phpmyadmin
    container_name: phpmyadmin
    restart: always
    depends_on:
      - mariadb
    ports:
      - "8080:80"
    environment:
      PMA_HOST: mariadb
      PMA_USER: myuser
      PMA_PASSWORD: 12345

  nodered:
    image: nodered/node-red
    container_name: nodered
    restart: always
    ports:
      - "1880:1880"
    volumes:
      - nodered_data:/data

  influxdb:
    image: influxdb:latest
    container_name: influxdb
    restart: always
    ports:
      - "8086:8086"
    environment:
      DOCKER_INFLUXDB_INIT_MODE: setup
      DOCKER_INFLUXDB_INIT_USERNAME: myuser
      DOCKER_INFLUXDB_INIT_PASSWORD: 12345
      DOCKER_INFLUXDB_INIT_ORG: myOrg
      DOCKER_INFLUXDB_INIT_BUCKET: iot_bucket
    volumes:
      - influxdb_data:/var/lib/influxdb

  grafana:
    image: grafana/grafana
    container_name: grafana
    restart: always
    ports:
      - "3000:3000"
    depends_on:
      - influxdb
    environment:
      GF_SECURITY_ADMIN_USER: myuser
      GF_SECURITY_ADMIN_PASSWORD: 12345
    volumes:
      - grafana_data:/var/lib/grafana

  nginx:
    image: nginx:latest
    container_name: nginx
    restart: always
    ports:
      - "80:80"
      - "443:443"
    volumes:
      - ./nginx.conf:/etc/nginx/nginx.conf:ro

volumes:
  mariadb_data:
  influxdb_data:
  grafana_data:
  nodered_data:
```
# - cài đặt các docker container mariadb (3306), phpmyadmin (8080), nodered/node-red (1880), influxdb (8086), grafana/grafana (3000), nginx (80,443):

# <img width="1236" height="817" alt="Screenshot 2025-11-05 160411" src="https://github.com/user-attachments/assets/eb1410a4-4d26-478d-bcd6-2a0945f508b9" />

# 4. Lập trình web frontend+backend: # fontend 
- Tạo cơ sở dữ liệu trong phpMyAdmin:
# Tạo cơ sở dữ liệu trong phpMyAdmin
# <img width="1194" height="1199" alt="Screenshot 2025-11-06 232125" src="https://github.com/user-attachments/assets/1a94950c-24ea-4a82-b746-77200d7d5d88" />
# Tạo Nodered để kết nối với MariaDB
# <img width="875" height="496" alt="Screenshot 2025-11-06 230630" src="https://github.com/user-attachments/assets/baa687c0-4bbd-4afd-a47d-147b3dcc44d1" />
# 5. Cấu hình nginx 
```
server {
    listen 80;
    server_name trieutramy.com www.trieutramy.com;

    root /var/www/trieutramy;
    index index.html index.php;

    # ==========================
    # Node-RED reverse proxy
    # ==========================
    location /nodered/ {
        proxy_pass http://localhost:1880/;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }

    # ==========================
    # Grafana reverse proxy
    # ==========================
    location /grafana/ {
        proxy_pass http://localhost:3000/;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
``` 
# - Cấu hình nginx để chạy được website qua url http://trieutramy.com
# <img width="964" height="718" alt="Screenshot 2025-11-06 233729" src="https://github.com/user-attachments/assets/1f635bf0-6635-44d6-b526-da8bdbde765d" />
# - Cấu hình nginx để http://trieutramy.com/nodered 
# <img width="1101" height="660" alt="Screenshot 2025-11-06 233552" src="https://github.com/user-attachments/assets/c731586b-2390-477e-b60c-1601a09b01ad" />
# - Cấu hình nginx để http://trieutramy.com/grafana 
# <img width="791" height="479" alt="Screenshot 2025-11-06 233400" src="https://github.com/user-attachments/assets/ac3568de-d5aa-47ad-9e72-96c65c03f469" />
# 6.Kết Luận
# Qua quá trình thực hiện bài tập, em đã nắm được cách cài đặt Ubuntu trên máy ảo VMware và triển khai các dịch vụ như MariaDB, phpMyAdmin, Node-RED, InfluxDB, Grafana và Nginx thông qua Docker với tệp cấu hình docker-compose.yml. Tất cả các thành phần đều được thiết lập và vận hành ổn định.

Hệ thống website dạng SPA cho phép người dùng đăng nhập, theo dõi dữ liệu cảm biến theo thời gian thực, đồng thời xem lại dữ liệu lịch sử thông qua biểu đồ trên Grafana. Node-RED đóng vai trò thu thập và ghi dữ liệu, trong khi Nginx hoạt động như một web server, giúp truy cập thống nhất thông qua các tên miền được cấu hình sẵn.

Bài làm giúp em hiểu rõ quy trình tích hợp nhiều công nghệ để xây dựng một hệ thống IoT hoàn chỉnh, từ khâu thu thập dữ liệu cho đến xử lý và hiển thị. Đồng thời, em cũng rèn luyện được kỹ năng triển khai thực tế với Docker và cấu hình Nginx, góp phần nâng cao tư duy hệ thống và khả năng triển khai ứng dụng trên môi trường thật.
