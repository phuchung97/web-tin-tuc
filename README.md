# 📊 Phúc Hưng — Thông tin thị trường bất động sản & kinh tế Nhật Bản

Chuyên trang tổng hợp thông tin và dữ liệu thị trường bất động sản, kinh tế Nhật Bản, **cập nhật mỗi ngày**.
Xây dựng theo mô hình **"tĩnh nhưng nạp động"**: giao diện cố định, nội dung nạp động qua JavaScript — host trên **GitHub Pages**.

## 🏗️ Cấu trúc dự án

```
web-tin-tuc/
├── index.html          # Trang chủ — đọc database.json & render nội dung
├── article.html        # Trang xem chi tiết một bản tin (theo ?date=YYYY-MM-DD)
├── database.json       # Mục lục các bản tin: [{ date, title }, ...]
├── archive/            # Nội dung từng ngày (fragment HTML)
│   └── YYYY-MM-DD.html
├── .nojekyll           # Tắt Jekyll của GitHub Pages
├── CLAUDE.md           # Hướng dẫn vận hành nội dung
└── README.md
```

## ⚙️ Cách hoạt động

1. Người dùng mở `index.html`.
2. JS đọc `database.json` → lấy bài mới nhất (`news_list[0]`).
3. Nạp `archive/<ngày-mới-nhất>.html` vào vùng **Tin Hôm Nay**.
4. Các bài còn lại được render thành danh sách **Bản Tin Các Ngày Trước** (kèm tiêu đề).
5. Bấm một bài cũ → mở `article.html?date=...` hiển thị nội dung trong khung có định dạng.

## 🚀 Triển khai GitHub Pages

1. Push toàn bộ thư mục lên repository GitHub.
2. Vào **Settings → Pages** → chọn nhánh `main`, thư mục `/ (root)`.
3. Truy cập: `https://<username>.github.io/<repo>/`.

## 🗂️ Cập nhật nội dung

Quy trình cập nhật hằng ngày (soạn bài → tạo file trong `archive/` → cập nhật `database.json` → push)
được mô tả trong `CLAUDE.md`.

---
© Phúc Hưng
