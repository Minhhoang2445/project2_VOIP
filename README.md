- làm việc với các file:
  + Dialplan:	extensions.conf, extensions_custom.conf, extensions_additional.conf
  + SIP/PJSIP:	pjsip.conf, sip.conf, pjsip.endpoint.conf, pjsip.auth.conf
  + Voicemail:	voicemail.conf
  + RTP:	rtp.conf
  + Queue:	queues.conf
  + lưu ý: thư mục cấu hình custom dùng để viết logic riêng cho hệ thống Asterisk mà không bị FreePBX ghi đè. Không chỉnh sửa các file auto-generate của FreePBX
  Chỉ viết logic trong các file *_custom.conf

các quy trình đã làm:
- tạo 2 domain: 1 là của nội bộ công ty, 1 là giả lập số điện ở bên ngoài
- tạo sip trunk trên 2 domain để nối 2 domain lại với nhau
- ở domain của nội bộ công ty tạo một inbound route với DID là 0952014302 và để destination là 6026 tức là khi có số từ ngoài gọi vào 0952014302 sẽ nối máy đến 6026
- ở domain của bên ngoài công ty tạo một outbound route với trunk TO-A để gọi vào domain của công ty
- tạo 1 số conference 4024 khi gọi vào số này sẽ yêu được nhập mật khẩu để tham gia

backup&store:
- có thể tải backup và restore để làm tiếp trên giao diện freepbx tại https://drive.google.com/drive/folders/1LZONHrd6VY-OJpJMPSaBeXk-GjJY2nqi
  + 20260411-085251-1775897571-16.0.33-2128775678.tar là của domain công ty
  + 20260411-100814-1775902094-16.0.33-1667844990.tar là của domain giả lập số điện thoại bên ngoài
  + lưu ý: cần sử dụng freepbx phiên bản 16.0.33, distro: SNG7-PBX16-64bit-2302-1.iso
  + cách restore: admin->backup&restore->restore->upload your restore file
------------------------------------------------------------------------------------------------------------------------------------
lần sửa thứ 2 update lần 2 của Phước:
## 📁 Danh sách toàn bộ các file đã chỉnh sửa

### 🖥️ 1. Thư mục `CongTy` (Máy 1 - 10.23.96.161)
Các file chứa kịch bản bóc phím 9, cấu hình Trunk và Network đã cập nhật:
* **`backup_May1_HoanThien.tar.gz`** (File Backup toàn diện hệ thống)
* `extensions_additional.conf` (Luật gọi ra/vào và bóc phím 9)
* `pjsip.endpoint.conf` (Thông số điểm cuối của Trunk TO-B)
* `pjsip.aor.conf` (Thông số định danh tài khoản Trunk)
* `sip_general_additional.conf` (Cấu hình NAT và mạng LAN)
* `manager.conf` (Quyền truy cập quản trị viên)
* `ari_additional.conf` (Giao diện REST Asterisk)
* `iax_general_additional.conf` (Cấu hình giao thức IAX chung)
* `res_odbc_additional.conf` (Kết nối cơ sở dữ liệu)

### 🖥️ 2. Thư mục `BenNgoai` (Máy 2 - 10.23.96.141)
Bao gồm file backup và toàn bộ 42 file cấu hình tùy chỉnh (`_custom.conf`) đã được cập nhật đồng bộ:
* **`backup_May2_HoanThien.tar.gz`** (File Backup toàn diện hệ thống)
* **Các file Custom (Force Update):**
  - `ari_additional_custom.conf`, `ari_general_custom.conf`
  - `cel_general_custom.conf`, `cel_odbc_custom.conf`
  - `confbridge_custom.conf`
  - `extconfig_custom.conf`
  - `extensions_custom.conf`
  - `features_applicationmap_custom.conf`, `features_featuremap_custom.conf`, `features_general_custom.conf`
  - `globals_custom.conf`, `http_custom.conf`
  - `iax_custom.conf`, `iax_general_custom.conf`, `iax_registrations_custom.conf`
  - `indications_custom.conf`, `indications_general_custom.conf`
  - `logger_general_custom.conf`, `logger_logfiles_custom.conf`
  - `manager_custom.conf`
  - `meetme_general_custom.conf`, `musiconhold_custom.conf`
  - `pjsip.aor_custom.conf`, `pjsip.auth_custom.conf`, `pjsip.endpoint_custom.conf`, `pjsip.identify_custom.conf`, `pjsip.registration_custom.conf`, `pjsip.transports_custom.conf`
  - `pjsip_custom.conf`, `pjsip_custom_post.conf`
  - `queuerules_custom.conf`, `queues_custom.conf`, `queues_post_custom.conf`
  - `res_fax_custom.conf`, `res_fax_digium_custom.conf`, `res_odbc_custom.conf`, `res_parking_custom.conf`
  - `rtp_custom.conf`
  - `sip_custom.conf`, `sip_general_custom.conf`, `sip_notify_custom.conf`, `sip_registrations_custom.conf`
  - `udptl_custom.conf`

---
