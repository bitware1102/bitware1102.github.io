---
title: File System, Raid, Storage trong Proxmox
date: 2025-02-18 00:00:00 +0700
categories: [Proxmox]
tags: [ảo hóa, virtualization, ESXi]   
image:
  path: assets/img/proxmox-5.png 
---

### **1. pmxcfs là gì?**

pmxcfs (Proxmox Cluster File System) là một hệ thống tệp **dựa trên cơ sở dữ liệu** để lưu trữ các tệp cấu hình liên quan đến:

- Các máy ảo (VMs).
- Các container (LXC).
- Các thiết lập liên quan đến cluster và dịch vụ của Proxmox VE.

Khác với các hệ thống tệp thông thường (như ext4 hoặc ZFS), pmxcfs được thiết kế để phục vụ cho **môi trường cluster**, với khả năng:

- **Đồng bộ thời gian thực** giữa các node trong cluster.
- **Lưu trữ nhỏ gọn** nhưng hiệu quả, sử dụng bộ nhớ RAM để tối ưu tốc độ truy xuất.

### **2. pmxcfs hoạt động như thế nào?**

- **Dữ liệu lưu trong RAM và trên ổ đĩa:**
    - pmxcfs lưu một bản sao dữ liệu trong **RAM** để đảm bảo truy xuất nhanh nhất.
    - Dữ liệu cũng được lưu vào **ổ đĩa** để đảm bảo tính bền vững và phục hồi khi hệ thống khởi động lại.
- **Kích thước tối đa:**
    - pmxcfs có dung lượng tối đa là **30MB** (vì nó chỉ lưu cấu hình, không lưu dữ liệu của máy ảo). Đây là dung lượng đủ lớn để lưu cấu hình của hàng nghìn máy ảo.
- **Đồng bộ thời gian thực bằng Corosync:**
    - Sử dụng **Corosync**, một dịch vụ đồng bộ hóa dữ liệu trong cluster, tất cả các tệp cấu hình trong pmxcfs được sao chép **ngay lập tức** đến các node khác.
    - Điều này đảm bảo rằng mọi node trong cluster đều có cùng một thông tin cấu hình.
  
### **3. Ưu điểm của pmxcfs**

- **Đồng nhất hóa cấu hình trong cluster:** Bạn chỉ cần thay đổi cấu hình tại một node, các node khác sẽ tự động nhận được thay đổi đó.
- **Bền vững:** Nếu một node bị lỗi, cấu hình vẫn tồn tại trên các node khác.
- **Tối ưu hiệu suất:** Việc lưu dữ liệu trong RAM giúp tăng tốc truy cập, còn lưu trên ổ đĩa đảm bảo an toàn.
- **Quản lý tập trung:** Toàn bộ cấu hình được quản lý dễ dàng mà không cần sử dụng công cụ bên ngoài.

### **4. So sánh với các hệ thống khác**

Proxmox VE là nền tảng duy nhất sử dụng pmxcfs. Trong khi đó:

- Các nền tảng khác như VMware vSphere sử dụng cơ chế lưu trữ cấu hình tập trung hoặc phi tập trung dựa trên các công cụ khác (VD: vCenter).
- pmxcfs độc đáo ở chỗ nó là một hệ thống tệp **hướng database**, nhẹ và tối ưu cho các cụm máy chủ nhỏ và vừa.

### 2. Raid 

Trong **Proxmox**, khi bạn cài đặt và chọn hệ thống file **ZFS**, bạn có thể thấy các tùy chọn như **RAID 0, RAID 1, RAID 10, RAIDZ-1, RAIDZ-2, RAIDZ-3**. Đây là các loại cấu hình RAID (Redundant Array of Independent Disks) được hỗ trợ bởi ZFS, mỗi loại có mục đích và cách hoạt động riêng:

### 1. **RAID 0 (Stripe)**

- **Cách hoạt động**: Dữ liệu được chia nhỏ và ghi lên tất cả các ổ đĩa.
- **Ưu điểm**:
    - Hiệu năng đọc/ghi cao vì tất cả các ổ đĩa đều hoạt động song song.
    - Tận dụng toàn bộ dung lượng của các ổ đĩa.
- **Nhược điểm**:
    - **Không có dự phòng dữ liệu**. Nếu 1 ổ đĩa hỏng, toàn bộ dữ liệu sẽ mất.
- **Sử dụng khi nào**: Khi bạn ưu tiên hiệu năng và không cần bảo vệ dữ liệu (ví dụ: lưu trữ dữ liệu tạm thời).

### 2. **RAID 1 (Mirror)**

- **Cách hoạt động**: Dữ liệu được ghi giống hệt lên từng ổ đĩa (mirror).
- **Ưu điểm**:
    - **Dự phòng tốt**: Dữ liệu vẫn an toàn nếu 1 ổ đĩa hỏng.
    - Hiệu năng đọc cao hơn, vì dữ liệu có thể được đọc từ bất kỳ ổ đĩa nào.
- **Nhược điểm**:
    - Hiệu năng ghi chậm hơn so với RAID 0.
    - Chỉ sử dụng được 50% dung lượng tổng (vì 1 nửa dành cho bản sao dữ liệu).
- **Sử dụng khi nào**: Khi bạn cần bảo vệ dữ liệu trên hệ thống nhỏ (2 ổ đĩa).
  
### 3. **RAID 10 (Stripe + Mirror)**

- **Cách hoạt động**: Kết hợp RAID 0 (stripe) và RAID 1 (mirror). Dữ liệu được striping để tăng tốc độ, đồng thời mỗi dữ liệu có bản sao để bảo vệ.
- **Ưu điểm**:
    - Hiệu năng đọc/ghi cao hơn RAID 1.
    - Dự phòng tốt, có thể chịu lỗi từ nhiều ổ đĩa (tùy cấu hình).
- **Nhược điểm**:
    - Yêu cầu tối thiểu 4 ổ đĩa.
    - Hiệu quả sử dụng dung lượng chỉ 50%.
- **Sử dụng khi nào**: Khi cần hiệu năng và dự phòng tốt.

### 4. **RAIDZ-1 (Tương đương RAID 5)**

- **Cách hoạt động**: Dữ liệu và thông tin parity (phục hồi lỗi) được phân phối trên các ổ đĩa. Nếu 1 ổ đĩa hỏng, ZFS dùng parity để khôi phục dữ liệu.
- **Ưu điểm**:
    - Tận dụng tốt dung lượng (chỉ mất 1 ổ đĩa để lưu parity).
    - Có thể chịu lỗi của **1 ổ đĩa**.
- **Nhược điểm**:
    - Hiệu năng ghi thấp hơn RAID 0 hoặc RAID 10.
    - Không chịu được lỗi từ 2 ổ đĩa cùng lúc.
- **Sử dụng khi nào**: Khi có ít nhất 3 ổ đĩa và cần cân bằng giữa dung lượng và dự phòng.

### 5. **RAIDZ-2 (Tương đương RAID 6)**

- **Cách hoạt động**: Giống RAIDZ-1, nhưng có thêm 1 lớp parity, cho phép chịu lỗi của **2 ổ đĩa**.
- **Ưu điểm**:
    - Tốt hơn RAIDZ-1 về khả năng chịu lỗi.
    - Cân bằng giữa dung lượng và an toàn dữ liệu.
- **Nhược điểm**:
    - Hiệu năng ghi thấp hơn RAIDZ-1.
    - Cần tối thiểu **4 ổ đĩa**.
- **Sử dụng khi nào**: Khi có từ 4 ổ đĩa trở lên và muốn bảo vệ dữ liệu tốt hơn.

### 6. **RAIDZ-3**

- **Cách hoạt động**: Có tới **3 lớp parity**, cho phép chịu lỗi của **3 ổ đĩa**.
- **Ưu điểm**:
    - Bảo vệ dữ liệu tốt nhất, phù hợp cho hệ thống lớn.
    - An toàn cao khi nhiều ổ đĩa có nguy cơ lỗi.
- **Nhược điểm**:
    - Hiệu năng ghi thấp nhất.
    - Cần tối thiểu **5 ổ đĩa**.
- **Sử dụng khi nào**: Trong các hệ thống lớn, nơi an toàn dữ liệu là ưu tiên hàng đầu.

### Tóm tắt nhanh:

<table>
  <tr>
    <th>Loại RAID</th>
    <th>Ổ đĩa tối thiểu</th>
    <th>Dự phòng ổ đĩa</th>
    <th>Ưu tiên</th>
  </tr>
  <tr>
    <td>RAID 0</td>
    <td>2</td>
    <td>Không</td>
    <td>Hiệu năng.</td>
  </tr>
  <tr>
    <td>RAID 1</td>
    <td>2</td>
    <td>1 ổ đĩa</td>
    <td>An toàn dữ liệu.</td>
  </tr>
  <tr>
    <td>RAID 10</td>
    <td>4</td>
    <td>Nhiều ổ (tùy cấu hình)</td>
    <td>Hiệu năng + Dự phòng.</td>
  </tr>
  <tr>
    <td>RAIDZ-1</td>
    <td>3</td>
    <td>1 ổ đĩa</td>
    <td>Dung lượng + Dự phòng.</td>
  </tr>
  <tr>
    <td>RAIDZ-2</td>
    <td>4</td>
    <td>2 ổ đĩa</td>
    <td>Dự phòng tốt hơn.</td>
  </tr>
  <tr>
    <td>RAIDZ-3</td>
    <td>5</td>
    <td>3 ổ đĩa</td>
    <td>An toàn cao nhất.</td>
  </tr>
</table>

