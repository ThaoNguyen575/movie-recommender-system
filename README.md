# Movie Recommender System

## 1. Giới thiệu
Hệ thống đề xuất phim (Movie Recommender System) nhằm cung cấp các gợi ý phim phù hợp với sở thích của người dùng dựa trên nội dung của các bộ phim đã có. Mục đích là tăng trải nghiệm người dùng bằng cách giúp họ khám phá phim mới tương tự phim họ đã yêu thích

---

## 2. Mô hình
Hệ thống gợi ý phim này sử dụng phương pháp **Content-Based Filtering**, dựa trên similarity giữa các đặc điểm của phim để đưa ra các gợi ý phim tương tự.

### Các bước xử lý chính

#### a. Tiền xử lý dữ liệu (Data Preprocessing)
- Đọc dữ liệu phim (movies.csv) và thông tin liên quan như diễn viên, đạo diễn (credits.csv).
- Xử lý dữ liệu thiếu và trùng lặp (nếu có).
- Chuyển các trường JSON chứa thông tin như genres, keywords, cast, crew thành dạng danh sách các từ khóa (list of strings).
- Lấy thông tin đạo diễn từ trường crew.
- Xử lý văn bản: loại bỏ khoảng trắng thừa trong tên thể loại, diễn viên, từ khóa; tách mô tả phim (overview) thành các từ riêng biệt.

#### b. Tạo đặc trưng chung (Feature Engineering)
- Kết hợp các trường overview, genres, keywords, cast, crew thành một trường duy nhất gọi là tags.
- Chuyển tags thành chuỗi chữ thường, chuẩn hóa (stem) các từ để giảm dạng từ về gốc.

#### c. Vector hóa dữ liệu (Vectorization)
- Sử dụng CountVectorizer để chuyển đổi các chuỗi tags thành các vector đặc trưng số học.
- Giới hạn số đặc trưng tối đa (ví dụ: 5000 từ phổ biến nhất).
- Kết quả là ma trận đặc trưng mỗi phim sẽ được biểu diễn bằng một vector số.

#### d. Tính toán độ tương đồng (Similarity Calculation)
- Sử dụng Cosine Similarity để đo mức độ tương đồng giữa các vector đặc trưng phim.
- Cosine similarity đo góc giữa hai vector, giá trị nằm trong [0,1], càng gần 1 càng giống nhau.

#### e. Thuật toán đề xuất (Recommendation Algorithm)
- Khi người dùng nhập một tên phim, hệ thống:
  - Tìm vị trí của phim đó trong ma trận dữ liệu.
  - Lấy vector đặc trưng của phim đó.
  - Tính cosine similarity với tất cả các phim khác.
  - Sắp xếp các phim theo độ tương đồng giảm dần.
  - Trả về danh sách N phim có điểm tương đồng cao nhất (ngoại trừ phim đã chọn).

---

## 3. Cài đặt
```bash
python -m venv venv
# Linux/macOS
source venv/bin/activate   
# Windows
venv\Scripts\activate      

pip install -r requirements.txt
```
---
## 4. Hướng phát triển
Áp dụng Hybrid Filtering kết hợp giữa Content-Based Filtering và Collaborative Filtering để nâng cao chất lượng gợi ý.

Xây dựng website thực tế thu thập dữ liệu hành vi người dùng (ví dụ: lượt xem, đánh giá, lịch sử tìm kiếm) để cải thiện mô hình gợi ý.

Triển khai mô hình Collaborative Filtering dựa trên dữ liệu người dùng.

Ứng dụng Neural Collaborative Filtering (NCF) — một phương pháp học sâu kết hợp các kỹ thuật embedding và mạng neural để khai thác mối quan hệ phức tạp giữa người dùng và sản phẩm, giúp cải thiện độ chính xác của hệ thống gợi ý.

