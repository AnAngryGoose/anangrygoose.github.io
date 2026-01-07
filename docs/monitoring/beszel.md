# Beszel 

[Github :simple-github: ](https://github.com/henrygd/beszel)
---

Beszel is a lightweight server monitoring platform that includes Docker statistics, historical data, and alert functions.

It has a friendly web interface, simple configuration, and is ready to use out of the box. It supports automatic backup, multi-user, OAuth authentication, and API access.

![Screenshot of Beszel dashboard and system page, side by side. The dashboard shows metrics from multiple connected systems, while the system page shows detailed metrics for a single system.](https://henrygd-assets.b-cdn.net/beszel/screenshot-new.png)


## Features

- **Lightweight**: Smaller and less resource-intensive than leading solutions.
- **Simple**: Easy setup with little manual configuration required.
- **Docker stats**: Tracks CPU, memory, and network usage history for each container.
- **Alerts**: Configurable alerts for CPU, memory, disk, bandwidth, temperature, load average, and status.
- **Multi-user**: Users manage their own systems. Admins can share systems across users.
- **OAuth / OIDC**: Supports many OAuth2 providers. Password auth can be disabled.
- **Automatic backups**: Save to and restore from disk or S3-compatible storage.
<!-- - **REST API**: Use or update your data in your own scripts and applications. -->

## Architecture

Beszel consists of two main components: the **hub** and the **agent**.

- **Hub**: A web application built on [PocketBase](https://pocketbase.io/) that provides a dashboard for viewing and managing connected systems.
- **Agent**: Runs on each system you want to monitor and communicates system metrics to the hub.

## Getting started

Other documentation is available on offical website, [beszel.dev](https://beszel.dev).

Install hub and local agent. The hub is central monitoring for multiple machines, this only needs to be on a single machine. The agent is used to monitor each machine. 

**compose.yaml**
  ```yaml
  # --- BESZEL HUB (The Dashboard) ---
  beszel-hub:
    image: henrygd/beszel # https://github.com/henrygd/beszel
    container_name: beszel-hub
    networks:
      - proxy_net  # To access via NPM
    ports:
      - "8090:8090"   # Exposed locally for initial setup
    volumes:
      - ${APPDATA}/beszel/data:/beszel_data
    restart: unless-stopped

  # --- BESZEL AGENT (The Sensor) ---
  beszel-agent:
    image: henrygd/beszel-agent # https://github.com/henrygd/beszel
    container_name: beszel-agent
    restart: unless-stopped
    network_mode: "host"  #  Must be on host to read actual CPU/Disk/Network

    # GPU monitoring 
    deploy:
      resources:
        reservations:
          devices:
            - driver: nvidia
              count: all
              capabilities:
                - utility  
                
    devices:
      - /dev/nvme0:/dev/nvme0 # Root Drive
      - /dev/sda:/dev/sda # Appdata Drive
      - /dev/sdb:/dev/sdb # Parity Drive  
      - /dev/sdc:/dev/sdc # Data Drive 1 
      - /dev/sdd:/dev/sdd # Data Drive 2 
    cap_add:
      - SYS_RAWIO # required for S.M.A.R.T. data
      - SYS_ADMIN # required for NVMe S.M.A.R.T. data
    
    volumes:
      - ./beszel_agent_data:/var/lib/beszel-agent
      - /var/run/docker.sock:/var/run/docker.sock:ro

      #  Map disk mounts for stroage info. For disk I/O info: /extra-filesystems/sdX = sdX must match disk from `cat /proc/diskstats`  -- double underscores adds the customs names. 
      - /mnt/hdd/WD-12345:/extra-filesystems/sdc__data_disk_1:ro 
      - /mnt/hdd/WD-67890/extra-filesystems/sdd__data_disk_2:ro 
    environment:
      - PORT=45876
      - KEY=${BESZEL_KEY} 
      - EXTRA_FILESYSTEMS=/mnt/root_drive
  ```
## Supported metrics

- **CPU usage** - Host system and Docker / Podman containers.
- **Memory usage** - Host system and containers. Includes swap and ZFS ARC.
- **Disk usage** - Host system. Supports multiple partitions and devices.
- **Disk I/O** - Host system. Supports multiple partitions and devices.
- **Network usage** - Host system and containers.
- **Load average** - Host system.
- **Temperature** - Host system sensors.
- **GPU usage / power draw** - Nvidia, AMD, and Intel.
- **Battery** - Host system battery charge.
- **Containers** - Status and metrics of all running Docker / Podman containers.
- **S.M.A.R.T.** - Host system disk health.