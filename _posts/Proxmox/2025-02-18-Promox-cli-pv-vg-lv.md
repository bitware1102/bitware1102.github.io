---
title: Proxmox CLI "pv, vg & lv mmanagement"
date: 2025-02-17 00:00:00 +0700
categories: [Proxmox]
tags: [ảo hóa, virtualization, PV, VG, LV Management]    
image:
  path: assets/img/proxmox-5.png
---

## Create a PV
```sh
pvcreate <disk-device-name>
```

## Remove a PV
```sh
pvremove <disk-device-name>
```

## List all PVs
```sh
pvs
```

## Create a VG
```sh
vgcreate <vg-name> <disk-device-name>
```

## Remove a VG
```sh
vgremove <vg-name>
```

## List all VGs

```sh
vgs
```

## Create a LV
```sh
lvcreate -L <lv-size> -n <lv-name> <vg-name>
```

## Remove a LV
```sh
lvremove <vg-name>/<lv-name>
```

## List all LVs
```sh
lvs
```