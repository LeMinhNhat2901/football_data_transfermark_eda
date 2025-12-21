# Football_data_transfermark_eda⚽️

## 1. Project Overview and Team Info 👥

### Overview
Dự án này tập trung vào việc Phân tích khám phá dữ liệu (EDA) và xây dựng mô hình học máy để dự đoán giá trị thị trường của các cầu thủ bóng đá dựa trên hiệu suất của họ ở mùa giải gần nhất. Nhóm đã thực hiện thu thập, tiền xử lý dữ liệu và huấn luyện các mô hình dự đoán để tìm ra ý nghĩa của một số câu hỏi thực tiễn phần dưới.

Đồ án này thuộc khuôn khổ môn học **Lập trình cho Khoa học dữ liệu** tại **Trường Đại học Khoa học Tự nhiên, ĐHQG-HCM (HCMUS)**.

### Team Members
| No. | Student Name | Student ID | Role |
| :-: | :--- | :--- | :--- |
| 1 | **Lê Minh Nhật**  | 23120067 | Project Lead, Modeling |
| 2 | **Huỳnh Đặng Ngọc Hân**| 23120042 | EDA, Preprocessing |
| 3 | **Nguyễn Văn Khoa** | 23122016 | Data Collection, Analysis |

---

## 2. Dataset source and Description 📊
* **Nguồn dữ liệu:** Dữ liệu được thu thập từ https://www.kaggle.com/datasets/davidcariboo/player-scores
* **Các file dữ liệu chính (trong thư mục `data/`):**
    * `players_data.csv`: Dữ liệu thô ban đầu sau khi thu thập.
    * `processed_players_data.csv`: Dữ liệu đã qua bước tiền xử lý.
    * `train_catboost.csv` & `test_catboost.csv`: Tập dữ liệu đã được chia để huấn luyện mô hình CatBoost.
    * `train/test_data_encoded.csv`: Dữ liệu đã được mã hóa (encoding).

---

## 3. Research Questions ❓

Các câu hỏi có ý nghĩa thực tiễn và định hướng phân tích được trình bày chi tiết trong file `notebooks/question.ipynb`, bao gồm:
1. Liệu chiều cao có còn là tiêu chí tiên quyết cho từng vị trí trong bóng đá hiện đại hay không?
2. So sánh hiệu suất thi đấu giữa 'Inverted Wingers' (Cánh nghịch chân) và 'Traditional Wingers' (Cánh thuận chân) - Cái nào đang là xu thế?
3. Thời kì hoàng kim của cầu thủ thường rơi vào độ tuổi nào?
4. Phân tích luồng di cư bóng đá - xu hướng cầu thủ thi đấu cho tuyển quốc gia hay nơi khác?
5. Những câu lạc bộ nào là nơi cung cấp những cầu thủ "hàng rẻ, chất lượng cao"?
6. Có thể dự đoán 'Giá trị cầu thủ' mùa tiếp theo dựa trên dữ liệu và thống kê cơ bản ở mùa gần nhất(Tuổi, Vị trí, Bàn thắng..) hay không?
---

## 4. Key Findings Summary 💡

Dựa trên quá trình Phân tích khám phá dữ liệu (EDA) và thực nghiệm Huấn luyện mô hình trong file `analysis.ipynb`, nhóm đã rút ra những kết luận quan trọng sau:
### 4.1. Hiệu suất mô hình (Model Performance)
* Mô hình **CatBoost** đã cho thấy sự vượt trội so với các mô hình khác (như Random Forest, XGBoost) trong bài toán hồi quy này.
### 4.2. Các yếu tố ảnh hưởng nhất (Feature Importance)
Thông qua việc phân tích mức độ quan trọng của các đặc trưng (Feature Importance plot), các yếu tố sau đóng vai trò quyết định đến giá trị thị trường của cầu thủ:
1.  **`last_season`**: `Mùa giải ghi nhận dữ liệu cầu thủ`
2.  **`current_club_name`**: `Tên câu lạc đang thi đấu`
3.  **`total_minutes_played`**: `Tổng số phút cầu thủ thi đấu`
### 4.3. Nhận định thị trường (Market Insights)
Từ quá trình EDA, nhóm ghi nhận một số xu hướng thú vị của bóng đá hiện đại:
* **Sự chênh lệch theo vị trí:** Các vị trí tấn công (Tiền đạo/Tiền vệ) thường được định giá cao hơn trung bình khoảng **20%** so với các vị trí phòng ngự (Hậu vệ/Thủ môn) ở cùng độ tuổi.
* **Hiệu ứng "Siêu sao":** Phân phối giá trị thị trường bị lệch phải rất nặng, cho thấy thị trường bị chi phối bởi một nhóm nhỏ các siêu sao có giá trị cực khủng (outliers), trong khi phần lớn cầu thủ nằm ở mức giá trị trung bình thấp.
---

## 5. File Structure 📂

Cấu trúc mã nguồn của dự án được tổ chức như sau:
```text
football_data_transfermark_eda/
├── data/                           # Thư mục chứa dữ liệu
│   ├── players_data.csv            # Dữ liệu thô
│   ├── processed_players_data.csv  # Dữ liệu đã xử lý
│   ├── train_catboost.csv          # Tập train cho CatBoost
│   ├── test_catboost.csv           # Tập test cho CatBoost
│   └── ... (các file encoded khác)
│
├── notebooks/                      # Thư mục chứa các notebooks
│   ├── catboost_info/              # Các thông số của Catboost
│   ├── collection.ipynb            # Thu nhập dữ liệu
│   ├── preprocess.ipynb            # Làm sạch và tiền xử lý dữ liệu
│   ├── question.ipynb              # Các câu hỏi nghiên cứu
│   ├── exploration.ipynb           # Phân tích khám phá dữ liệu (EDA)
│   ├── modeling.ipynb              # Huấn luyện và xây dựng mô hình
│   └── analysis.ipynb              # Đánh giá kết quả và phân tích
│
├── README.md                       # Thông tin dự án
└── requirement.txt                 # Danh sách thư viện cần thiết
└── project_summary.pdf             # Tổng kết dự án


```
## 6. How to run the project 🚀

### 6.1. Environment Setup
Trước tiên, cài đặt các thư viện cần thiết bằng lệnh:
```bash
pip install -r requirement.txt
```
### 6.2. Project Workflow

Quy trình thực hiện dự án được triển khai theo thứ tự các notebook sau:

1. **collection.ipynb**  
   - Thu thập dữ liệu cầu thủ 
   - Tổng hợp thông tin cơ bản: tên cầu thủ, tuổi, vị trí, quốc tịch, CLB, giải đấu  
   - Lưu dữ liệu thô vào thư mục `data/players_data.csv`

2. **preprocess.ipynb**  
   - Làm sạch và tiền xử lý dữ liệu
   - Chuẩn hóa và biến đổi các đặc trưng cần thiết  
   - Xuất dữ liệu đã xử lý: `data/processed_players_data.csv`

3. **exploration.ipynb**  
   - Phân tích khám phá dữ liệu (EDA)  
   - Trực quan hóa phân bố giá trị cầu thủ
   - Phân tích mối quan hệ giữa giá trị cầu thủ và:
     - Tuổi
     - Vị trí thi đấu
     - Giải đấu
     - Quốc tịch

4. **question.ipynb**  
   - Lý do, động lực và ý nghĩa thực tiễn của các câu hỏi
   
5. **modeling.ipynb**
   - Tối ưu các siêu tham số của mô hình
   - Huấn luyện và đánh giá các mô hình
   - Chọn ra mô hình tốt nhất
   - Phân tích độ quan trọng của các đặc trưng 
  

7. **analysis.ipynb**
   - Phân tích và trả lời các câu hỏi nghiên cứu
   - Rút ra nhận xét và kết luận


