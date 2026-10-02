# 👻 Module Bảo Mật Ghost
**Công Cụ Tăng Cường Bảo Mật Windows & Azure Dựa Trên PowerShell**

> **Tăng cường bảo mật chủ động cho các điểm cuối Windows và môi trường Azure.** Ghost cung cấp các chức năng tăng cường dựa trên PowerShell có thể giúp giảm các vector tấn công phổ biến bằng cách vô hiệu hóa các dịch vụ và giao thức không cần thiết.

## ⚠️ Tuyên Bố Từ Chối Trách Nhiệm Quan Trọng

**CẦN KIỂM THỬ**: Luôn kiểm thử Ghost trong môi trường không phải sản xuất trước. Vô hiệu hóa các dịch vụ có thể ảnh hưởng đến các chức năng kinh doanh hợp pháp.

**KHÔNG CÓ BẢO HÀNH**: Mặc dù Ghost nhắm vào các vector tấn công phổ biến, không có công cụ bảo mật nào có thể ngăn chặn tất cả các cuộc tấn công. Đây là một thành phần của chiến lược bảo mật toàn diện.

**TÁC ĐỘNG VẬN HÀNH**: Một số chức năng có thể ảnh hưởng đến chức năng hệ thống. Xem xét cẩn thận từng cài đặt trước khi triển khai.

**ĐÁNH GIÁ CHUYÊN NGHIỆP**: Đối với môi trường sản xuất, hãy tham khảo ý kiến các chuyên gia bảo mật để đảm bảo các cài đặt phù hợp với nhu cầu của tổ chức bạn.

## 📊 Bối Cảnh Bảo Mật

Thiệt hại từ Ransomware đã đạt **57 tỷ đô la vào năm 2025**, với nghiên cứu chỉ ra rằng nhiều cuộc tấn công thành công khai thác các dịch vụ Windows cơ bản và cấu hình sai. Các vector tấn công phổ biến bao gồm:

- **90% các sự cố ransomware** liên quan đến khai thác RDP
- **Lỗ hổng SMBv1** đã cho phép các cuộc tấn công như WannaCry và NotPetya
- **Macro tài liệu** vẫn là phương thức phân phối malware chính
- **Tấn công dựa trên USB** tiếp tục nhắm vào các mạng bị cô lập
- **Lạm dụng PowerShell** đã tăng đáng kể trong những năm gần đây

## 🛡️ Chức Năng Bảo Mật Ghost

Ghost cung cấp **16 chức năng tăng cường Windows** cộng với **tích hợp bảo mật Azure**:

### Tăng Cường Điểm Cuối Windows

| Chức Năng | Mục Đích | Cân Nhắc |
|----------|---------|----------------|
| `Set-RDP` | Quản lý truy cập Remote Desktop | Có thể ảnh hưởng đến quản trị từ xa |
| `Set-SMBv1` | Kiểm soát giao thức SMB cũ | Cần thiết cho các hệ thống rất cũ |
| `Set-AutoRun` | Kiểm soát AutoPlay/AutoRun | Có thể ảnh hưởng đến sự tiện lợi của người dùng |
| `Set-USBStorage` | Hạn chế thiết bị lưu trữ USB | Có thể ảnh hưởng đến việc sử dụng USB hợp pháp |
| `Set-Macros` | Kiểm soát thực thi macro Office | Có thể ảnh hưởng đến tài liệu có macro |
| `Set-PSRemoting` | Quản lý PowerShell remoting | Có thể ảnh hưởng đến quản lý từ xa |
| `Set-WinRM` | Kiểm soát Windows Remote Management | Có thể ảnh hưởng đến quản trị từ xa |
| `Set-LLMNR` | Quản lý giao thức phân giải tên | Thường an toàn khi vô hiệu hóa |
| `Set-NetBIOS` | Kiểm soát NetBIOS qua TCP/IP | Có thể ảnh hưởng đến ứng dụng cũ |
| `Set-AdminShares` | Quản lý chia sẻ quản trị | Có thể ảnh hưởng đến truy cập file từ xa |
| `Set-Telemetry` | Kiểm soát thu thập dữ liệu | Có thể ảnh hưởng đến khả năng chẩn đoán |
| `Set-GuestAccount` | Quản lý tài khoản khách | Thường an toàn khi vô hiệu hóa |
| `Set-ICMP` | Kiểm soát phản hồi ping | Có thể ảnh hưởng đến chẩn đoán mạng |
| `Set-RemoteAssistance` | Quản lý Remote Assistance | Có thể ảnh hưởng đến hoạt động helpdesk |
| `Set-NetworkDiscovery` | Kiểm soát khám phá mạng | Có thể ảnh hưởng đến duyệt mạng |
| `Set-Firewall` | Quản lý Windows Firewall | Quan trọng cho bảo mật mạng |

### Bảo Mật Azure Cloud

| Chức Năng | Mục Đích | Yêu Cầu |
|----------|---------|--------------|
| `Set-AzureSecurityDefaults` | Kích hoạt bảo mật Azure AD cơ bản | Quyền Microsoft Graph |
| `Set-AzureConditionalAccess` | Cấu hình chính sách truy cập | Cấp phép Azure AD P1/P2 |
| `Set-AzurePrivilegedUsers` | Kiểm toán tài khoản đặc quyền | Quyền Global Admin |

### Tùy Chọn Triển Khai Doanh Nghiệp

| Phương Thức | Trường Hợp Sử Dụng | Yêu Cầu |
|--------|----------|--------------|
| **Thực Thi Trực Tiếp** | Kiểm thử, môi trường nhỏ | Quyền admin cục bộ |
| **Group Policy** | Môi trường domain | Domain admin, quản lý GP |
| **Microsoft Intune** | Thiết bị quản lý cloud | Cấp phép Intune, Graph API |

## 🚀 Bắt Đầu Nhanh

### Đánh Giá Bảo Mật
```powershell
# Tải module Ghost
Invoke-WebRequest 'https://raw.githubusercontent.com/jimrtyler/Ghost/main/Ghost.ps1' -OutFile .\Ghost.ps1
Get-Content .\Ghost.ps1
. .\Ghost.ps1

# Kiểm tra tình trạng bảo mật hiện tại
Get-Ghost
```

### Tăng Cường Cơ Bản (Kiểm Thử Trước)
```powershell
# Tăng cường cần thiết - kiểm thử trong môi trường lab trước
Set-Ghost -SMBv1 -AutoRun -Macros

# Xem xét các thay đổi
Get-Ghost
```

### Triển Khai Doanh Nghiệp
```powershell
# Triển khai Group Policy (môi trường domain)
Set-Ghost -SMBv1 -AutoRun -GroupPolicy

# Triển khai Intune (thiết bị quản lý cloud)
Set-Ghost -SMBv1 -RDP -USBStorage -Intune
```

## 📋 Phương Thức Cài Đặt

### Tùy Chọn 1: Tải Xuống Trực Tiếp (Kiểm Thử)
```powershell
Invoke-WebRequest 'https://raw.githubusercontent.com/jimrtyler/Ghost/main/Ghost.ps1' -OutFile .\Ghost.ps1
Get-Content .\Ghost.ps1
. .\Ghost.ps1
```

### Tùy Chọn 2: Cài Đặt Module
```powershell
# Cài đặt từ PowerShell Gallery (khi có sẵn)
Install-Module Ghost -Scope CurrentUser
Import-Module Ghost
```

### Tùy Chọn 3: Triển Khai Doanh Nghiệp
```powershell
# Sao chép đến vị trí mạng cho triển khai Group Policy
# Cấu hình script Intune PowerShell cho triển khai cloud
```

## 💼 Ví Dụ Trường Hợp Sử Dụng

### Doanh Nghiệp Nhỏ
```powershell
# Bảo vệ cơ bản với tác động tối thiểu
Set-Ghost -SMBv1 -AutoRun -Macros -ICMP
```

### Môi Trường Chăm Sóc Sức Khỏe
```powershell
# Tăng cường tập trung vào HIPAA
Set-Ghost -SMBv1 -RDP -USBStorage -AdminShares -Telemetry
```

### Dịch Vụ Tài Chính
```powershell
# Cấu hình bảo mật cao
Set-Ghost -RDP -SMBv1 -AutoRun -USBStorage -Macros -PSRemoting -AdminShares
```

### Tổ Chức Cloud-First
```powershell
# Triển khai được quản lý bởi Intune
Connect-IntuneGhost -Interactive
Set-Ghost -SMBv1 -RDP -AutoRun -Macros -Intune
```

## 🔍 Chi Tiết Chức Năng

### Chức Năng Tăng Cường Cốt Lõi

#### Dịch Vụ Mạng
- **RDP**: Chặn truy cập remote desktop hoặc ngẫu nhiên hóa port
- **SMBv1**: Vô hiệu hóa giao thức chia sẻ file cũ
- **ICMP**: Ngăn phản hồi ping cho reconnaissance
- **LLMNR/NetBIOS**: Chặn giao thức phân giải tên cũ

#### Bảo Mật Ứng Dụng
- **Macros**: Vô hiệu hóa thực thi macro trong ứng dụng Office
- **AutoRun**: Ngăn thực thi tự động từ media di động

#### Quản Lý Từ Xa
- **PSRemoting**: Vô hiệu hóa phiên PowerShell từ xa
- **WinRM**: Dừng Windows Remote Management
- **Remote Assistance**: Chặn kết nối remote assistance

#### Kiểm Soát Truy Cập
- **Admin Shares**: Vô hiệu hóa chia sẻ C$, ADMIN$
- **Guest Account**: Vô hiệu hóa truy cập tài khoản khách
- **USB Storage**: Hạn chế sử dụng thiết bị USB

### Tích Hợp Azure
```powershell
# Kết nối đến Azure tenant
Connect-AzureGhost -Interactive

# Kích hoạt security defaults
Set-AzureSecurityDefaults -Enable

# Cấu hình conditional access
Set-AzureConditionalAccess -BlockLegacyAuth -RequireMFA

# Kiểm toán người dùng đặc quyền
Set-AzurePrivilegedUsers -AuditOnly
```

### Tích Hợp Intune (Mới trong v2)
```powershell
# Kết nối đến Intune
Connect-IntuneGhost -Interactive

# Triển khai qua chính sách Intune
Set-IntuneGhost -Settings @{
    RDP = $true
    SMBv1 = $true
    USBStorage = $true
    Macros = $true
}
```

## ⚠️ Cân Nhắc Quan Trọng

### Yêu Cầu Kiểm Thử
- **Môi Trường Lab**: Kiểm thử tất cả cài đặt trong môi trường cô lập trước
- **Triển Khai Từng Giai Đoạn**: Mở rộng dần để xác định vấn đề
- **Kế Hoạch Rollback**: Đảm bảo bạn có thể hoàn nguyên thay đổi nếu cần
- **Tài Liệu**: Ghi lại cài đặt nào hoạt động cho môi trường của bạn

### Tác Động Tiềm Năng
- **Năng Suất Người Dùng**: Một số cài đặt có thể ảnh hưởng đến quy trình làm việc hàng ngày
- **Ứng Dụng Cũ**: Hệ thống cũ có thể yêu cầu một số giao thức
- **Truy Cập Từ Xa**: Xem xét tác động đến quản trị từ xa hợp pháp
- **Quy Trình Kinh Doanh**: Xác minh cài đặt không làm hỏng chức năng quan trọng

### Giới Hạn Bảo Mật
- **Phòng Thủ Chiều Sâu**: Ghost là một lớp bảo mật, không phải giải pháp hoàn chỉnh
- **Quản Lý Liên Tục**: Bảo mật yêu cầu giám sát và cập nhật liên tục
- **Đào Tạo Người Dùng**: Kiểm soát kỹ thuật phải kết hợp với nhận thức bảo mật
- **Tiến Hóa Mối Đe Dọa**: Phương thức tấn công mới có thể vượt qua bảo vệ hiện tại

## 🎯 Ví Dụ Kịch Bản Tấn Công

Mặc dù Ghost nhắm vào các vector tấn công phổ biến, việc ngăn chặn cụ thể phụ thuộc vào triển khai và kiểm thử phù hợp:

### Tấn Công Kiểu WannaCry
- **Giảm Thiểu**: `Set-Ghost -SMBv1` vô hiệu hóa giao thức dễ bị tổn thương
- **Cân Nhắc**: Đảm bảo không có hệ thống cũ nào yêu cầu SMBv1

### Ransomware Dựa Trên RDP
- **Giảm Thiểu**: `Set-Ghost -RDP` chặn truy cập remote desktop
- **Cân Nhắc**: Có thể cần phương thức truy cập từ xa thay thế

### Malware Dựa Trên Tài Liệu
- **Giảm Thiểu**: `Set-Ghost -Macros` vô hiệu hóa thực thi macro
- **Cân Nhắc**: Có thể ảnh hưởng đến tài liệu có macro hợp pháp

### Mối Đe Dọa Qua USB
- **Giảm Thiểu**: `Set-Ghost -USBStorage -AutoRun` hạn chế chức năng USB
- **Cân Nhắc**: Có thể ảnh hưởng đến việc sử dụng thiết bị USB hợp pháp

## 🏢 Tính Năng Doanh Nghiệp

### Hỗ Trợ Group Policy
```powershell
# Áp dụng cài đặt qua registry Group Policy
Set-Ghost -SMBv1 -RDP -AutoRun -GroupPolicy

# Cài đặt áp dụng domain-wide sau khi GP refresh
gpupdate /force
```

### Tích Hợp Microsoft Intune
```powershell
# Tạo chính sách Intune cho cài đặt Ghost
Set-IntuneGhost -Settings $GhostSettings -Interactive

# Chính sách triển khai tự động đến thiết bị được quản lý
```

### Báo Cáo Tuân Thủ
```powershell
# Tạo báo cáo đánh giá bảo mật
Get-Ghost | Export-Csv -Path "Kiểm-Toán-Bảo-Mật-$(Get-Date -Format 'yyyy-MM-dd').csv"

# Báo cáo tình trạng bảo mật Azure
Get-AzureGhost | Out-File "Báo-Cáo-Bảo-Mật-Azure.txt"
```

## 📚 Thực Hành Tốt Nhất

### Trước Triển Khai
1. **Tài Liệu Trạng Thái Hiện Tại**: Chạy `Get-Ghost` trước thay đổi
2. **Kiểm Thử Kỹ Lưỡng**: Xác thực trong môi trường không phải sản xuất
3. **Kế Hoạch Rollback**: Biết cách hoàn nguyên từng cài đặt
4. **Xem Xét Stakeholder**: Đảm bảo các đơn vị kinh doanh phê duyệt thay đổi

### Trong Quá Trình Triển Khai
1. **Phương Pháp Từng Giai Đoạn**: Triển khai đến nhóm pilot trước
2. **Giám Sát Tác Động**: Theo dõi khiếu nại người dùng hoặc vấn đề hệ thống
3. **Tài Liệu Vấn Đề**: Ghi lại bất kỳ vấn đề nào để tham khảo tương lai
4. **Thông Báo Thay Đổi**: Thông báo cho người dùng về cải tiến bảo mật

### Sau Triển Khai
1. **Đánh Giá Định Kỳ**: Chạy `Get-Ghost` định kỳ để xác minh cài đặt
2. **Cập Nhật Tài Liệu**: Giữ cấu hình bảo mật luôn cập nhật
3. **Xem Xét Hiệu Quả**: Giám sát các sự cố bảo mật
4. **Cải Tiến Liên Tục**: Điều chỉnh cài đặt dựa trên bối cảnh mối đe dọa

## 🔧 Khắc Phục Sự Cố

### Vấn Đề Thường Gặp
- **Lỗi Quyền**: Đảm bảo phiên PowerShell được nâng quyền
- **Phụ Thuộc Dịch Vụ**: Một số dịch vụ có thể có phụ thuộc
- **Tương Thích Ứng Dụng**: Kiểm thử với ứng dụng kinh doanh
- **Kết Nối Mạng**: Xác minh truy cập từ xa vẫn hoạt động

### Tùy Chọn Khôi Phục
```powershell
# Kích hoạt lại dịch vụ cụ thể nếu cần
Set-RDP -Enable
Set-SMBv1 -Enable
Set-AutoRun -Enable
Set-Macros -Enable
```

## 👨‍💻 Về Tác Giả

**Jim Tyler** - Microsoft MVP cho PowerShell
- **YouTube**: [@PowerShellEngineer](https://youtube.com/@PowerShellEngineer) (10,000+ người đăng ký)
- **Newsletter**: [PowerShell.News](https://powershell.news) - Thông tin bảo mật hàng tuần
- **Tác Giả**: "PowerShell for Systems Engineers"
- **Kinh Nghiệm**: Hàng thập kỷ tự động hóa PowerShell và bảo mật Windows

## 📄 Giấy Phép & Từ Chối Trách Nhiệm

### Giấy Phép MIT
Ghost được cung cấp dưới Giấy phép MIT cho việc sử dụng, sửa đổi và phân phối miễn phí.

### Từ Chối Trách Nhiệm Bảo Mật
- **Không Bảo Hành**: Ghost được cung cấp "như hiện tại" không có bảo hành dưới bất kỳ hình thức nào
- **Cần Kiểm Thử**: Luôn kiểm thử trong môi trường không phải sản xuất trước
- **Hướng Dẫn Chuyên Nghiệp**: Tham khảo chuyên gia bảo mật cho triển khai sản xuất
- **Tác Động Vận Hành**: Tác giả không chịu trách nhiệm cho bất kỳ gián đoạn vận hành nào
- **Bảo Mật Toàn Diện**: Ghost là một thành phần của chiến lược bảo mật hoàn chỉnh

### Hỗ Trợ
- **GitHub Issues**: [Báo cáo lỗi hoặc yêu cầu tính năng](https://github.com/jimrtyler/Ghost/issues)
- **Tài Liệu**: Sử dụng `Get-Help <function> -Full` để được trợ giúp chi tiết
- **Cộng Đồng**: Diễn đàn cộng đồng PowerShell và bảo mật

---

**🔒 Tăng cường tình trạng bảo mật của bạn với Ghost - nhưng luôn kiểm thử trước.**

```powershell
# Bắt đầu với đánh giá, không phải giả định
Get-Ghost
```

**⭐ Gắn sao cho repository này nếu Ghost giúp cải thiện tình trạng bảo mật của bạn!**