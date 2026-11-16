# 05 · Lộ trình

Các giai đoạn dưới đây là lộ trình đề xuất theo đầu ra, chưa gắn ngày hoàn thành vì chưa biết thời lượng và yêu cầu chính xác.

## Giai đoạn 0 — Chốt ý tưởng

- Đọc và tóm tắt ý tưởng gốc.
- Chốt người dùng, vấn đề cần giải quyết và mục tiêu portfolio.
- Chọn loại dữ liệu, nguồn, độ trễ mong muốn và phạm vi MVP.
- Chọn tiêu chí đánh giá thành công.

**Đầu ra:** bản tổng quan và phạm vi không còn giả định trọng yếu.

## Giai đoạn 1 — Thiết kế

- Chọn nguồn dữ liệu và khảo sát API/quota/schema.
- Chốt công nghệ lưu trữ, chạy lịch và cách cấu hình.
- Chốt schema raw/curated, khóa chống trùng và partition.
- Tạo sơ đồ kiến trúc và quyết định kỹ thuật.

**Đầu ra:** kiến trúc được chốt và thiết kế dữ liệu có thể triển khai.

## Giai đoạn 2 — MVP batch

- Tạo connector cho một nguồn và một tập tài sản nhỏ.
- Nạp dữ liệu lịch sử vào raw zone.
- Chuẩn hóa, kiểm tra chất lượng và ghi curated data.
- Hỗ trợ chạy lại an toàn và truy vấn mẫu.

**Đầu ra:** pipeline end-to-end có thể chạy cục bộ.

## Giai đoạn 3 — Vận hành và trình bày

- Thêm lịch chạy, retry có giới hạn và log/metrics.
- Viết hướng dẫn setup, sơ đồ và ví dụ truy vấn.
- Thêm dashboard hoặc notebook nếu có trong phạm vi.
- Đánh giá lỗi nguồn, độ đầy đủ và hiệu năng trên dữ liệu mẫu.

**Đầu ra:** dự án có thể được người khác chạy và hiểu.

## Giai đoạn 4 — Mở rộng (tùy chọn)

- Thêm nguồn hoặc loại dữ liệu thứ hai.
- Chuyển một phần ingest sang streaming nếu độ trễ yêu cầu điều đó.
- Thêm kiểm tra freshness, cảnh báo và quản lý retention.

Chỉ mở rộng sau khi MVP có tiêu chí vận hành rõ ràng.
