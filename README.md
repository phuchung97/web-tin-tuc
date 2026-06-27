# 📰 Trang Cập Nhật Tin Tức Mỗi Ngày

Hệ thống tự động tổng hợp tin tức hằng ngày, vận hành bởi **Phuc Hung Agent**.
Thiết kế theo mô hình **"Tĩnh nhưng chạy động"**: giao diện cố định, nội dung nạp động qua JavaScript — host miễn phí trên **GitHub Pages**.

## 🏗️ Cấu trúc dự án

```
web-tin-tuc/
├── index.html          # Trang chủ cố định (TẠO 1 LẦN) — "bộ máy" render
├── database.json       # Mục lục các ngày có bài (CẬP NHẬT MỖI NGÀY)
├── archive/            # Kho tin thô theo ngày (THÊM FILE MỚI MỖI NGÀY)
│   └── YYYY-MM-DD.html
├── .nojekyll           # Tắt Jekyll của GitHub Pages
├── CLAUDE.md           # Chỉ dẫn cho Claude Cowork khi chạy tự động
└── README.md
```

## ⚙️ Cách hoạt động

1. Người dùng mở `index.html`.
2. JS đọc `database.json` → lấy ngày mới nhất (`news_list[0]`).
3. Nạp ngầm `archive/<ngày-mới-nhất>.html` vào vùng **Tin Hôm Nay**.
4. Các ngày còn lại được render thành danh sách **Bản Tin Các Ngày Trước**.

## 🚀 Triển khai GitHub Pages

1. Push toàn bộ thư mục lên repository GitHub.
2. Vào **Settings → Pages** → chọn nhánh `main`, thư mục `/ (root)`.
3. Truy cập: `https://<username>.github.io/<repo>/`.

## 🤖 Tự động hóa

Quy trình hằng ngày (cào tin → tạo file archive → cập nhật `database.json` → push) được
mô tả trong **Prompt Vận Hành**, dán vào Scheduled Task của Claude Cowork. Xem `CLAUDE.md`.

---
© Phuc Hung Agent
