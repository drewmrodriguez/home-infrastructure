- Homelab
A personal infrastructure lab built to develop and demonstrate hands-on skills in networking, virtualization, and systems administration. This lab serves as a living environment for testing configurations, self-hosting services, and preparing for professional IT and network engineering roles.

Certifications: CompTIA A+ · CompTIA Network+ · CompTIA Security+ (in progress)

Drew — Cloud & Network Engineering student | Mobile, AL
This lab is actively maintained and updated as new technologies and configurations are explored.


- Network Overview

 Diagram coming soon 

The lab is segmented into multiple VLANs managed by pfSense, with traffic isolation enforced between zones. A managed switch handles inter-VLAN routing at Layer 2, while pfSense acts as the firewall and gateway.

- Infrastructure Summary
Networking:
Router: pfSense Gateway, DHCP, DNS, firewall rules
Switching: Managed SwitchVLAN trunking, port-based segmentationVLAN Design802.1QTraffic isolation across lab zones
DNS: pfSense + UnboundLocal DNS resolution, ad blocking

Hardware:
Dell OptiPlex 7050 Primary server — Proxmox VE hypervisor node
HP EliteDeskDedicated NVR — PoE security camera recording and management

Virtualization:
Proxmox VEPrimary hypervisor on OptiPlex 7050 — VM and LXC management

Self-Hosted Services:
NVR Software: HP EliteDeskPoE security camera recording and footage management
Pi-hole: Proxmox VMNetwork-wide DNS ad blocking and local DNS resolution
Jellyfin: Proxmox VMSelf-hosted media server
Home Assistant: Proxmox VMHome automation and IoT device management

- VLAN Segmentation
The network is divided into isolated segments to enforce least-privilege traffic flow and practice real-world network security concepts.
(e.g., 10) Management Hypervisor and infrastructure access
(e.g., 20) Servers Proxmox VMs Pi-hole, Jellyfin, Home Assistant
(e.g., 30) IoT Home Assistant devices — isolated from main LAN
(e.g., 40) Cameras PoE security cameras — NVR-only access (planned)
(e.g., 50) Trusted Primary workstations
(e.g., 99) Guest Internet-only, no LAN access

Firewall rules enforce that VLAN zones cannot communicate laterally unless explicitly permitted.


- Repository Structure
homelab/
├── README.md                  ← This file — lab overview
├── networking/
│   ├── pfsense-config.md      ← Firewall rules, DHCP, DNS setup
│   ├── vlan-design.md         ← VLAN layout and rationale
│   └── switch-setup.md        ← Managed switch configuration
├── virtualization/
│   ├── proxmox-setup.md       ← Proxmox install, VM templates, storage
│   ├── hyper-v-notes.md       ← Windows Server / Hyper-V configuration
│   └── vm-inventory.md        ← Active VMs and their roles
├── services/
│   ├── self-hosted-apps.md    ← Installed services and access methods
│   └── dns-config.md          ← Local DNS records and split-horizon setup
└── docs/
    └── diagrams/              ← Network diagrams (draw.io / PNG)

- Skills Demonstrated

Network segmentation — VLAN design and firewall rule enforcement with pfSense
Virtualization — VM and LXC management on Proxmox VE (Dell OptiPlex 7050)
Security fundamentals — Least-privilege access, traffic isolation, firewall policy
Systems administration — Linux and Windows Server configuration in a lab context
Documentation — Infrastructure documented in a professional, reproducible format


- Goals & Roadmap

 Add network topology diagram
 Document pfSense firewall ruleset
 Complete VLAN configuration writeups
 Add Proxmox VM templates and provisioning notes
 Isolate PoE cameras onto dedicated VLAN with NVR-only firewall rules
 Integrate IDS/IPS (e.g., Snort or Suricata via pfSense)
 Explore log aggregation 



