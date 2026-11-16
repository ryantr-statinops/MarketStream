# 06 · Quyết định và câu hỏi mở

## Giả định đang dùng

| ID | Giả định | Lý do | Trạng thái |
|---|---|---|---|
| A1 | MarketStream liên quan đến crypto market data | Suy ra từ tên repo và tiêu đề cửa sổ “Gợi ý project crypto DE” | Cần xác nhận |
| A2 | Dự án tập trung vào data engineering/pipeline | Suy ra từ “DE” trong tiêu đề cửa sổ | Cần xác nhận |
| A3 | Có thể bắt đầu bằng batch ingestion | MVP dễ kiểm chứng trước khi cần streaming liên tục | Đề xuất |
| A4 | Tài liệu trong thư mục này là tiếng Việt | Theo ngôn ngữ yêu cầu hiện tại | Đang áp dụng |

## Quyết định cần chốt

| Chủ đề | Câu hỏi | Trạng thái |
|---|---|---|
| Nguồn | Sàn/API hoặc dataset nào? | Chưa chốt |
| Loại dữ liệu | OHLCV, trades, order book, funding rate hay loại khác? | Chưa chốt |
| Tần suất | Batch theo lịch hay stream liên tục? Độ trễ mục tiêu là bao nhiêu? | Chưa chốt |
| Phạm vi | Những tài sản và cặp giao dịch nào thuộc MVP? | Chưa chốt |
| Lưu trữ | Data lake, warehouse hay database nào phù hợp? | Chưa chốt |
| Điều phối | Chạy thủ công, scheduler đơn giản hay orchestrator? | Chưa chốt |
| Giao diện | Chỉ cần SQL/notebook hay cần dashboard? | Chưa chốt |
| Triển khai | Chạy local, cloud hay cả hai? | Chưa chốt |
| Mục tiêu | Portfolio, học tập, nghiên cứu hay sản phẩm dùng thật? | Chưa chốt |

## Nhật ký quyết định

| Ngày | Quyết định | Lý do | Tác động |
|---|---|---|---|
| 2026-11-16 | Tạo bộ tài liệu kế hoạch ban đầu với giả định được gắn nhãn | Repo chưa có mã nguồn/tài liệu; chưa truy cập được nội dung share trong phiên này | Cần rà soát sau khi ý tưởng gốc được cung cấp |

## Cách cập nhật

Khi có nội dung ý tưởng gốc, cập nhật `01-project-overview.md` và `02-scope-and-requirements.md` trước; sau đó rà soát các đề xuất trong kiến trúc, dữ liệu và roadmap. Chuyển giả định đã xác nhận sang quyết định có ngày và lý do; xóa những phần không còn đúng.
