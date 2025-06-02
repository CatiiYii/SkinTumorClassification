PHÁT TRIỂN KỸ THUẬT PHÂN LOẠI KHỐI U TRÊN DA DỰA TRÊN HỌC SÂU

Dự án này thực hiện các thử nghiệm với nhiều quy trình tiền xử lý và hậu xử lý khác nhau cho bài toán phân loại ảnh y khoa, sử dụng hai tập dữ liệu chính: **Dataset 907** và **Dataset 2750**.

---

## 📁 Cấu trúc Thư mục

### 🔹 Dataset_907/
Chứa các mô hình và kết quả huấn luyện, đánh giá trên tập dữ liệu gồm **907 ảnh**.

### 🔹 Dataset_2750/
Chứa các mô hình và kết quả huấn luyện, đánh giá trên tập dữ liệu gồm **2750 ảnh**.

### 🔹 load_weights_gray_2750/
Tải lại trọng số của mô hình đề xuất để thử nghiệm trên 4 ảnh từ tập dữ liệu 2750.

---

## 📂 Mô tả Các Thử Nghiệm

Mỗi thư mục tương ứng với một cấu hình thử nghiệm gồm tiền xử lý, mô hình phân lớp, và hậu xử lý cụ thể trên một tập dữ liệu nhất định:

| Thư mục           | Tiền xử lý     | Mô hình                | Hậu xử lý                 | Tập dữ liệu |
|-------------------|----------------|------------------------|---------------------------|-------------|
| `bayer_907/`      | Bayer          | Mô hình đề xuất        | Morphology Operations     | 907         |
| `bayer_2750/`     | Bayer          | Mô hình đề xuất        | Morphology Operations     | 2750        |
| `gau_907/`        | Gaussian       | Mô hình đề xuất        | Morphology Operations     | 907         |
| `gau_2750/`       | Gaussian       | Mô hình đề xuất        | Morphology Operations     | 2750        |
| `begin_907/`      | CLAHE          | SegUNet (gốc)          | Morphology Operations     | 907         |
| `begin_2750/`     | CLAHE          | SegUNet (gốc)          | Morphology Operations     | 2750        |
| `resunet_907/`    | CLAHE          | ResUNet                | Morphology Operations     | 907         |
| `resunet_2750/`   | CLAHE          | ResUNet                | Morphology Operations     | 2750        |
| `gray_907/`       | CLAHE          | Mô hình đề xuất        | Morphology + CRF          | 907         |
| `gray_2750/`      | CLAHE          | Mô hình đề xuất        | Morphology + CRF          | 2750        |

---

## 🎯 Mục tiêu

So sánh hiệu quả giữa các mô hình phân lớp trên tập dữ liệu ảnh y khoa khác nhau.

