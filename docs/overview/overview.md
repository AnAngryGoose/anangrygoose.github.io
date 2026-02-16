# Overview

This is just reference and notes for all my project stuff. Most of this is just for personal reference, but some of it may be useful.  

This covers a large scope. Nothing in particular, will add as I do things.

Currently using list below (mostly, kinda sorta)

--- 

## Infrastructure

---

<div class="grid cards" markdown>

-   :simple-debian:{ .lg .middle } __Debian__

    ---

    Install Debian Linux to run the server

    [:octicons-arrow-right-24: Getting started](/infrastructure/gettingstarted/pcsetup/)

-   :material-merge:{ .lg .middle } __MergerFS + SNAPRaid__

    ---

    Merge your drives as one, then create snapshots of your data. 

    [:octicons-arrow-right-24: Filesystems](/infrastructure/filesystem/management/)

-   :material-docker:{ .lg .middle } __Docker__

    ---

    Platform for building, packaging, and distributing containerized applications

    [:octicons-arrow-right-24: Docker](/infrastructure/docker/dockerinstall/)

-   :material-git:{ .lg .middle } __git__

    ---

    Version control system. Track your files, use actions, and more.  

    [:octicons-arrow-right-24: git](/infrastructure/git/git/)

</div>


<!-- :simple-debian: **Debian Linux** - It's debian

:simple-ansible: **Ansible** - IT Automation. Easily create and manage multiple servers. 

:simple-proxmox: **Proxmox** - Lightweight, easily managed hypervisor. 

:material-merge: **MergerFS** - FUSE-based union filesystem. Merge multiple drives to be read and used as one. Lots of options. 

:material-backup-restore: **SNAPRaid** - SNAPshot Raid. Take a snapshot of a pool (mergerFS), create parity, rebuild if a drive dies. 

:material-docker: **Docker** - Platform for building, packaging, and distributing containerized applications

:material-git: **git** - version control system  -->

## Network Management

---

<div class="grid cards" markdown>

-   :simple-opnsense:{ .lg .middle } __OPNSense__

    ---

    An open source, easy-to-use and easy-to-build FreeBSD based firewall and routing platform.

    [:octicons-arrow-right-24: Installing OPNSense](/networking/opnsense/opnsense/)

-   :simple-tplink:{ .lg .middle } __Omada Controller__

    ---

    TP-Link Omada Software Controller (also known as TP-Link Omada Network Application) to centrally manage TP-Link Omada Hardware
    
    [:octicons-arrow-right-24: Omada Controller](/services/omada/omada/)

-   :simple-tailscale:{ .lg .middle } __Tailscale__

    ---

    A Zero Trust identity-based connectivity platform. Allows remote, secure access to a defined network (tailnet). 

    [:octicons-arrow-right-24: Tailscale](/services/tailscale/tailscale/) 

-   :simple-cloudflare:{ .lg .middle } __cloudflare__

    ---

    DNS server, domain registrar, CDN. Primarily used here for tunnels. 
    
    [:octicons-arrow-right-24: Cloudflare](/networking/cloudflare/tunnels/)

</div>

<!-- :simple-opnsense: **OPNSense** - An open source, easy-to-use and easy-to-build FreeBSD based firewall and routing platform.

:simple-tplink: **Omada Controller** - TP-Link Omada Software Controller (also known as TP-Link Omada Network Application) to centrally manage TP-Link Omada Hardware

:simple-tailscale: **Tailscale** - A Zero Trust identity-based connectivity platform. Allows remote, secure access to a defined network (tailnet). 

:simple-adguard: **Adguard Home** - A network-wide software for blocking ads & tracking.

:simple-cloudflare: **Cloudflare** - DNS server, domain registrar, CDN. Primarily used here for tunnels. -->

## Cloud Services & File sharing

---

<div class="grid cards" markdown>


-   :simple-nextcloud:{ .lg .middle } __Nextcloud__

    ---

    A suite of client-server software for creating and using file hosting services
    [:octicons-arrow-right-24: Nextcloud Setup](/services/nextcloud/nextcloud/)

-   :simple-immich:{ .lg .middle } __Immich__
  
    ---

    Self-hosted photo and video management solution

    [:octicons-arrow-right-24: Immich Setup](/services/immich/immich/)

-   :material-folder:{ .lg .middle } __Filebrowser Quantum__
  
    ---

    Web-based file manager with configurable sources, OIDC authentication, Office file support, and real-time indexing. 

    [:octicons-arrow-right-24: Filebrowser Quantum Setup](/services/filebrowser/filebrowser/)



</div>

<!-- :simple-nextcloud: **Nextcloud** - A suite of client-server software for creating and using file hosting services

:simple-immich: **Immich** - Self-hosted photo and video management solution

:material-folder: **Filebrowser Quantum** - Web-based file manager with configurable sources, OIDC authentication, Office file support, and real-time indexing.  -->

## Media Server

---

<div class="grid cards" markdown>

-   :simple-plex:{ .lg .middle } __Plex Media Server__

    ---

    Media server for streaming content

    [:octicons-arrow-right-24: Plex Setup](/services/plex/plex/)

-   :simple-jellyfin:{ .lg .middle } __Jellyfin__

    ---

    Media server for streaming content. Less convoluted and more privacy focused than Plex.

    [:octicons-arrow-right-24: Jellyfin Setup](/services/jellyfin/jellyfin/)

-   :simple-radarr:{ .lg .middle } __Arr stack__
  
    ---

    *arr software for media management. Radarr, sonarr, etc.

    [:octicons-arrow-right-24: Arr Stack Setup](/services/servarr/radarr/)

</div>

<!-- :simple-plex: **Plex Media Server** - Media server for streaming content

:simple-jellyfin: **Jellyfin** - Media server for streaming content. Less convoluted and more privacy focused than Plex.

:simple-radarr: ***Arr stack** - *arr software for media management. Radarr, sonarr, etc. -->

## Smart Home

---

<div class="grid cards" markdown>
-   :simple-homeassistant:{ .lg .middle } __Home Assistant__
    
    ---

    Home Assistant is free and open-source software used to enable centralized home automation.

    [:octicons-arrow-right-24: Home Assistant Setup](/services/homeassistant/homeassistant/)


-   :simple-mqtt:{ .lg .middle } __MQTT__
  
      ---

    Message Queuing Telemetry Transport - it is a lightweight, publish-subscribe network protocol designed for low-bandwidth, unreliable, or high-latency networks. 

    [:octicons-arrow-right-24: MQTT Setup](/services/mqtt/mqtt/)
</div>


<!-- :simple-homeassistant: **Home Assistant** - Home Assistant is free and open-source software used to enable centralized home automation.

:simple-mqtt: **MQTT** - Message Queuing Telemetry Transport - it is
a lightweight, publish-subscribe network protocol designed for low-bandwidth, unreliable, or high-latency networks.  -->

## Generative AI

---

<div class="grid cards" markdown>
-   :simple-ollama:{ .lg .middle } __Ollama__
    
    ---

    Lightweight, extensible framework for building and running language models on the local machine. It provides a simple API for creating, running, and managing models, as well as a library of pre-built models that can be easily used in a variety of applications.

    [:octicons-arrow-right-24: Ollama Setup](/services/ollama/ollama/)
</div>

<!-- :simple-ollama: **Ollama** - Lightweight, extensible framework for building and running language models on the local machine. It provides a simple API for creating, running, and managing models, as well as a library of pre-built models that can be easily used in a variety of applications. -->

## Utilities
---

<div class="grid cards" markdown>

-   :material-file-convert:{ .lg .middle } __convertx__

    ---

    Self hosted, web based file convertor with support for A LOT of file types.

    [:octicons-arrow-right-24: convertx Setup](/services/convertx/convertx/)

-  :material-file-pdf-box:{ .lg .middle } __BentoPDF__
  
    ---

    Web based PDF editor. Does all work in browser. 

    [:octicons-arrow-right-24: BentoPDF Setup](/services/bentopdf/bentopdf/)

-   :material-tools:{ .lg .middle } __ittools__

    ---

    Collection of handy online tools for developers, with great UX. 

    [:octicons-arrow-right-24: ittools Setup](/services/ittools/ittools/)

-   :material-pen:{ .lg .middle } __drawio__
  
    ---

    self hosted version of drawio. draw.io is a JavaScript, client-side editor for general diagramming. 

    [:octicons-arrow-right-24: drawio Setup](/services/drawio/drawio/)

<!-- 
**convertx** - Self hosted, web based file convertor with support for A LOT of file types.

:material-file-pdf-box: **BentoPDF** - Web based PDF editor. Does all work in browser. 

**ittools** - Collection of handy online tools for developers, with great UX. 

**drawio** - self hosted version of drawio. draw.io is a JavaScript, client-side editor for general diagramming.  -->