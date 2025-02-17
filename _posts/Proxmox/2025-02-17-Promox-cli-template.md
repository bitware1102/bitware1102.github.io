---
title: Proxmox CLI "Template Management"
date: 2025-02-17 00:00:00 +0700
categories: [Proxmox]
tags: [ảo hóa, virtualization, template]    
image:
  path: assets/img/proxmox-5.png
---

## List All Templates
```sh
pveam available
```
## List All Templates
```sh
pveam list <storage>
```

### Download Appliance Templates
```sh
pveam download <storage> <template>
```

## Remove a Template
```sh
pveam remove <template-path>
```

### Update Container Template Database.
```sh
pveam update
```
