---
title: Proxmox CLI "Important File/Dir Path"
date: 2025-02-17 00:00:00 +0700
categories: [Proxmox]
tags: [ảo hóa, virtualization, Debug]    
image:
  path: assets/img/proxmox-5.png
---

```sh
/etc/pve/authkey.pub    # Public key used by the ticket system
```

```sh
/etc/pve/ceph.conf      # Ceph configuration file (note: /etc/ceph/ceph.conf is a symbolic link to this)
```

```sh
/etc/pve/corosync.conf  # Corosync cluster configuration file (prior to Proxmox VE 4.x, this file was called cluster.conf)
```

```sh
/etc/pve/datacenter.cfg     #Proxmox VE data center-wide configuration (keyboard layout, proxy, …)
```

```sh
/etc/pve/domains.cfg       # Proxmox VE authentication domains
```

```sh
/etc/pve/firewall/cluster.fw    # Firewall configuration applied to all nodes
```

```sh
/etc/pve/firewall/<NAME>.fw     # Firewall configuration for individual nodes
```

```sh
/etc/pve/firewall/<VMID>.fw     # Firewall configuration for VMs and containers
```

```sh
/etc/pve/ha/crm_commands        # Displays HA operations that are currently being carried out by the CRM
```

```sh
/etc/pve/ha/manager_status      # JSON-formatted information regarding HA services on the cluster
```

```sh
/etc/pve/ha/resources.cfg       # Resources managed by high availability, and their current state
```

```sh
/etc/pve/nodes/<NAME>/config      # Node-specific configuration
```

```sh
/etc/pve/nodes/<NAME>/lxc/<VMID>.conf   # VM configuration data for LXC containers
```

```sh
/etc/pve/nodes/<NAME>/openvz/   # Prior to PVE 4.0, used for container configuration data (deprecated, removed soon)
```

```sh
/etc/pve/nodes/<NAME>/pve-ssl.key       # Private SSL key for pve-ssl.pem
```

```sh
/etc/pve/nodes/<NAME>/pve-ssl.pem       # Public SSL certificate for web server (signed by cluster CA)
```

```sh
/etc/pve/nodes/<NAME>/pveproxy-ssl.key      # Private SSL key for pveproxy-ssl.pem (optional)
```

```sh
/etc/pve/nodes/<NAME>/pveproxy-ssl.pem      # Public SSL certificate (chain) for web server (optional override for pve-ssl.pem)
```

```sh
/etc/pve/nodes/<NAME>/qemu-server/<VMID>.conf       # VM configuration data for KVM VMs
```

```sh
/etc/pve/priv/authkey.key       # Private key used by ticket system
```

```sh
/etc/pve/priv/authorized_keys       # SH keys of cluster members for authentication
```

```sh
/etc/pve/priv/ceph*         # Ceph authentication keys and associated capabilities
```

```sh
/etc/pve/priv/known_hosts      # SSH keys of the cluster members for verification
```

```sh
/etc/pve/priv/lock/*           # Lock files used by various services to ensure safe cluster-wide operations
```

```sh
/etc/pve/priv/pve-root-ca.key       # Private key of cluster CA
```

```sh
/etc/pve/priv/shadow.cfg        # Shadow password file for PVE Realm users
```

```sh
/etc/pve/priv/storage/<STORAGE-ID>.pw       # Contains the password of a storage in plain text
```

```sh
/etc/pve/priv/tfa.cfg       # Base64-encoded two-factor authentication configuration
```

```sh
/etc/pve/priv/token.cfg	    # API token secrets of all tokens
```

```sh
/etc/pve/pve-root-ca.pem    # Public certificate of cluster CA
```

```sh
/etc/pve/pve-www.key        # Private key used for generating CSRF tokens
```

```sh
/etc/pve/sdn/*              # Shared configuration files for Software Defined Networking (SDN)
```

```sh
/etc/pve/status.cfg         # Proxmox VE external metrics server configuration
```

```sh
/etc/pve/storage.cfg        # Proxmox VE storage configuration
```

```sh
/etc/pve/user.cfg           # Proxmox VE access control configuration (users/groups/…)
```

```sh
/etc/pve/virtual-guest/cpu-models.conf      # For storing custom CPU models
```

```sh
/etc/pve/vzdump.cron        # Cluster-wide vzdump backup-job schedule
```