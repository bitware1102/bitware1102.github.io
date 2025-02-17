---
title: Proxmox CLI "Disk Container"
date: 2025-02-17 00:00:00 +0700
categories: [Proxmox]
tags: [ảo hóa, virtualization, disk container]    
image:
  path: assets/img/proxmox-5.png
---

## Get the Container’s Current Disk Usage
```sh
pct df <vmid>
```
## Run a Filesystem Check (fsck) on a Container Volume
```sh
pct fsck <vmid> [OPTIONS]
```
## Run fstrim on a Chosen CT and Its Mountpoints
```sh
pct fstrim <vmid> [OPTIONS]
```
## Mount the Container’s Filesystem on the Host
This will hold a lock on the container and is meant for emergency maintenance only
as it will prevent further operations on the container other than start and stop.
```sh
pct mount <vmid>
```
## Move a rootfs-/mp-Volume to a Different Storage or to a Different Container
```sh
pct move-volume <vmid> <volume> [<storage>] [<target-vmid>] [<target-volume>] [OPTIONS]
```
## Unmount the Container’s Filesystem
```sh
pct unmount <vmid>
```
## Resize a Container Mount Point
```sh
pct resize <vmid> <disk> <size> [OPTIONS]
```
## Rescan All Storages and Update Disk Sizes and Unused Disk Images
```shpct rescan [OPTIONS]
```
## Launch a Console for the Specified Container
```sh
pct console <vmid> [OPTIONS]
```
## Launch a Shell for the Specified Container
```sh
pct enter <vmid>
```
## Launch a Command Inside the Specified Container
```sh
pct exec <vmid> [<extra-args>]
```
## Copy a File from the Container to the Local System
```sh
pct pull <vmid> <path> <destination> [OPTIONS]
```
## Copy a Local File to the Container
```sh
pct push <vmid> <file> <destination> [OPTIONS]
```