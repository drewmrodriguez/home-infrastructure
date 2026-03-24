# home-infrastructure
A self-hosted home infrastructure built around a Proxmox hypervisor, managed networking, and a dedicated NVR system for security camera management.

- Network Topology
Internet
    │
Amazon Eero (Router / Gateway)
    │
Managed Switch
    ├── Dell OptiPlex  (Proxmox — primary server)
    ├── HP ProDesk     (NVR — camera storage & live monitor)
    ├── PoE Camera 1
    └── PoE Camera 2

PoE cameras are powered directly by the managed switch — no separate power adapters needed.


- Hardware
DeviceRoleNotesAmazon EeroRouter / gatewayISP uplink, DHCPManaged SwitchNetwork backbonePowers PoE camerasDell OptiPlexPrimary serverRuns Proxmox VEHP ProDeskNVR / camera serverFootage storage + live displayPoE Camera ×2SurveillanceConnected to managed switch

- Proxmox VMs & Services
The Dell OptiPlex runs Proxmox VE as a Type 1 hypervisor, hosting the following services as VMs or LXC containers:
Pi-hole

Purpose: Network-wide ad and tracker blocking
Scope: Acts as the primary DNS resolver for all devices on the network
Why: Reduces ads and telemetry across every device without per-device configuration

Plex Media Server

Purpose: Self-hosted media streaming
Scope: Serves local media library to devices on the network (and remotely)
Why: Full control over media without recurring subscription costs

Home Assistant

Purpose: Home automation and smart device management
Scope: Centralises control of smart home devices, automations, and dashboards
Why: Local-first automation with no cloud dependency


- Security Camera System
The HP ProDesk runs a dedicated NVR (Network Video Recorder) setup:

Receives footage from 2 PoE IP cameras connected via the managed switch
Stores recorded footage locally
Drives a live monitor for real-time viewing
PoE eliminates the need for separate camera power runs


- Goals & Roadmap

 Add VLANs to isolate IoT devices, cameras, and trusted hosts
 Set up a reverse proxy (e.g. Nginx Proxy Manager or Traefik) for internal service access
 Add offsite or NAS-based backups for critical VMs
 Explore Tailscale or WireGuard for secure remote access
 Document Proxmox VM specs and resource allocation


- Tech Stack
Proxmox VE Pi-hole Plex Home Assistant PoE networking

This homelab is a work in progress. See the roadmap above for planned improvements.
