# Proxmox

[Official Docs :simple-proxmox: ](https://pve.proxmox.com/pve-docs/)

---

## Overview

---

Proxmox Virtual Environment is a complete, open-source server management platform for enterprise virtualization. It tightly integrates the KVM hypervisor and Linux Containers (LXC), software-defined storage and networking functionality, on a single platform. With the integrated web-based user interface you can manage VMs and containers, high availability for clusters, or the integrated disaster recovery tools with ease.

## Installation 

---

* Download the ISO: https://www.proxmox.com/en/products/proxmox-virtual-environment/get-started

* Create bootable disk (ventoy is nice)

* Choose the desired info when prompted.
    * For The filesystem:
        * If not planning to use HA replication, have low RAM (<32GB), or just need a simpler system, stick with ext4. 

!!!note
    Using ext4 will create an LVM. This is a standard linux setup and will allow for easy resizing later. 


## Initial Setup

---

### Update

After installation, the system should be accessible via a browser at `<selected-IP>:8006`

* First, update the system
    * `Node > Updates > Repositories`
        * Select No-Subscription repo
    * `Node > Updates > Refresh`
        * Select upgrade, let it download, and reboot. 

### Initial VM setup





