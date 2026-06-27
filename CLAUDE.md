# Hướng dẫn vận hành nội dung — Phúc Hưng

## Bối cảnh
Chuyên trang thông tin và dữ liệu thị trường bất động sản, kinh tế Nhật Bản,
xây dựng theo mô hình "tĩnh nhưng nạp động", host trên GitHub Pages.
Nội dung được cập nhật mỗi ngày.

## NGUYÊN TẮC BẤT BIẾN (không được vi phạm)
- ❌ **KHÔNG** chỉnh sửa `index.html` và `article.html` trong quy trình cập nhật hằng ngày. Đây là các file giao diện cố định.
- ❌ **KHÔNG** xóa hay sửa các file cũ trong thư mục `archive/`.
- ✅ Mỗi ngày chỉ: (1) thêm 1 file archive mới, (2) cập nhật `database.json`, (3) push.

## Cấu trúc file dữ liệu
- `database.json` → khóa `news_list` là mảng, **sắp xếp mới → cũ**. Mỗi phần tử là một object:
  `{ "date": "YYYY-MM-DD", "title": "tiêu đề bài viết" }`. Bài mới nhất luôn ở **đầu mảng** (index 0).
- `archive/YYYY-MM-DD.html` → fragment HTML thô (chỉ `<article>`, `<h2>`, `<p>`, `<table>`, `<svg>`...),
  KHÔNG chứa thẻ `<html>`, `<head>`, `<body>`, `<style>`, `<script>`.

## Khung mẫu mỗi bài trong file archive
```html
<article class="news-item">
  <h2>Tiêu đề bài viết</h2>
  <div class="news-meta">
    <span class="news-tag">Phân loại</span>
    <span class="news-time">⏱ Đăng lúc: HH:MM (JST) — DD/MM/YYYY</span>
  </div>
  <p>Nội dung, chia đoạn rõ ràng...</p>
</article>
```

## Quy trình cập nhật hằng ngày
Chi tiết được cấu hình trong tác vụ định kỳ (Scheduled Task).
Tóm tắt: Soạn nội dung → tạo `archive/<hôm-nay>.html` → thêm `{date, title}` vào đầu `news_list`
→ cập nhật `database.json` → git push.
