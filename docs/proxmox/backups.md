# Proxmox VM Backup Configuration

## Overview

Configured scheduled backups for the Ubuntu Server virtual machine hosted on Proxmox VE.

## Environment

- **Hypervisor:** Proxmox VE
- **Node:** HL-Hackerjaxz
- **Virtual machine:** ubuntu-server
- **VM ID:** 100
- **Virtual disk:** 32 GB
- **Backup storage:** local
- **Backup directory:** `/var/lib/vz/dump/`

## Backup Configuration

| Setting | Configuration |
|---|---|
| Schedule | Every Sunday at 2:00 AM |
| Backup mode | Snapshot |
| Compression | ZSTD |
| Retention | Keep last 2 backups |
| Selected VM | 100 (ubuntu-server) |

Snapshot mode allows the VM to remain running during backup.

## Initial Backup Verification

The initial manual backup completed successfully on October 13, 2026.

- **Archive:** `vzdump-qemu-100-2026_10_13-18_33_05.vma.zst`
- **Size:** Approximately 5.3 GB
- **Duration:** 1 minute and 19 seconds
- **Result:** Successful

The archive was verified in the Proxmox backup directory.

## Services Protected

The VM hosts these Docker services:

- Jellyfin
- Homepage
- Uptime Kuma
- Portainer

Data stored on the VM's virtual disk is included. Media and other data stored on separate machines are not included.

## Storage Considerations

Backups are currently stored on the same physical Proxmox server as the VM. This helps with VM-level recovery but does not protect against failure of the host or its storage.

The local filesystem had approximately 70 GB available when the backup was configured. Retention is limited to two backups.

## Future Improvements

- Configure a separate backup destination on another physical machine or disk.
- Implement off-host backups after the Linux Mint storage expansion.
- Test the restoration procedure.
- Periodically review backup success and available storage.

## Lessons Learned

- Created and verified a VM backup using `vzdump`.
- Learned how ZSTD compression reduces backup size.
- Configured a recurring backup schedule and retention policy.
- Identified the importance of storing backups separately from the systems they protect.
