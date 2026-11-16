# 03 · Kiến trúc đề xuất

## Luồng dữ liệu khái quát

```text
Nguồn market data
      ↓
Ingestion / connector
      ↓
Raw zone (giữ payload và metadata nguồn)
      ↓
Validate + normalize + deduplicate
      ↓
Curated storage
      ↓
SQL / báo cáo / dashboard (nếu nằm trong phạm vi)
```

Orchestrator hoặc scheduler điều phối các lần chạy; logging và kiểm tra chất lượng đi xuyên suốt pipeline.

## Thành phần

| Thành phần | Trách nhiệm | Ghi chú |
|---|---|---|
| Connector | Gọi API hoặc nhận luồng từ nguồn | Bắt đầu với một nguồn |
| Raw storage | Lưu dữ liệu nhận được cùng metadata | Hữu ích để replay và debug |
| Transform | Chuẩn hóa schema, timezone, đơn vị và khóa | Tách logic nghiệp vụ khỏi connector |
| Quality checks | Kiểm tra schema, null, trùng lặp và phạm vi | Lưu số liệu kiểm tra theo lần chạy |
| Curated storage | Cung cấp dữ liệu sạch cho phân tích | Chọn công nghệ sau khi chốt yêu cầu |
| Orchestrator | Lên lịch, retry và theo dõi trạng thái | Có thể bắt đầu bằng lịch chạy đơn giản |
| Consumer | Truy vấn, notebook hoặc dashboard | Dashboard là tùy chọn chưa xác nhận |

## Nguyên tắc thiết kế

- Giữ dữ liệu raw không bị ghi đè bởi bước biến đổi.
- Chuẩn hóa timestamp về UTC và ghi rõ độ phân giải thời gian.
- Tách thông tin nguồn khỏi định danh thị trường.
- Thiết kế thao tác ghi có thể retry an toàn.
- Đưa cấu hình ra khỏi mã nguồn; không ghi bí mật vào log.
- Ghi nhận phiên bản schema/logic khi có thay đổi ảnh hưởng dữ liệu.

## Lựa chọn công nghệ

Chưa chốt công nghệ vì repo hiện chưa có mã nguồn hoặc đặc tả. Khi quyết định, cần đánh giá theo: khả năng chạy cục bộ, chi phí, hỗ trợ incremental load, độ dễ quan sát, và mức độ phù hợp với mục tiêu portfolio.

## Rủi ro kiến trúc

- API giới hạn tốc độ hoặc thay đổi schema.
- Dữ liệu lịch sử có khoảng trống, sửa đổi hoặc khác biệt giữa các nguồn.
- Streaming thật làm tăng chi phí vận hành so với batch; cần xác nhận yêu cầu độ trễ trước khi chọn.
- Dữ liệu raw tăng nhanh; cần chính sách partition và retention.
