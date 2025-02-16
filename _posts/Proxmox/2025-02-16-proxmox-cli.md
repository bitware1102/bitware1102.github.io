---
title: Proxmox Cheatsheet CLI
date: 2025-02-16 00:00:00 +0700
categories: [Proxmox]
tags: [ảo hóa, virtualization]     # TAG names should always be lowercase
---

#VM Management
List VMs
qm list

Create or restore a virtual machine.
qm create <vmid>

Create or restore a virtual machine with core, memory, disks specified.
qm create <vmid> --name <vm-name> --cores <number-of-cores> --memory <memory-size-in-bytes> --scsi0 file=<vg-name>:<size-in-gb> --cdrom local:<iso-name> --net0 virtio,bridge=<bridge-name>

Start a VM
qm start <vmid>

Suspend virtual machine.
qm suspend <vmid>

Shutdown a VM
qm shutdown <vmid>

Reboot a VM
qm reboot <vmid>

Reset a VM
qm reset <vmid>

Stop a VM
qm stop <vmid>

Destroy the VM and all used/owned volumes.
Note: Removes any VM specific permissions and firewall rules
qm destroy <vmid>

Enter Qemu Monitor interface.
qm monitor <vmid>

Get the virtual machine configuration with both current and pending values.
qm pending <vmid>

Send key event to virtual machine.
qm sendkey <vmid> <key> [OPTIONS]

Show command line which is used to start the VM (debug info).
qm showcmd <vmid> [OPTIONS]

Unlock the VM.
qm unlock <vmid>

Clone a VM
qm clone <vmid> <newid>

Clone a VM in full clone mode and also set the name.
qm clone <vmid> <newid> --full --name <name>

Migrate a VM
qm migrate <vmid> <target-node>

Show VM status
qm status <vmid>

Clean up resources for a VM
qm cleanup <vmid> <clean-shutdown> <guest-requested>

Create a Template.
qm template <vmid> [OPTIONS]

Set virtual machine options (synchrounous API)
qm set <vmid> [OPTIONS]