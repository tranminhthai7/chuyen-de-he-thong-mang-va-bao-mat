# ChuyĂªn Ä‘á»  Há»‡ thá»‘ng Máº¡ng vĂ  Báº£o máº­t: Thiáº¿t káº¿ vĂ  Ä Ă¡nh giĂ¡ MĂ´ hĂ¬nh TÆ°á» ng lá»­a pfSense

## 1. Giá»›i thiá»‡u Ä‘á»  tĂ i
- **TĂªn Ä‘á»  tĂ i:** Thiáº¿t káº¿ vĂ  Ä‘Ă¡nh giĂ¡ mĂ´ hĂ¬nh tÆ°á» ng lá»­a pfSense cho máº¡ng doanh nghiá»‡p nhá»  vá»›i phĂ¢n vĂ¹ng LAN/DMZ vĂ  kiá»ƒm soĂ¡t truy cáº­p.
- **Má»¥c tiĂªu:** XĂ¢y dá»±ng há»‡ thá»‘ng máº¡ng an toĂ n sá»­ dá»¥ng tÆ°á» ng lá»­a mĂ£ nguá»“n má»Ÿ **pfSense**, thá»±c hiá»‡n phĂ¢n tĂ¡ch cĂ¡c vĂ¹ng máº¡ng (Segmentation), triá»ƒn khai vĂ¹ng phi quĂ¢n sá»± (**DMZ**) chá»©a mĂ¡y chá»§ Web Nginx vĂ  thá»±c thi chĂ­nh sĂ¡ch kiá»ƒm soĂ¡t truy cáº­p theo nguyĂªn táº¯c Ä‘áº·c quyá» n tá»‘i thiá»ƒu (Least Privilege) vĂ  tá»« chá»‘i máº·c Ä‘á»‹nh (Default Deny).

---

## 2. Kiáº¿n trĂºc vĂ  SÆ¡ Ä‘á»“ MĂ´ hĂ¬nh Máº¡ng (Topology)

`	ext
               +--------------------------------------+
               |      MĂY CHá»¦ QUáº¢N TRá»Š WINDOWS       |
               |      (Host-Only: 192.168.56.1)       |
               +------------------+-------------------+
                                  | (HTTPS WebGUI)
                                  v
+-----------------------+  [em3 / OPT2]
|   MĂY KHĂCH OUTSIDE   |  192.168.56.2
| (Internal: 'OUTSIDE') |
+-----------+-----------+
            | [em0 / WAN]
            v
+-----------------------------------------------------+
|                  TÆ¯á»œNG Lá»¬A pfSense                 |
+-----------+-----------------------------+-----------+
            | [em1 / LAN]                 | [em2 / OPT1 (DMZ)]
            | 192.168.1.1/24              | 192.168.10.1/24
            v                             v
+-----------------------+     +-----------------------+
|   Debian-LAN-Client   |     |   Debian-DMZ-Server   |
|  (Internal: 'LAN')    |     |  (Internal: 'DMZ')    |
|     192.168.1.10      |     |     192.168.10.10     |
| (MĂ¡y tráº¡m ná»™i bá»™)    |     |   (Web Server Nginx)  |
+-----------------------+     +-----------------------+
`

---

## 3. Báº£ng PhĂ¢n Bá»• Ä á»‹a Chá»‰ IP (IP Plan)

| VĂ¹ng máº¡ng | TĂªn Interface (pfSense) | Kiá»ƒu Card VirtualBox | Ä á»‹a chá»‰ Subnet | Gateway | Vai trĂ² chĂ­nh |
|:---|:---|:---|:---|:---|:---|
| **WAN / OUTSIDE** | em0 (WAN) | Internal Network OUTSIDE | - | - | MĂ´ phá» ng máº¡ng bĂªn ngoĂ i cĂ´ láº­p |
| **LAN** | em1 (LAN) | Internal Network LAN | 192.168.1.0/24 | 192.168.1.1 | VĂ¹ng ngÆ°á» i dĂ¹ng ná»™i bá»™ an toĂ n |
| **DMZ** | em2 (OPT1) | Internal Network DMZ | 192.168.10.0/24 | 192.168.10.1 | VĂ¹ng cĂ´ láº­p chá»©a Web Server Nginx |
| **MGMT** | em3 (OPT2) | Host-Only Adapter | 192.168.56.0/24 | 192.168.56.2 | Quáº£n trá»‹ an toĂ n qua Web GUI tá»« mĂ¡y tháº­t |

---

## 4. ChĂ­nh sĂ¡ch Kiá»ƒm soĂ¡t Truy cáº­p (Access Matrix)

| Luá»“ng truy cáº­p | Nguá»“n | Ä Ă­ch | Dá»‹ch vá»¥ / Cá»•ng | ChĂ­nh sĂ¡ch | Káº¿t quáº£ thá»±c nghiá»‡m |
|:---|:---|:---|:---|:---:|:---:|
| **LAN -> DMZ** | LAN Subnet (192.168.1.0/24) | DMZ Web (192.168.10.10) | TCP / 80 (HTTP) | **PASS** | Nháº­n HTTP 200 (Welcome to nginx!) |
| **DMZ -> LAN** | DMZ Subnet (192.168.10.0/24)| LAN Subnet (192.168.1.0/24) | ToĂ n bá»™ (ICMP, TCP, UDP) | **BLOCK** | Cháº·n 100% (100% packet loss) |
| **MGMT -> pfSense** | Host Windows (192.168.56.1) | pfSense (192.168.56.2) | HTTPS / 443 | **PASS** | Quáº£n trá»‹ WebGUI thĂ nh cĂ´ng |

---

## 5. Cáº¥u trĂºc ThÆ° má»¥c Dá»± Ă¡n

- **docs/**: CĂ¡c tĂ i liá»‡u cÆ¡ sá»Ÿ lĂ½ thuyáº¿t, phĂ¢n tĂ­ch nguy cÆ¡, quy táº¯c an toĂ n vĂ  kiáº¿n trĂºc há»‡ thá»‘ng.
- **LAB/**: CĂ¡c ká»‹ch báº£n kiá»ƒm thá»­ (test cases), sÆ¡ Ä‘á»“, cĂ¡c bĂ i Ä‘Ă¡nh giĂ¡ an ninh tÆ°á» ng lá»­a.
- **SETUP/**: HÆ°á»›ng dáº«n cĂ i Ä‘áº·t vĂ  cáº¥u hĂ¬nh mĂ´i trÆ°á» ng mĂ¡y áº£o, gĂ³i dá»‹ch vá»¥.
- **THESIS/**: BĂ¡o cĂ¡o Word vĂ  Slide thuyáº¿t trĂ¬nh chĂ­nh thá»©c cá»§a chuyĂªn Ä‘á» .
