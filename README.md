
Nhận dạng hành vi sinh viên trong lớp học sử dụng camera thông minh và YOLOv7
Dự án này sử dụng YOLOv7 để nhận dạng hành vi của sinh viên trong lớp học, thông qua video trực tiếp từ camera thông minh RTSP

Các tính năng chính:
Nhận dạng hành vi sinh viên: Sử dụng mô hình YOLOv7 đã được huấn luyện để nhận dạng các hành vi của sinh viên trong lớp học.
Camera thông minh RTSP: Camera RTSP được sử dụng để truyền tải video trực tiếp đến hệ thống để xử lý và nhận diện hành vi.
Dữ liệu trực tiếp: Kết quả nhận dạng hành vi được cập nhật và hiển thị theo thời gian thực, cho phép giảng viên hoặc quản lý lớp học theo dõi hành vi của sinh viên.
Cấu trúc thư mục:
├── app/
│   ├── static/
│   │   ├── images/               # Lưu trữ ảnh hoặc video nhận dạng
│   ├── yolov7                     # Thư mục chứa mã nguồn YOLOv7
│   ├── camera.py                  # Xử lý kết nối với camera RTSP
|    ├── Detect.py   
├── models/                        # Mô hình YOLOv7 đã huấn luyện
│   ├── best.pt                    # Mô hình YOLOv7 đã huấn luyện (tốt nhất)
│   ├── last.pt                    # Mô hình YOLOv7 (mới nhất)
├── requirements.txt               # Các thư viện cần thiết
└── README.md                      # Tài liệu hướng dẫn sử dụng

1. Cài đặt các thư viện yêu cầu:
pip install -r requirements.txt
Cài đặt mô hình YOLOv7:

2.Tải mô hình đã huấn luyện của bạn vào thư mục models/.
Đảm bảo rằng bạn đã có best.pt hoặc last.pt trong thư mục models/.
3.Cấu hình kết nối camera RTSP:
Mở tệp camera.py và nhập URL RTSP của camera thông minh của bạn.
