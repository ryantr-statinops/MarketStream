# 01 · Tổng quan dự án

## Tóm tắt

**MarketStream** được định hướng như một dự án data engineering về dữ liệu thị trường crypto: thu thập dữ liệu giá/giao dịch từ một hoặc nhiều nguồn, chuẩn hóa, lưu trữ và cung cấp dữ liệu đủ tin cậy cho truy vấn hoặc phân tích.

> Đây là diễn giải tạm thời từ tên dự án và ngữ cảnh repo. Cần đối chiếu với nội dung ý tưởng gốc trước khi xem là mô tả chính thức.

## Vấn đề cần giải quyết

Dữ liệu thị trường thường đến từ nhiều API hoặc luồng sự kiện, có định dạng và tần suất khác nhau. Một pipeline có cấu trúc giúp theo dõi nguồn, xử lý dữ liệu đến trễ/trùng lặp, và tạo dữ liệu lịch sử nhất quán để phân tích.

## Mục tiêu dự kiến

- Xây dựng pipeline ingestion có thể chạy lặp lại và quan sát được.
- Chuẩn hóa dữ liệu theo một schema thống nhất.
- Lưu dữ liệu thô và dữ liệu đã xử lý để có thể kiểm tra nguồn gốc.
- Tạo bộ dữ liệu phục vụ truy vấn phân tích theo tài sản và thời gian.
- Thể hiện các năng lực data engineering: orchestration, chất lượng dữ liệu, logging, tài liệu và triển khai.

## Người dùng dự kiến

- Người phát triển muốn tìm hiểu hoặc trình diễn một pipeline data engineering.
- Nhà phân tích cần dữ liệu lịch sử crypto có cấu trúc.
- Người xem dashboard (nếu dashboard nằm trong phạm vi cuối cùng).

## Giá trị đầu ra

1. Một pipeline có thể tái chạy và có thể giải thích.
2. Dữ liệu được kiểm tra, chuẩn hóa và truy vấn được.
3. Tài liệu kiến trúc, cách chạy cục bộ và các giới hạn dữ liệu rõ ràng.

## Ngoài mục tiêu mặc định

Các mục sau chưa được xác nhận là yêu cầu: giao dịch tự động, khuyến nghị đầu tư, dự báo giá, dashboard thời gian thực cho người dùng cuối, hoặc cam kết dữ liệu production-grade.

## Chỉ số thành công đề xuất

- Pipeline chạy end-to-end từ nguồn đến bảng phân tích.
- Có thể chạy lại cùng khoảng thời gian mà không tạo bản ghi sai lệch do trùng lặp.
- Có kiểm tra cho trường bắt buộc, timestamp, phạm vi giá và tính đầy đủ cơ bản.
- Có hướng dẫn tái tạo môi trường và truy vấn dữ liệu mẫu.
