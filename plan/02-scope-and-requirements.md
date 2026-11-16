# 02 · Phạm vi và yêu cầu

## Phạm vi MVP đề xuất

### Ingestion

- Chọn một nguồn dữ liệu công khai và một nhóm thị trường/tài sản nhỏ để bắt đầu.
- Lấy dữ liệu lịch sử theo khoảng thời gian; bổ sung cập nhật định kỳ sau khi luồng lịch sử ổn định.
- Ghi nhận thời điểm lấy dữ liệu, nguồn, tham số truy vấn và trạng thái chạy.

### Xử lý

- Chuẩn hóa tên trường, mã tài sản, đơn vị giá/khối lượng và timestamp về UTC.
- Phát hiện dữ liệu thiếu trường, giá trị ngoài miền hợp lệ, bản ghi trùng và timestamp bất thường.
- Giữ nguyên payload thô hoặc một bản lưu tương đương để có thể đối chiếu.

### Lưu trữ và truy vấn

- Tách dữ liệu thô khỏi dữ liệu đã chuẩn hóa.
- Có khóa xác định duy nhất cho một bản ghi thị trường (ví dụ: nguồn + thị trường + thời điểm + loại dữ liệu).
- Có ít nhất một truy vấn hoặc báo cáo mẫu theo tài sản và khoảng thời gian.

### Vận hành

- Cấu hình bằng biến môi trường hoặc tệp cấu hình không chứa bí mật.
- Log được số bản ghi nhận, số bản ghi loại bỏ/lỗi và thời lượng chạy.
- Có hướng dẫn chạy cục bộ và xử lý lỗi phổ biến.

## Ngoài phạm vi MVP (tạm thời)

- Đặt lệnh hoặc kết nối tài khoản giao dịch.
- Dự báo/đưa ra tín hiệu mua bán.
- Bao phủ mọi sàn giao dịch và mọi tài sản.
- SLA, độ sẵn sàng hoặc độ trễ cấp production.

## Yêu cầu phi chức năng

- **Tính lặp lại:** cùng input và phiên bản logic cho kết quả nhất quán.
- **Tính idempotent:** chạy lại một khoảng dữ liệu không nhân đôi kết quả.
- **Khả năng kiểm tra:** truy vết được bản ghi đã xử lý về nguồn và lần chạy.
- **Bảo mật:** không commit API key/token; dùng secret manager hoặc biến môi trường khi cần.
- **Khả năng mở rộng:** có thể thêm nguồn hoặc loại dữ liệu mà không phá schema hiện có.

## Tiêu chí nghiệm thu MVP

- Từ hướng dẫn trong repo, người khác có thể cấu hình và chạy pipeline trên một khoảng thời gian mẫu.
- Dữ liệu raw và curated có thể phân biệt; schema và đơn vị được mô tả.
- Chạy lại không làm sai số lượng bản ghi duy nhất.
- Báo cáo/log nêu rõ thành công, lỗi và số lượng bản ghi.
- Có ví dụ truy vấn tạo ra kết quả hữu ích.

## Cần xác nhận

Nguồn dữ liệu, phạm vi tài sản, loại dữ liệu (OHLCV, trades, order book…), mức độ realtime, công nghệ bắt buộc và việc có dashboard hay không đang chờ nội dung ý tưởng gốc.
