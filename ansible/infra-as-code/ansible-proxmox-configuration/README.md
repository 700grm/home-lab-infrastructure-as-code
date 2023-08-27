# How to install Proxmox on Dell XPS 8950

# TODO:

Proxmox NETWORKING: VLANs, Bridges, and Bonds! : https://www.youtube.com/watch?v=zx5LFqyMPMU

# Create bootable USB stick
1. Create Proxmox bootable USB stick with balenaEtcher
2. Download balenaEtcher software: [https://github.com/balena-io/etcher/releases/](https://github.com/balena-io/etcher/releases/)

# Update Dell XPS 8950 Firmware
1. Downlod the latest BIOS Firmware: [link](https://www.dell.com/support/home/en-uk/product-support/servicetag/0-eHFoTHBTYmlLQWtENlA0UnlQOWdZZz090/drivers)
2. Copy to small red SanDisk USB stick
3. Insert into the front top USB port
4. Press power on button and **F12**

# Server specs
### Disks:
- sda: Samsung SSD 840 EVO 250GB
- nvme0n1: Micron 3400 NVMe 1024GB # Original
- nvme1n1: Samsung SSD 970 EVO Plus 2TB

### NIC's:
- enp2s0
- wlp3s0 # Wi-Fi

# Deploy and configure
1. Install Proxmox on a server
2. After instalation replace `bridge-ports wlp3s0` with `bridge-ports enp2s0`

```
iface vmbr0 inet static
        address <IP ADDRESS>/24
        gateway <IP ADDRESS>
        bridge-ports enp2s0
        bridge-stp off
        bridge-fd 0
```
3. Execute Ansible playbook

 # Config
 ISO files location
'/var/lib/vz/template/iso'