---
title: Proxmox CLI "snapshot"
date: 2025-02-17 00:00:00 +0700
categories: [Proxmox]
tags: [ảo hóa, virtualization, snapshot]  # TAG names should always be lowercase
image:
  path: assets/img/proxmox-5.png
---
## List All Snapshot 

```sh
qm listsnapshot <vmid>
```
## Snapshot a VM\\

```sh
qm delsnapshot <vmid> <snapname>
```

## Rollback a snapshot
```sh
qm rollback <vmid> <snapname>
```

## Open a terminal using a serial device
(The VM need to have a serial device configured, for example serial0: socket)

```sh
qm terminal <vmid> [OPTIONS]
```

## Proxy VM VNC traffic to stdin/stdout

```sh
qm vncproxy <vmid>
```