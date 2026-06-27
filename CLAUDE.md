# Chỉ dẫn vận hành cho Claude Cowork — Dự án "Web Tin Tức"

## Bối cảnh
Đây là hệ thống tổng hợp tin tức tự động theo mô hình "Tĩnh nhưng chạy động",
host trên GitHub Pages. Vận hành bởi **Phuc Hung Agent**.

## NGUYÊN TẮC BẤT BIẾN (không được vi phạm)
- ❌ **KHÔNG** chỉnh sửa `index.html` trong quy trình chạy hằng ngày. File này là cố định.
- ❌ **KHÔNG** xóa các file cũ trong thư mục `archive/`.
- ✅ Mỗi ngày chỉ: (1) thêm 1 file archive mới, (2) cập nhật `database.json`, (3) push.

## Cấu trúc file dữ liệu
- `database.json` → khóa `news_list` là mảng các ngày `"YYYY-MM-DD"`, **sắp xếp mới → cũ**.
  Ngày mới nhất luôn nằm ở **đầu mảng** (index 0).
- `archive/YYYY-MM-DD.html` → fragment HTML thô (chỉ `<article>`, `<h2>`, `<p>`, `<table>`...),
  KHÔNG chứa thẻ `<html>`, `<head>`, `<body>`.

## Khung mẫu mỗi bài trong file archive
```html
<article class="news-item">
  <h2>Tiêu đề bài báo</h2>
  <div class="news-meta">
    <span class="news-tag">Phân loại</span>
    <span class="news-time">⏱ Cào lúc: HH:MM — DD/MM/YYYY</span>
  </div>
  <p>Nội dung tóm tắt, chia đoạn rõ ràng...</p>
</article>
```

## Quy trình hằng ngày
Xem chi tiết trong "Prompt Vận Hành" được cấu hình ở Scheduled Task.
Tóm tắt: Cào tin → Tạo `archive/<hôm-nay>.html` → `unshift` ngày vào `news_list` → Git push.
