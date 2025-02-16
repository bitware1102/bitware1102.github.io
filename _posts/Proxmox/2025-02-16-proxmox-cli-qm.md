---
title: Proxmox Cheatsheet CLI "QM"
date: 2025-02-16 00:00:00 +0700
categories: [Proxmox]
tags: [ảo hóa, virtualization, qm]     # TAG names should always be lowercase
image:  #banner
---


# Proxmox QM Commands

## Giới thiệu

`qm` là công cụ dòng lệnh để quản lý máy ảo trên Proxmox VE. Dưới đây là danh sách các lệnh `qm` phổ biến giúp bạn tạo, quản lý và giám sát máy ảo trên hệ thống Proxmox.

---

## 📋 Danh sách VM
```sh
qm list
```

---

## 🛠️ Tạo và khôi phục máy ảo
```sh
qm create <vmid>
```

Tạo máy ảo với các thông số cụ thể:
```sh
qm create <vmid> --name <vm-name> --cores <number-of-cores> --memory <memory-size-in-bytes> --scsi0 file=<vg-name>:<size-in-gb> --cdrom local:<iso-name> --net0 virtio,bridge=<bridge-name>
```

---

## ▶️ Khởi động và quản lý VM
```sh
qm start <vmid>       # Khởi động máy ảo
qm suspend <vmid>     # Tạm dừng máy ảo
qm shutdown <vmid>    # Tắt máy ảo
qm reboot <vmid>      # Khởi động lại máy ảo
qm reset <vmid>       # Reset máy ảo
qm stop <vmid>        # Dừng máy ảo ngay lập tức
```

---

## 🗑️ Xóa và quản lý tài nguyên VM
```sh
qm destroy <vmid>    # Xóa máy ảo và toàn bộ dữ liệu liên quan
qm cleanup <vmid>    # Dọn dẹp tài nguyên của VM
```

---

## 🔍 Giám sát và Debug VM
```sh
qm monitor <vmid>    # Truy cập giao diện Qemu Monitor
qm pending <vmid>    # Xem cấu hình VM (cả giá trị hiện tại và giá trị chờ)
qm sendkey <vmid> <key> [OPTIONS]  # Gửi tín hiệu bàn phím đến VM
qm showcmd <vmid> [OPTIONS]  # Hiển thị lệnh khởi động VM (debug)
qm status <vmid>    # Hiển thị trạng thái của VM
qm unlock <vmid>    # Mở khóa máy ảo
```

---

## 🖥️ Clone, Migrate và Template VM
```sh
qm clone <vmid> <newid>    # Clone VM
qm clone <vmid> <newid> --full --name <name>    # Clone đầy đủ và đặt tên
qm migrate <vmid> <target-node>    # Di chuyển VM đến node khác
qm template <vmid>    # Tạo Template từ VM
```

---

## ⚙️ Cấu hình VM
```sh
qm set <vmid> [OPTIONS]    # Cấu hình VM
```

---

## 📌 Lưu ý
- `<vmid>`: ID của máy ảo cần thao tác
- `<newid>`: ID của máy ảo mới khi clone
- `<target-node>`: Node đích khi di chuyển VM
- `<vg-name>`: Volume Group lưu trữ đĩa cứng
- `<iso-name>`: Tên file ISO để cài đặt OS
- `<bridge-name>`: Cầu nối mạng cho VM

---

## 🔗 Tham khảo thêm
- [Proxmox Official Documentation](https://pve.proxmox.com/wiki/Main_Page)

---

🚀 **Tài liệu này giúp bạn quản lý máy ảo Proxmox dễ dàng hơn. Chúc bạn thành công!**