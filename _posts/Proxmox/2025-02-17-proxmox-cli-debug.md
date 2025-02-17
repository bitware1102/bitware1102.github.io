---
title: Proxmox CLI "Debug"
date: 2025-02-17 00:00:00 +0700
categories: [Proxmox]
tags: [ảo hóa, virtualization, Debug]    
image:
  path: assets/img/proxmox-5.png
---

```sh
/etc/pve/.version   # File Versions (to detect file modifications)
```
```sh
/etc/pve/.members   # Info about Cluster Members
```

```sh
/etc/pve/.vmlist    # List of all VMs
```

```sh
/etc/pve/.clusterlog    # Cluster Log (last 50 entries)
```

```sh
/etc/pve/.rrd   # RRD Data (most recent entries)
```