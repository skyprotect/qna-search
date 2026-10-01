# Tra Cứu Câu Hỏi & Đáp Án Trắc Nghiệm

Trang web tra cứu câu hỏi và đáp án trắc nghiệm nhanh chóng, hiện đại, tương tự giao diện tra cứu tại [skyprotect.github.io/qna-search](https://skyprotect.github.io/qna-search/).

Dữ liệu được trích xuất tự động từ file `cauhoi.xlsx` (180 câu hỏi trắc nghiệm kèm đáp án chính xác).

---

## 🚀 Tính năng nổi bật

1. **Tìm kiếm siêu tốc & thông minh**:
   - Tìm theo từ khóa **có dấu hoặc không dấu** (ví dụ: `dai hoi 14`, `nghi quyet 27`, `quy dinh 144`).
   - Tự động nhận diện chữ số La Mã thông dụng: gõ `dai hoi 14` vẫn tìm thấy `Đại hội XIV`.
   - Tìm trực tiếp theo số thứ tự câu hỏi: gõ `15`, `câu 180` hoặc `c50` sẽ hiện ngay câu tương ứng.
   - Thuật toán kết hợp: Khớp chính xác + Khớp cụm từ + Khớp từng từ + Fuse.js fuzzy search khi có lỗi chính tả.
   - Bôi vàng (highlight) từ khóa trùng khớp trong cả câu hỏi và đáp án.

2. **Giao diện hiện đại & tiện ích**:
   - Thẻ câu hỏi rõ ràng, đáp án đúng được làm nổi bật với màu xanh lá và icon trực quan.
   - Nút **Sao chép đáp án** và nút **📋 Sao chép Q&A** tiện lợi với thông báo toast.
   - Tùy chọn **Xem tất cả các đáp án (A, B, C, D)** cho từng câu hoặc bật đồng loạt toàn bộ trang.
   - Thanh bộ lọc nhanh: `Tất cả (180)`, `Top 10`, `Câu 1-50`, `Câu 51-100`, `Câu 101-150`, `Câu 151-180`.
   - Chế độ Giao diện **Sáng / Tối (Light / Dark mode)** lưu cấu hình theo người dùng.
   - Phím tắt tiện lợi: Nhấn phím `/` hoặc `Ctrl+K` để nhảy vào ô tìm kiếm, phím `Esc` để xóa trắng tìm kiếm.
   - Nút nổi cuộn nhanh lên đầu trang (Scroll to top).

3. **Chạy Offline 100% & Sẵn sàng đưa lên GitHub Pages**:
   - Không cần cài web server phức tạp: Nhấp đúp chuột mở trực tiếp file `index.html` trong trình duyệt là chạy ngay (nhờ file `data.js` và `fuse.min.js` cục bộ, không bị lỗi CORS).
   - Tương thích hoàn toàn với GitHub Pages khi đẩy lên repository.

---

## 📁 Cấu trúc thư mục

| Tên file | Mô tả |
| :--- | :--- |
| `index.html` | Giao diện web tra cứu chính (HTML + CSS + JS thuần, siêu nhẹ, tải tức thì) |
| `cauhoi.xlsx` | File Excel gốc chứa dữ liệu 180 câu hỏi và đáp án |
| `data.js` | Dữ liệu câu hỏi được xuất sang JS (dùng cho chạy offline trực tiếp qua `file://`) |
| `data.json` | Dữ liệu câu hỏi dạng JSON chuẩn (dùng cho fetch API hoặc tích hợp ứng dụng khác) |
| `fuse.min.js` | Thư viện tìm kiếm mờ Fuse.js 6.6.2 lưu sẵn để hoạt động khi không có internet |
| `convert.py` | Script Python tự động đọc `cauhoi.xlsx` và cập nhật lại `data.json` & `data.js` |

---

## 🛠 Hướng dẫn sử dụng

### 1. Mở trang web ngay trên máy tính
- Chỉ cần nhấp đúp vào file `index.html` để mở bằng bất kỳ trình duyệt nào (Chrome, Edge, Cốc Cốc, Firefox...).

### 2. Cập nhật câu hỏi khi sửa file Excel `cauhoi.xlsx`
Khi bạn bổ sung thêm câu hỏi hoặc chỉnh sửa trong `cauhoi.xlsx`, chỉ cần chạy lệnh sau:
```bash
python convert.py
```
Script sẽ tự động đọc toàn bộ câu hỏi, làm sạch dữ liệu, tìm đáp án đúng và xuất ra lại `data.json` và `data.js`. Sau đó chỉ cần tải lại trang web (F5).

### 3. Đưa lên GitHub Pages (tương tự skyprotect.github.io)
1. Tạo một repository mới trên GitHub (ví dụ: `tracnghiem-daihoi14`).
2. Tải các file lên repository:
   - `index.html`
   - `data.js`
   - `data.json`
   - `fuse.min.js`
3. Vào **Settings** của repository -> **Pages** -> Tại mục **Build and deployment**, chọn Branch `main` (hoặc `master`) và thư mục `/ (root)`, nhấn **Save**.
4. Sau 1–2 phút, trang web của bạn sẽ hoạt động trực tuyến tại đường dẫn:
   `https://skyprotect.github.io/<tên-repo>/`
