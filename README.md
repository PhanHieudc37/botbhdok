# Bot Thu Thập Dữ Liệu Domain 22.cn

Chương trình tự động thu thập dữ liệu domain từ trang web 22.cn sử dụng Playwright với các tính năng chống phát hiện bot.

## Tính năng

- ✅ Đăng nhập tự động vào 22.cn
- ✅ Chống phát hiện bot với các kỹ thuật tiên tiến
- ✅ Mô phỏng hành vi người dùng thật
- ✅ Thu thập dữ liệu domain từ nhiều khoảng giá (0-100, 101-500, 501-999, 1000-1999, 2000-3000, 3001-5000)
- ✅ Lưu trữ vào cơ sở dữ liệu SQLite
- ✅ Xuất dữ liệu ra file CSV theo định dạng yêu cầu
- ✅ Xử lý lỗi và retry
- ✅ Tránh trùng lặp dữ liệu

## Cài đặt

1. Cài đặt Python 3.8+ nếu chưa có
2. Cài đặt các thư viện cần thiết:

```bash
pip install -r requirements.txt
```

3. Cài đặt trình duyệt cho Playwright:

```bash
playwright install chromium
```

## Sử dụng

Chạy chương trình:

```bash
python 22cn.py
```

## Cấu trúc dữ liệu

Dữ liệu được lưu trong file `domain.db` với cấu trúc:

```sql
CREATE TABLE domains (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    name TEXT NOT NULL,           -- Tên domain
    price TEXT NOT NULL,          -- Giá hiện tại
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### Khoảng giá được thu thập:

1. **0-100**: Domain giá thấp
2. **101-500**: Domain giá trung bình thấp
3. **501-999**: Domain giá trung bình
4. **1000-1999**: Domain giá trung bình cao
5. **2000-3000**: Domain giá cao
6. **3001-5000**: Domain giá rất cao

### File xuất:

- `domains_export.csv`: File CSV chứa tất cả domain theo định dạng: 名称,当前价格

## Tính năng chống phát hiện bot

- Ẩn webdriver properties
- Mô phỏng gõ phím như người thật
- Độ trễ ngẫu nhiên giữa các thao tác
- User-Agent thật
- Headers HTTP thật
- Mô phỏng di chuyển chuột và cuộn trang

## Lưu ý

- Chương trình sẽ mở trình duyệt để bạn có thể theo dõi quá trình
- Đảm bảo thông tin đăng nhập chính xác
- Có thể cần xử lý captcha thủ công nếu xuất hiện
