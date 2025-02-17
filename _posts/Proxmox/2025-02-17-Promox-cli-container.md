---
title: Proxmox CLI "Container Management"
date: 2025-02-17 00:00:00 +0700
categories: [Proxmox]
tags: [ảo hóa, virtualization, container]    
image:
  path: assets/img/proxmox-5.png
---

## List Containers
```sh
pct list
```
## Create or Restore a Container
```sh
pct create <vmid> <ostemplate> [OPTIONS]
```
## Start the Container
```sh
pct start <vmid> [OPTIONS]
```
## Create a Container Clone/Copy
```sh
pct clone <vmid> <newid> [OPTIONS]
```
## Suspend the Container - This is Experimental
```sh
pct suspend <vmid>
```
## Resume the Container
```sh
pct resume <vmid>
```
## Stop the Container
This will abruptly stop all processes running in the container.
```sh
pct stop <vmid> [OPTIONS]
```
## Shutdown the Container
This will trigger a clean shutdown of the container, see lxc-stop(1) for details
```sh
pct shutdown <vmid> [OPTIONS]
```
## Destroy the Container (Also Delete All Uses Files)
```sh
pct destroy <vmid> [OPTIONS]
```
## Show CT Status
```sh
pct status <vmid> [OPTIONS]
```
## Migrate the Container to Another Node. Creates a New Bigration Task
```sh
pct migrate <vmid> <target> [OPTIONS]
```
## Get Container Configuration
```sh
pct config <vmid> [OPTIONS]
```
## Print the List of Assigned CPU Sets
```sh
pct cpusets
```
## Get Container Configuration, Including Pending Changes
```sh
pct pending <vmid>
```
## Reboot the Container by Shutting it Down, and Starting it Again. Applies Pending Changes.
```sh
pct reboot <vmid> [OPTIONS]
```
## Create or Restore a Container
```sh
pct restore <vmid> <ostemplate> [OPTIONS]
```
## Set Container Options
```sh
pct set <vmid> [OPTIONS]
```
## Create a Template.
```sh
pct template <vmid>
```
## Unlock the VM.
```sh
pct unlock <vmid>
```