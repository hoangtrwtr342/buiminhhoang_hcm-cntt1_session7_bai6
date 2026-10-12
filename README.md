Bài 6 : Đánh giá An toàn Script Quản lý Trang trại Thông minh


Phần 1 — Phân tích lệnh AI

Lệnh Remove-Item -Path "C:\*" -Recurse -Force cố xóa các tệp và thư mục bên trong ổ C: theo cách đệ quy. Việc này có thể làm mất dữ liệu cá nhân, xóa tệp hệ thống hoặc khiến Windows và các ứng dụng không hoạt động. Xóa file chủ yếu giải phóng dung lượng đĩa, không phải RAM.


Quy trình thẩm định an toàn gồm 3 bước:

1. Soi lệnh và phạm vi: nhận diện lệnh xóa Remove-Item, đường dẫn quá rộng C:\* và các tùy chọn -Recurse, -Force.
2. 
3. Kiểm tra an toàn: dùng -WhatIf để xem trước thao tác; nếu cần thử, chỉ dùng bản sao dữ liệu trong thư mục sandbox.
4. 
5. Chỉ thực thi lệnh đã xác minh, giới hạn đúng phạm vi và lưu nhật ký để có thể kiểm tra lại. Với lệnh xóa toàn bộ nội dung C:\ này, không thực thi.

Phần 2 — Script PowerShell an toàn

Get-Content ".\water_log.txt" | Select-String -Pattern "WARNING" | ForEach-Object { $_.Line } | echo >> incident.txt

Write-Host "Hoan thanh"
