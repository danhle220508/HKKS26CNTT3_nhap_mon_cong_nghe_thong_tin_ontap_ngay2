
# BÀI LÀM – ÔN TẬP NGÀY 2

- **Họ tên:Lê Đức Anh**
- **Lớp:CNTT3**
- **Link repository:**
- **Hệ điều hành (Windows/macOS):Windows**

## Bài 1. Lọc log thủ công

### Lệnh đã chạy

```powershell

Get-Content .\logs\access.log | Select-String "ERROR" > logs\error_report.txt
```

### 2 dòng lỗi đầu tiên trong error_report.txt

```text
 2025-10-18 08:17:59 [ERROR] Khong tim thay trang /lich-thi (404)
2025-10-18 08:25:55 [ERROR] Het thoi gian cho (timeout)
```

## Bài 2. Đếm bằng pipeline

### Lệnh

```powershell
et-Content .\logs\access.log | Select-String "WARNING" | Measure-Object -Line
 Get-Content .\logs\payment.log | Select-String "ERROR" | Measure-Object -Line
```

### Kết quả đếm (Windows: giá trị Count; macOS: con số in ra)

```text
WARNING trong access.log:
Lines Words Characters Property
----- ----- ---------- --------
    4
ERROR trong payment.log:
Lines Words Characters Property
----- ----- ---------- --------
    3
```

## Bài 3. Chạy script auto_warning (.ps1 hoặc .sh)

### Lệnh chạy (Windows: nếu dùng Phụ lục 2 thì ghi cả 2 lệnh)

```powershell
 .\auto_warning.ps1
```

### Nội dung file logs/warning_report.txt

```text
=== CANH BAO THANH TOAN ===

2025-10-18 09:19:13 [WARNING] Cong thanh toan phan hoi cham
2025-10-18 09:28:16 [WARNING] Nhieu lan nhap sai ma OTP
2025-10-18 09:43:01 [WARNING] So du vi gan bang hoc phi
2025-10-18 09:46:22 [WARNING] So du vi gan bang hoc phi
2025-10-18 09:49:43 [WARNING] So du vi gan bang hoc phi
```

## Bài 4. Báo cáo tổng hợp

### Các lệnh đã chạy

```shell
"=== TONG HOP ACCESS LOG ===" > logs/tong_hop_ngay2.txt 
Get-Content logs/access.log | Select-String "ERROR" >> logs/tong_hop_ngay2.txt 
(Get-Content logs/payment.log | Select-String "WARNING" | Measure-Object -Line).Lines >> logs/tong_hop_ngay2.txt
```

### Nội dung file logs/tong_hop_ngay2.txt

```text
=== TONG HOP ACCESS LOG ===

2025-10-18 08:17:59 [ERROR] Khong tim thay trang /lich-thi (404)
2025-10-18 08:25:55 [ERROR] Het thoi gian cho (timeout)
2025-10-18 08:33:51 [ERROR] Ket noi may chu du lieu that bai
2025-10-18 08:37:19 [ERROR] Ket noi may chu du lieu that bai
2025-10-18 08:49:43 [ERROR] Het thoi gian cho (timeout)
2025-10-18 08:53:11 [ERROR] Het thoi gian cho (timeout)
```

## Bài 5. Câu hỏi ngắn

- **a)** Toán tử > dùng để ghi đè và Toán tử >> dùng để ghi nối tiếp
- **b)** Nội dung file tong_hop_ngay2.txt sẽ bị mất dòng tiêu đề đầu tiên ==== TONG HOP ACCESS LOG === vì lệnh thứ hai đã ghi đè lên toàn bộ file.
- **c)** Đường dẫn tương đối giúp mã nguồn có tính linh hoạt cao, có thể chạy mượt mà trên bất kỳ máy tính nào mà không bị lỗi "sai đường dẫn"

## Tự chấm (điền sau khi có đáp án)

- **Điểm tự chấm:** ..../100
- **Lỗi mình đã mắc và cách sửa:**

