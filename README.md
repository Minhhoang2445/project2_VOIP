- làm việc với các file:
  + Dialplan:	extensions.conf, extensions_custom.conf, extensions_additional.conf
  + SIP/PJSIP:	pjsip.conf, sip.conf, pjsip.endpoint.conf, pjsip.auth.conf
  + Voicemail:	voicemail.conf
  + RTP:	rtp.conf
  + Queue:	queues.conf
- tạo 2 domain: 1 là của nội bộ công ty, 1 là giả lập số điện ở bên ngoài
- tạo sip trunk trên 2 domain để nối 2 domain lại với nhau
- ở domain của nội bộ công ty tạo một inbound route với DID là 0952014302 và để destination là 6026 tức là khi có số từ ngoài gọi vào 0952014302 sẽ nối máy đến 6026
- ở domain của bên ngoài công ty tạo một outbound route với trunk TO-A để gọi vào domain của công ty
