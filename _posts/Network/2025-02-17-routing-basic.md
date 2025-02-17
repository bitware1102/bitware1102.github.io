---
title: Routing Basic 
date: 2025-02-17 00:00:00 +0700
categories: [Network]
tags: [routing, CCNA,]     # TAG names should always be lowercase
image:
  path:
---
### 1. **Static Routing (Định tuyến tĩnh)**

- **Chức năng**: Người quản trị mạng thiết lập thủ công các tuyến đường cố định trên router.
- **Nhiệm vụ**: Cung cấp đường dẫn cụ thể cho các gói tin đến một mạng đích. Không có khả năng tự động điều chỉnh khi mạng thay đổi.
- **Ưu điểm**: Đơn giản, dễ triển khai trong các mạng nhỏ.
- **Nhược điểm**: Không linh hoạt, phải cập nhật thủ công khi có thay đổi trong mạng.
- **Sử dụng khi nào**: Mạng nhỏ, đơn giản, không có yêu cầu thay đổi nhiều.

### 2. **Dynamic Routing (Định tuyến động)**

- **Chức năng**: Các router sử dụng giao thức định tuyến động để tự động học và cập nhật các tuyến đường mới khi mạng thay đổi.
- **Nhiệm vụ**: Tự động điều chỉnh bảng định tuyến, giảm bớt khối lượng công việc của người quản trị khi mạng mở rộng hoặc thay đổi.
- **Ưu điểm**: Tự động cập nhật khi có sự thay đổi mạng, dễ mở rộng.
- **Nhược điểm**: Tốn tài nguyên mạng và tính toán của router do phải trao đổi thông tin liên tục.
- **Sử dụng khi nào**: Mạng lớn và phức tạp cần tự động hóa quá trình định tuyến.

### Các giao thức định tuyến động phổ biến:

### a. **RIP (Routing Information Protocol)**

- **Chức năng**: Là một giao thức định tuyến khoảng cách vector (distance vector) dựa trên số "hops" (bước nhảy) để xác định tuyến đường.
- **Nhiệm vụ**: Tìm tuyến đường ngắn nhất dựa trên số bước nhảy giữa các router.
- **Ưu điểm**: Dễ cấu hình, phù hợp cho các mạng nhỏ.
- **Nhược điểm**: Hạn chế về quy mô (chỉ hỗ trợ tối đa 15 bước nhảy), không hiệu quả trong mạng lớn.
- **Sử dụng khi nào**: Mạng nhỏ hoặc mạng tĩnh, ít thay đổi.

### b. **OSPF (Open Shortest Path First)**

- **Chức năng**: Là một giao thức định tuyến trạng thái đường liên kết (link-state) sử dụng thuật toán Dijkstra để tìm tuyến đường ngắn nhất.
- **Nhiệm vụ**: Tính toán tuyến đường tối ưu dựa trên băng thông, độ trễ và các yếu tố khác.
- **Ưu điểm**: Hiệu quả trong các mạng lớn, hội tụ nhanh, khả năng mở rộng tốt.
- **Nhược điểm**: Cấu hình phức tạp hơn so với RIP.
- **Sử dụng khi nào**: Mạng lớn, nhiều router, yêu cầu khả năng hội tụ nhanh.

### c. **EIGRP (Enhanced Interior Gateway Routing Protocol)**

- **Chức năng**: Là một giao thức định tuyến hybrid, kết hợp giữa distance vector và link-state. Sử dụng các số liệu như băng thông, độ trễ, và độ tin cậy để xác định tuyến đường.
- **Nhiệm vụ**: Cung cấp tuyến đường tối ưu và hội tụ nhanh trong mạng.
- **Ưu điểm**: Hiệu quả trong mạng lớn, dễ cấu hình, hội tụ nhanh.
- **Nhược điểm**: Là giao thức độc quyền của Cisco (chỉ dùng được trên thiết bị Cisco).
- **Sử dụng khi nào**: Mạng vừa và lớn, sử dụng thiết bị Cisco.

### d. **BGP (Border Gateway Protocol)**

- **Chức năng**: Là giao thức định tuyến ngoại vi (exterior gateway protocol), sử dụng cho việc trao đổi thông tin định tuyến giữa các hệ thống tự trị (Autonomous Systems - AS).
- **Nhiệm vụ**: Kết nối các mạng khác nhau (ví dụ: kết nối giữa các ISP hoặc giữa doanh nghiệp với ISP).
- **Ưu điểm**: Khả năng mở rộng tốt, dùng cho mạng lớn hoặc giữa các tổ chức.
- **Nhược điểm**: Cấu hình phức tạp, hội tụ chậm hơn so với các giao thức định tuyến nội bộ.
- **Sử dụng khi nào**: Trong mạng lớn, đặc biệt là trên internet giữa các ISP hoặc doanh nghiệp lớn.

### 3. **Default Routing (Định tuyến mặc định)**

- **Chức năng**: Chỉ định một tuyến đường mặc định mà router sẽ sử dụng khi không tìm thấy tuyến đường cụ thể trong bảng định tuyến.
- **Nhiệm vụ**: Đảm bảo các gói tin không bị mất khi không có tuyến đường cụ thể, bằng cách gửi đến một gateway mặc định (thường là kết nối với một router khác hoặc mạng lớn hơn như internet).
- **Ưu điểm**: Dễ cấu hình, giảm tải bảng định tuyến.
- **Nhược điểm**: Không tối ưu nếu có nhiều mạng phức tạp.
- **Sử dụng khi nào**: Trong mạng nhỏ hoặc khi có một cổng thoát duy nhất (thường là cổng ra internet).

### 4. **Policy-Based Routing (Định tuyến dựa trên chính sách)**

- **Chức năng**: Định tuyến các gói tin dựa trên các chính sách cụ thể được cấu hình bởi quản trị viên (ví dụ: dựa trên loại lưu lượng, địa chỉ nguồn/đích).
- **Nhiệm vụ**: Điều khiển lưu lượng mạng theo các tiêu chí tùy chỉnh thay vì dựa hoàn toàn vào bảng định tuyến.
- **Ưu điểm**: Linh hoạt, có thể kiểm soát lưu lượng mạng theo chính sách.
- **Nhược điểm**: Cấu hình phức tạp hơn, cần quản lý chính sách cẩn thận.
- **Sử dụng khi nào**: Khi cần định tuyến lưu lượng theo tiêu chí cụ thể, ví dụ như phân tách lưu lượng theo loại dịch vụ (VoIP, dữ liệu...).

### 5. **Multipath Routing (Định tuyến đa đường)**

- **Chức năng**: Cho phép nhiều tuyến đường cùng tồn tại cho một đích đến, nhằm mục đích cân bằng tải hoặc dự phòng.
- **Nhiệm vụ**: Cân bằng tải hoặc dự phòng khi có nhiều tuyến đường đến đích.
- **Ưu điểm**: Tăng hiệu suất mạng và khả năng dự phòng.
- **Nhược điểm**: Cấu hình có thể phức tạp hơn trong mạng lớn.
- **Sử dụng khi nào**: Khi muốn cân bằng tải hoặc cung cấp tính năng dự phòng giữa nhiều tuyến đường.

### Tóm tắt:

- **Static Routing**: Định tuyến thủ công, phù hợp cho mạng nhỏ, ít thay đổi.
- **Dynamic Routing**: Tự động cập nhật, phù hợp cho mạng lớn và phức tạp, với các giao thức như RIP, OSPF, EIGRP, và BGP.
- **Default Routing**: Sử dụng khi không có tuyến đường cụ thể, thường dùng để ra ngoài mạng nội bộ.
- **Policy-Based Routing**: Định tuyến dựa trên chính sách tùy chỉnh.
- **Multipath Routing**: Cân bằng tải hoặc dự phòng giữa nhiều tuyến đường.

Mỗi loại định tuyến có những ưu và nhược điểm riêng, và được sử dụng tùy vào yêu cầu của hệ thống mạng.