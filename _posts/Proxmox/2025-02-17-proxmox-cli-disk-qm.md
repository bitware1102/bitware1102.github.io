---
title: Proxmox CLI "disk qm"
date: 2025-02-17 00:00:00 +0700
categories: [Proxmox]
tags: [ảo hóa, virtualization, disk qm]     # TAG names should always be lowercase
image:
  path: assets/img/proxmox-5.png
---
# Proxmox `qm` Disk Commands

## 📦 Import an External Disk Image as an Unused Disk in a VM
To import an external disk image as an unused disk in a VM. Note: The image format must be supported by `qemu-img`.

```sh
qm disk import <vmid> <source> <storage>
```
🧳 Move Volume to Different Storage or to a Different VM
To move a volume to different storage or VM.
```sh
qm disk move <vmid> <disk> [<storage>] [OPTIONS]
```
## 🔄 Rescan All Storages and Update Disk Sizes and Unused Disk Images
```sh
qm disk rescan [OPTIONS]
```
## ⏩ Extend Volume Size
```sh
qm disk resize <vmid> <disk> <size> [OPTIONS]
```
## ❌ Unlink/Delete Disk Images
```sh
qm disk unlink <vmid> --idlist <string> [OPTIONS]
```
## 🔄 Rescan Volumes
```sh
qm rescan
```