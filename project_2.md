# Thiết bị
-	Access Point: Totolink N302R Plus
-	Operation System: Kali Linux 2020.2
-	CPU core: i5
-	CPU Speed: 250 GHz
-	RAM: 16GB
-	Wireless Card: Intel(R) Dual Band Wireless-AC 8265

# Cracking WEP
## Lỗ hổng của WEP
- WEP sử dụng RC4 (stream cipher). Nên để đảm bảo hai plaintext giống nhau sẽ luôn cho ra hai ciphertext khác nhau trong những lần encrypt khác nhau, một IV dài 24 bits được tạo ra, cộng thêm với key để encrypt plaintext. Sau đó IV dưới dạng plaintext sẽ được gửi kèm với ciphertext cho người nhận.
-	Với độ dài 24 bit, số IV có thể được tạo ra dao động trong khoảng 16.777.216 trường hợp. Từ việc bắt được 1 số lượng IVs đủ lớn, cũng như lợi dụng lỗ hổng từ RC4, hacker có thể tiến hành phân tích IVs, dò ra được đoạn ciphertext, từ đó bẻ khóa được password WEP.

## Cracking WEP (Kismet, Aireplay-ng, Airodump-ng, Aircarck-ng)
### *Step 1: Đặt vào chế độ Monitor:*
-	Kiểm tra Kali Linux nhận wireless card bằng câu lệnh iwconfig, tại đây ta thấy wlan0 sẽ là interface của wireless adapter.
-	Chạy lệnh airmon-ng start wlan0 để bật chế độ monitor cho wlan0.
-	Chạy lệnh ifconfig wlan0mon ta sẽ thấy một interface mới, wlan0mon là in-terface dùng để sniff các packet wireless, lúc này card mạng sẽ thu nhận tất cả các packets được gửi đi từ các card wireless khác trong phạm vi bắt sóng.
![text](Image1.png)
