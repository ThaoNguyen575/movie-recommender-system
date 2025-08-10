# Movie Recommender System

## Giới thiệu

Dự án này là một hệ thống gợi ý phim sử dụng Python, Streamlit và mô hình similarity dựa trên dữ liệu phim. Người dùng có thể nhập tên phim và nhận được danh sách các phim tương tự kèm ảnh bìa.
Model sử dụng **Cosine Similarity** để tính độ tương đồng giữa các phim dựa trên vector đặc trưng của chúng.
Hệ thống gợi ý phim này sử dụng phương pháp **Content-Based Filtering**, dựa trên similarity giữa các đặc điểm của phim để đưa ra các gợi ý phim tương tự.
---

## Cài đặt
```bash
python -m venv venv
# Linux/macOS
source venv/bin/activate   
# Windows
venv\Scripts\activate      

pip install -r requirements.txt
```
---
## Hướng phát triển
Áp dụng Hybrid Filtering kết hợp giữa Content-Based Filtering và Collaborative Filtering để nâng cao chất lượng gợi ý.

Xây dựng website thực tế thu thập dữ liệu hành vi người dùng (ví dụ: lượt xem, đánh giá, lịch sử tìm kiếm) để cải thiện mô hình gợi ý.

Triển khai mô hình Collaborative Filtering dựa trên dữ liệu người dùng.

Ứng dụng Neural Collaborative Filtering (NCF) — một phương pháp học sâu kết hợp các kỹ thuật embedding và mạng neural để khai thác mối quan hệ phức tạp giữa người dùng và sản phẩm, giúp cải thiện độ chính xác của hệ thống gợi ý.

