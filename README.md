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

- có thể tải backup và restore để làm tiếp trên giao diện freepbx tại https://drive.google.com/drive/folders/1LZONHrd6VY-OJpJMPSaBeXk-GjJY2nqi
  + 20260411-085251-1775897571-16.0.33-2128775678.tar là của domain công ty
  + 20260411-100814-1775902094-16.0.33-1667844990.tar là của domain giả lập số điện thoại bên ngoài
  + lưu ý: cần sử dụng freepbx phiên bản 16.0.33, distro: SNG7-PBX16-64bit-2302-1.iso
  + cách restore: admin->backup&restore->restore->upload your restore file
