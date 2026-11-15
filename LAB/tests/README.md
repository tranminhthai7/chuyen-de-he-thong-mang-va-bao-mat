# Danh sĂ¡ch vĂ  káº¿t quáº£ kiá»ƒm thá»­ chĂ­nh sĂ¡ch tÆ°á» ng lá»­a (Test Cases)

TĂ i liá»‡u nĂ y ghi nháº­n cĂ¡c ca kiá»ƒm thá»­ kiá»ƒm soĂ¡t truy cáº­p giá»¯a cĂ¡c phĂ¢n vĂ¹ng máº¡ng trong mĂ´ hĂ¬nh lab pfSense.

## BĂ i kiá»ƒm thá»­ 1: Kiá»ƒm soĂ¡t phĂ¢n vĂ¹ng LAN -> DMZ (Cho phĂ©p há»£p lá»‡)

- **ID:** TC01
- **Má»¥c tiĂªu:** Kiá»ƒm tra mĂ¡y khĂ¡ch ná»™i bá»™ LAN truy cáº­p Ä‘Æ°á»£c dá»‹ch vá»¥ Web cĂ´ng khai trĂªn mĂ¡y chá»§ DMZ.
- **Nguá»“n:** Debian-LAN-Client (192.168.1.10)
- **Ä Ă­ch:** Debian-DMZ-Server (192.168.10.10:80)
- **Giao thá»©c / Cá»•ng:** TCP / 80 (HTTP)
- **Ká»³ vá» ng:** CHO PHĂ‰P (Pass). Máy trạm LAN nhận được phản hồi HTTP 200 từ Web Server Nginx.
- **Káº¿t quáº£ thá»±c táº¿:** **PASS**. Lệnh wget -qO- http://192.168.10.10 trả về mã nguồn trang chủ Nginx (<title>Welcome to nginx!</title>). Ping từ LAN sang DMZ đạt 0% packet loss (thời gian phản hồi trung bình ~3.2ms).
- **Tráº¡ng thĂ¡i:** Đạt yêu cầu thiết kế.

---

## BĂ i kiá»ƒm thá»­ 2: CĂ´ láº­p vĂ¹ng DMZ -> LAN (NgÄƒn cháº·n truy cáº­p ngÆ°á»£c)

- **ID:** TC02
- **Má»¥c tiĂªu:** Đảm bảo nguyên tắc bảo mật tối thượng của phân vùng DMZ (DMZ Isolation): máy chủ vùng DMZ bị cách ly, không thể chủ động khởi tạo kết nối hay quét vào mạng nội bộ LAN.
- **Nguá»“n:** Debian-DMZ-Server (192.168.10.10)
- **Ä Ă­ch:** Debian-LAN-Client (192.168.1.10)
- **Giao thá»©c:** ICMP (Ping) / TCP
- **Ká»³ vá» ng:** CHẶN (Default Deny / Block). Tường lửa pfSense chặn đứng toàn bộ gói tin xuất phát từ DMZ đi vào LAN.
- **Káº¿t quáº£ thá»±c táº¿:** **PASS** (Chặn thành công). Lệnh ping 192.168.1.10 từ máy chủ DMZ bị chặn 100% (60 packets transmitted, 0 received, 100% packet loss).
- **Tráº¡ng thĂ¡i:** Đạt yêu cầu thiết kế an toàn phân vùng.
