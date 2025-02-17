---
title: Proxmox CLI "storage management"
date: 2025-02-17 00:00:00 +0700
categories: [Proxmox]
tags: [ảo hóa, virtualization, storage management]    
image:
  path: assets/img/proxmox-5.png
---

## Create a new storage.
```sh
pvesm add <type> <storage> [OPTIONS]
```

## Allocate disk images.
```sh
pvesm alloc <storage> <vmid> <filename> <size> [OPTIONS]
```

## Delete volume
```sh
pvesm free <volume> [OPTIONS]
```

## Delete storage configuration.
```sh
pvesm remove <storage>
```

## List storage content.
```sh
pvesm list <storage> [OPTIONS]
```

## An alias for pvesm scan lvm.
```sh
pvesm lvmscan
```

## An alias for pvesm scan lvmthin.
```sh
pvesm lvmthinscan
```

## List local LVM volume groups.
```sh
pvesm scan lvm
```

## List local LVM Thin Pools.
```sh
pvesm scan lvmthin <vg>
```

## Get status for all datastores.
```sh
pvesm status [OPTIONS]
```