---
title: Proxmox CLI CloudInit
date: 2025-02-16 00:00:00 +0700
categories: [Proxmox]
tags: [ảo hóa, virtualization, cloudinit]
image:
  path: assets/img/proxmox-5.png
---

CloudInit giúp tự động hóa quá trình cấu hình máy ảo trong Proxmox. Dưới đây là một số lệnh `qm cloudinit` hữu ích để quản lý CloudInit trên các VM.

## 1. Lấy file cấu hình CloudInit tự động tạo
```sh
qm cloudinit dump <vmid> <type>
```
- **vmid**: ID của máy ảo
- **type**: Loại file CloudInit cần lấy (`network`, `meta`, `user`)

Ví dụ:
```sh
qm cloudinit dump 100 user
```
Lệnh trên sẽ lấy file `user-data` của VM có ID `100`.

---

## 2. Xem cấu hình CloudInit đang áp dụng và chờ áp dụng
```sh
qm cloudinit pending <vmid>
```
Lệnh này sẽ hiển thị cả các thiết lập hiện tại và các thiết lập đang chờ xử lý của CloudInit.

Ví dụ:
```sh
qm cloudinit pending 100
```

---

## 3. Tạo lại và cập nhật ổ đĩa CloudInit
```sh
qm cloudinit update <vmid>
```
Lệnh này sẽ tạo lại và cập nhật ổ đĩa CloudInit cho VM.

Ví dụ:
```sh
qm cloudinit update 100
```
Sau khi chạy lệnh này, các thay đổi trong CloudInit sẽ được cập nhật vào máy ảo.

---

### 🔹 **Lưu ý**:
- Trước khi chạy các lệnh trên, hãy đảm bảo rằng VM đã được cấu hình CloudInit đúng cách.
- Bạn có thể kiểm tra xem một VM có hỗ trợ CloudInit hay không bằng lệnh:
  ```sh
  qm config <vmid> | grep cloudinit
  ```

---
**Nguồn tham khảo**: [Proxmox Documentation](https://pve.proxmox.com/wiki/Cloud-Init_Support)
