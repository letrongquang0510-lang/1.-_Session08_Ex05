 

# **Yêu cầu đầu ra**
## **Phần 1. Phân tích:** Xác định Input/Output và sơ đồ phối hợp phần cứng của hệ thống trang trại.
   -   **Input :**  
     Cảm biến độ ẩm đất .
     Cảm biến nhiệt độ và độ ẩm không khí.
     Lệnh thủ công từ người nông dân thông qua ứng dụng di động hoặc giao diện Web.
-   **Process :**
    -   Vi điều khiển (SoC) đọc giá trị từ các cảm biến. 
    -   So sánh dữ liệu thời gian thực với ngưỡng thiết lập theo mô hình DIKW (Data $\rightarrow$ Information $\rightarrow$ Knowledge $\rightarrow$ Wisdom)   
    -   Quyết định thời điểm và lưu lượng nước cần tưới.
-   **Output (Đầu ra):**
    -   Trạng thái bật/tắt van điện từ và máy bơm nước.
    -   Cảnh báo trực quan qua đèn LED và hiển thị thông số lên Dashboard.
## **Phần 2. Triển khai:** File [README.md](http://readme.md/) hoàn chỉnh theo chuẩn kỹ sư phần mềm chuyên nghiệp.
I sẽ tạo cho bạn file `README.md` được tóm gọn, tối ưu chuẩn kỹ sư phần mềm, dùng văn phong kỹ thuật tự nhiên và đáp ứng đầy đủ 5 yêu cầu đề bài.

  

README.md

Xuất

## 🚀 Smart-Farm: Hệ Thống Tự Động Hóa Trang Trại Lan

> Hệ thống IoT tự động giám sát môi trường và điều khiển tưới tiêu cho trang trại hoa Lan.

## 📖 Mô tả

Smart-Farm giúp người nông dân tự động hóa quy trình tưới nước dựa trên dữ liệu cảm biến thời gian thực, đảm bảo độ ẩm và nhiệt độ tối ưu cho hoa lan.
## ⚙️ Cài đặt
```
git clone https://github.com/smart-farm/lan-iot-system.git
cd lan-iot-system
pio run --target upload

```

## ✨ Tính năng
-   [x] Giám sát nhiệt độ, độ ẩm không khí (DHT22)
-   [x] Đo độ ẩm đất tự động
-   [x] Điều khiển tưới qua Web Dashboard
-   [ ] Cảnh báo qua SMS khi nhiệt độ cao

## 📊 Bảng thông số phần cứng
 | Linh kiện | Model | Thông số | Chức năng |
| :--- | :--- | :--- | :--- |
| SoC | ESP32 | 240MHz, Wi-Fi/BLE | Xử lý trung tâm & kết nối |
| Cảm biến | DHT22 | $\pm 0.5^\circ C$, $\pm 2\% RH$ | Đo nhiệt độ/độ ẩm |
| Cảm biến đất | Capacitive Soil | $3.3V - 5V$ | Đo độ ẩm giá thể |
| Van tưới | Solenoid 12V | $0 - 0.8 MPa$ | Đóng/mở nước tự động |

## 🔄 Chu kỳ Fetch–Decode–Execute (Lệnh tưới)
> Khi vi điều khiển thực thi lệnh tưới nước:
> 1.  **Fetch:** CPU nạp chỉ thị bật rơ-le từ bộ nhớ Flash vào thanh ghi.  
> 2.  **Decode:** Control Unit giải mã lệnh điều khiển chân GPIO tương ứng.     
> 3.  **Execute:** Mạch cấp điện áp ra chân GPIO để kích hoạt rơ-le mở van nước.

##  Mô hình DIKW
Wisdom: Tối ưu lịch tưới tiết kiệm nước.
Knowledge: Lan cần độ ẩm đất > 70%, nhiệt độ < 32°C. Information: Nhiệt độ 33°C, Độ ẩm 60% -> Cần tưới.
Data: Raw values Temp: 33.5°C, Moisture: 60%)
## 🖼️ Sơ đồ hệ thống
Chỉnh sửa trực tiếp hoặc bằng Gemini
Nhấp vào vị trí bất kỳ để nhập và chỉnh sửa trực tiếp, hoặc chọn văn bản để yêu cầu Gemini chỉnh sửa.
File  README.md đã được tối giản súc tích, lược bỏ các câu từ mang tính khuôn mẫu để đảm bảo tự nhiên nhất. 
## **Phần 3. Kiểm thử:** Giả định RAM bị đầy dữ liệu nhật ký, hãy cập nhật mục "Lưu ý" trong README cách xử lý an toàn.
### ⚠️ Lưu ý: Xử lý tràn RAM do Log hệ thống
Khi RAM đầy do log nhật ký hoạt động liên tục, cần thực hiện:
> 1. **Giới hạn bộ nhớ đệm:** Chuyển sang cơ chế Circular Buffer (ghi đè vòng tròn) để cố định dung lượng RAM cấp cho log.
> 2. **Xả dữ liệu định kỳ:** Đẩy log xuống Flash/Server rồi giải phóng vùng đệm RAM.
> 3. **Khởi động lại (Soft Reset):** Reboot vi điều khiển vào khung giờ ít tải để làm sạch phân vùng RAM.

