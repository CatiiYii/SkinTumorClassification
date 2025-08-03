PHÁT TRIỂN KỸ THUẬT PHÂN LOẠI KHỐI U TRÊN DA DỰA TRÊN HỌC SÂU

Dự án này tập trung phát triển và thử nghiệm các kỹ thuật phân loại khối u trên da từ ảnh y khoa, sử dụng các mô hình học sâu với nhiều cấu hình tiền xử lý và hậu xử lý khác nhau. Hai tập dữ liệu chính được sử dụng trong nghiên cứu gồm: Dataset 907 và Dataset 2750 — đều được tái cấu trúc từ tập dữ liệu ISIC 2017.

== CẤU TRÚC THƯ MỤC DỰ ÁN ==

🔹 Dataset_907/
Chứa các mô hình, mã nguồn huấn luyện, kết quả đánh giá được thực hiện trên tập dữ liệu 907.

🔹 Dataset_2750/
Chứa các mô hình, mã nguồn huấn luyện, kết quả đánh giá tương ứng trên tập dữ liệu gồm 2750.

== MÔ TẢ CÁC THỬ NGHIỆM ==

Mỗi thư mục con thể hiện một thử nghiệm độc lập, bao gồm một cấu hình cụ thể về:
- Phương pháp tiền xử lý ảnh
- Kiến trúc mô hình phân loại
- Phương pháp hậu xử lý đầu ra

Thư mục        | Tiền xử lý     | Mô hình sử dụng   | Hậu xử lý             | Tập dữ liệu
---------------|----------------|-------------------|------------------------|------------
bayer_907/     | Bayer Filter   | Mô hình đề xuất   | Morphology Operations | 907 ảnh
bayer_2750/    | Bayer Filter   | Mô hình đề xuất   | Morphology Operations | 2750 ảnh
gau_907/       | Gaussian Blur  | Mô hình đề xuất   | Morphology Operations | 907 ảnh
gau_2750/      | Gaussian Blur  | Mô hình đề xuất   | Morphology Operations | 2750 ảnh
begin_907/     | CLAHE          | SegUNet (gốc)     | Morphology Operations | 907 ảnh
begin_2750/    | CLAHE          | SegUNet (gốc)     | Morphology Operations | 2750 ảnh
resunet_907/   | CLAHE          | ResUNet           | Morphology Operations | 907 ảnh
resunet_2750/  | CLAHE          | ResUNet           | Morphology Operations | 2750 ảnh
gray_907/      | CLAHE          | Mô hình đề xuất   | Morphology + CRF      | 907 ảnh
gray_2750/     | CLAHE          | Mô hình đề xuất   | Morphology + CRF      | 2750 ảnh

== TÁI CẤU TRÚC TẬP DỮ LIỆU ISIC 2017 ==
Tập dữ liệu ISIC 2017 được tái cấu trúc thành hai phiên bản: Dataset 907 và Dataset 2750, thông qua hai file mã nguồn kltn-dataset-raw-907.py và kltn-dataset-raw-2750.py.

Quá trình chuyển tập dữ liệu ISIC 2017 thành tập 907 và 2750 là như nhau. Chỉ khác nhau tại phần sau khi đọc file csv (GroundTruth_part3) thì tập 907 tiến hành loại bỏ các dòng có giá trị trên cả 2 cột melanoma và seborrheic_keratosis là 0, còn 2750 thì không thực hiện bước này. Sau đó, tiến hành cắt bỏ cột seborrheic_keratosis, chỉ giữ lại cột image-id và cột melanoma.
---

## 🎯 Mục tiêu

So sánh hiệu quả giữa các mô hình phân lớp trên tập dữ liệu ảnh y khoa khác nhau.

