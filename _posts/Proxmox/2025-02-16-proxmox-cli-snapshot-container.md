---
title: Proxmox CLI "Snapshot container"
date: 2025-02-16 00:00:00 +0700
categories: [Proxmox]
tags: [ảo hóa, virtualization, Snapshot]
image:
  path: assets/img/proxmox-5.png
---
## Snapshot a Container
```sh
pct snapshot <vmid> <snapname> [OPTIONS]
```
## List all Snapshots
```sh
pct listsnapshot <vmid>
```
## List all Snapshots
Rollback LXC State to Specified Snapshot
```sh
pct rollback <vmid> <snapname> [OPTIONS]
```
## List all Snapshots
Delete a LXC Snapshot
```sh
pct delsnapshot <vmid> <snapname> [OPTIONS]
```
```