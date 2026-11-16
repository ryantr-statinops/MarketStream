# 04 · Mô hình dữ liệu

## Nguyên tắc

Schema này là điểm khởi đầu cho dữ liệu thị trường dạng chuỗi thời gian. Cần điều chỉnh theo loại dữ liệu được chọn (OHLCV, trades, quotes hoặc order book).

## Thực thể dự kiến

### `market_observation` (curated)

| Trường | Ý nghĩa | Quy ước gợi ý |
|---|---|---|
| `source` | Nguồn/sàn cung cấp | mã ngắn ổn định |
| `market` | Cặp giao dịch | ví dụ `BTC-USDT`, theo quy ước được chọn |
| `event_time` | Thời điểm sự kiện | UTC, lưu rõ độ chính xác |
| `ingested_at` | Thời điểm pipeline nhận dữ liệu | UTC |
| `observation_type` | Loại dữ liệu | ví dụ `ohlcv`, `trade` |
| `price` | Giá hoặc giá đóng cửa | kiểu số thập phân chính xác |
| `quantity` | Khối lượng | đơn vị phải được ghi rõ |
| `open`, `high`, `low`, `close` | Giá OHLC, nếu áp dụng | kiểu số thập phân |
| `interval` | Cửa sổ nến, nếu áp dụng | ví dụ `1m`, `1h` |
| `trade_id` | ID giao dịch, nếu nguồn cung cấp | dùng cho dedup trades |
| `run_id` | Mã lần chạy ingestion | liên kết log và kiểm tra |
| `schema_version` | Phiên bản schema | tăng khi thay đổi có ý nghĩa |

Không phải mọi cột đều áp dụng cho mọi loại quan sát. Có thể tách bảng theo loại dữ liệu sau khi chốt yêu cầu.

## Khóa và chống trùng

- Nến: thường dùng `(source, market, interval, event_time)`.
- Giao dịch: ưu tiên `(source, market, trade_id)`; nếu không có ID, cần quy tắc thay thế được ghi rõ.
- Quotes/order book: khóa phụ thuộc vào sequence number hoặc timestamp và loại snapshot/delta.

Đây là khóa gợi ý, chưa phải quyết định cuối cùng.

## Metadata lần chạy

Bảng/log `ingestion_run` nên lưu `run_id`, nguồn, khoảng thời gian yêu cầu, thời điểm bắt đầu/kết thúc, trạng thái, số bản ghi đọc/ghi/bỏ qua, số lỗi và phiên bản code/schema.

## Chất lượng và đơn vị

- Timestamp lưu UTC; timezone nguồn được ghi nhận nếu cần.
- Giá và khối lượng không nên dùng kiểu floating point nhị phân cho dữ liệu tài chính cần độ chính xác.
- Đơn vị base/quote asset và cách tính volume phải được định nghĩa.
- Tách giá trị thiếu khỏi giá trị 0; không tự điền dữ liệu nếu chưa có quy tắc.
