<h1 align="center">NHẬN DẠNG HÀNH VI SINH VIÊN TRONG LỚP HỌC SỬ DỤNG CAMERA THÔNG MINH</h1>

<p align="center">
  <img src="https://github.com/user-attachments/assets/e5a919d1-d081-4d12-819e-5fb18ce91a68" width="200"/>
  <img src="https://github.com/user-attachments/assets/59dec55d-7825-422f-b80c-ac6915e3775a" width="170"/>
</p>
<p align="center">
  <a href="https://www.facebook.com/DNUAIoTLab">
    <img src="https://img.shields.io/badge/Made%20by%20AIoTLab-blue?style=for-the-badge" alt="Made by AIoTLab"/>
  </a>
  <a href="https://fitdnu.net/">
    <img src="https://img.shields.io/badge/Fit%20DNU-green?style=for-the-badge" alt="Fit DNU"/>
  </a>
  <a href="https://dainam.edu.vn">
    <img src="https://img.shields.io/badge/DaiNam%20University-red?style=for-the-badge" alt="DaiNam University"/>
  </a>
</p>

## **Giới thiệu**  
Hệ thống Nhận dạng Hành vi Sinh viên trong Lớp học sử dụng Camera và trí tuệ nhân tạo (AI) để phát hiện và nhận diện hành vi của sinh viên trong lớp học thông qua luồng video trực tiếp. Hệ thống phù hợp cho các ứng dụng giám sát hành vi học tập, giúp theo dõi và đánh giá hành vi sinh viên trong môi trường học đường.

Hệ thống hoạt động theo cơ chế:

Nhận diện hành vi của sinh viên trong video bằng mô hình YOLOv7.

Theo dõi và phân tích hành vi của từng sinh viên trong lớp học.

Cung cấp thông tin hành vi và thống kê các hoạt động của sinh viên trong lớp học theo thời gian thực.

**Công nghệ sử dụng:**
- **YOLOv7**: Nhận diện hành vi sinh viên từ video trực tiếp và sử dụng PyTorch..
- **OpenCV**: Xử lý hình ảnh và video để phát hiện và phân tích hành vi. 
- **PyTorch Framework**: train dữ liệu 
---

## **Thiết bị sử dụng trong bài**
**Phần cứng**
- Camera Fnkvison. 
- Laptop để dữ liệu từ camera

**Phần mềm**
- Hệ điều hành: Windows.
- Môi trường Python: Python hoặc anaconda).

---
## **Yêu cầu hệ thống**  
- **Python** 3.10 trở lên   
- Bạn cần pip install requirements.txt trong file để khởi tạo


## **Hướng dẫn cài đặt**  

### **1. Cài đặt các thư viện cần thiết**  
Chạy lệnh sau để cài đặt các thư viện Python yêu cầu:  
```
pip install -r requirements.txt
```

### **2. Hướng dẫn thực hiện**  
Sơ đồ cấu trúc:
![image](https://github.com/user-attachments/assets/1b2eb0de-d875-4dc7-a989-ad5daee27662)

#### **2.1. Sử dụng phần mềm ODM để lấy địa chỉ và port/onvif1**  
Định dạng nguồn: 
```
rtsp://[username]:[password]@[Địa-chỉ-IP]:554/onvif
```
Ví dụ: Tên username bắt buộc phải là admin
```
rtsp://admin:danhphong2004@192.168.0.53:554/onvif1
```
#### **2.6. Tiến hành train mô hình** 
**Bước 1: Chuyền dataset đã thu thập được vào Folder (images)**

![image](https://github.com/user-attachments/assets/3b2c0942-6012-479d-be58-23cf56b69820)

Các link dataset:
- [CrowdHuman Crowd Detection CSV Labels](https://www.kaggle.com/datasets/permanalwep/crowd-human-csv-labels)
- [CrowdHuman Crowd Detection](https://www.kaggle.com/datasets/permanalwep/crowdhuman-crowd-detection)
- [CrowdHuman Face](https://www.kaggle.com/datasets/permanalwep/crowdhuman-face)

**Bước 2: Tiến hành tự động gán nhãn bằng mô hình yolov8 (auto_labeling.py)**

![image](https://github.com/user-attachments/assets/1f31a6d2-e086-43c7-aec7-f424de74a345)

```
python auto_labeling.py
```
**Bước 3: Kiểm tra sau khi tự động gán nhãn (labels/)**

![image](https://github.com/user-attachments/assets/22653595-baa2-4564-98da-f4c9cefdcd7b)

Có file .txt là đúng

**Bước 4: Bắt đầu train (models/train_lstm.py)**
```
python train_lstm.py
```
Kết quả sau khi train tốt nhất sẽ được lưu vào file **`trained_model.h5`**
![image](https://github.com/user-attachments/assets/c604b999-7b20-478b-907c-a9f710aa6b08)

#### **2.7. Chạy toàn bộ mô hình sau khi train xong (app.py)** 
```
python app.py
```
## **Các API Endpoint**  
| Endpoint                 | Phương thức | Mô tả |
|--------------------------|------------|-------|
| `/`                      | GET        | Trả về trang giao diện chính của ứng dụng (index.html), hiển thị giao diện web cho người dùng. |
| `/video_feed`            | GET        | Cung cấp stream video real-time dưới dạng JPEG từ hàm **`generate_frames()`**, cho phép hiển thị video trực tuyến trong trình duyệt. |
| `/start`               | POST       | Khởi động kết nối camera với RTSP URL được truyền qua request (tham số **`rtsp_url`**).|
| `/stop`        | POST       | Dừng kết nối camera và giải phóng các tài nguyên liên quan. |
| `/announce`          | POST       | Kích hoạt thông báo giọng nói (voice notification) để công bố số lượng người hiện tại. |
---

## **Ghi chú:**  
✅ Hãy kết hợp cả CPU+GPU để camera hoạt động tốt hơn. 

---
**Poster**

![Poster_Nhom9_CNTT_1601 -_1_](https://github.com/user-attachments/assets/41c750e6-52ae-4d4c-b525-262805ef826d)
