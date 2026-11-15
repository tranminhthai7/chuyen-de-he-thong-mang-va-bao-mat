# MĂ´i trÆ°á» ng Thá»±c nghiá»‡m (LAB Environment)

ThÆ° má»¥c nĂ y lÆ°u trá»¯ cĂ¡c tĂ i liá»‡u thiáº¿t káº¿ thá»±c nghiá»‡m, kĂªnh kiá»ƒm tra vĂ  káº¿t quáº£ Ä‘Ă¡nh giĂ¡ an toĂ n máº¡ng trĂªn há»‡ thá»‘ng tÆ°á» ng lá»­a **pfSense**.

---

## 1. ThĂ nh pháº§n Há»‡ thá»‘ng Thá»±c nghiá»‡m

| ThĂ nh pháº§n | Há»‡ Ä‘iá» u hĂ nh / Dá»‹ch vá»¥ | PhĂ¢n vĂ¹ng máº¡ng | IP Cáº¥u hĂ¬nh | Chá»©c nÄƒng |
|:---|:---|:---|:---|:---|
| **pfSense-FW** | pfSense CE 2.9.0-RELEASE | Firewall Gateway | Multi-interface | Ä iá» u phá»‘i, Ä‘á»‹nh tuyáº¿n vĂ  lá» c gĂ³i tin giá»¯a cĂ¡c vĂ¹ng |
| **Debian-DMZ-Server** | Debian GNU/Linux 13 (Trixie) / Nginx | DMZ | 192.168.10.10/24 | MĂ¡y chá»§ Web demo cung cáº¥p dá»‹ch vá»¥ HTTP |
| **Debian-LAN-Client** | Debian GNU/Linux 13 (Trixie) | LAN | 192.168.1.10/24 | MĂ¡y tráº¡m ngÆ°á» i dĂ¹ng ná»™i bá»™ kiá»ƒm thá»­ |
| **Management Host** | Windows 11 / TrĂ¬nh duyá»‡t Web | MGMT (Host-Only) | 192.168.56.1/24 | Quáº£n trá»‹ tÆ°á» ng lá»­a qua pfSense WebConfigurator |

---

## 2. TiĂªu chĂ­ An toĂ n vĂ  CĂ´ láº­p MĂ´i trÆ°á» ng
- ToĂ n bá»™ cĂ¡c káº¿t ná»‘i giá»¯a cĂ¡c mĂ¡y áº£o thá»±c nghiá»‡m Ä‘á» u sá»­ dá»¥ng card **Internal Network** cĂ´ láº­p hoĂ n toĂ n trong pháº¡m vi VirtualBox.
- KhĂ´ng sá»­ dá»¥ng Bridged Adapter trá»±c tiáº¿p vĂ o máº¡ng váº­t lĂ½ bĂªn ngoĂ i, khĂ´ng Ä‘Æ°a dá»¯ liá»‡u tháº­t hoáº·c lÆ°u lÆ°á»£ng cĂ´ng cá»™ng vĂ o phĂ¢n vĂ¹ng kiá»ƒm thá»­.
- Ă p dá»¥ng nguyĂªn táº¯c **Default Deny** (Tá»« chá»‘i máº·c Ä‘á»‹nh) vĂ  **Least Privilege** (Ä áº·c quyá» n tá»‘i thiá»ƒu) cho má» i quy táº¯c lá» c gĂ³i.

---

## 3. Danh má»¥c Káº¿t quáº£ Kiá»ƒm thá»­
Chi tiáº¿t cĂ¡c ca kiá»ƒm thá»­ vĂ  báº±ng chá»©ng Ä‘Ă¡nh giĂ¡ an ninh Ä‘Æ°á»£c trĂ¬nh bĂ y táº¡i:
- **[Káº¿t quáº£ kiá»ƒm thá»­ chĂ­nh sĂ¡ch tÆ°á» ng lá»­a](tests/README.md)**: Ghi nháº­n cĂ¡c ca kiá»ƒm thá»­ phĂ¢n vĂ¹ng LAN -> DMZ (Pass) vĂ  DMZ -> LAN (Block).
