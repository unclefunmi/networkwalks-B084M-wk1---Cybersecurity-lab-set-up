<div align="center">

# 🔐 Cybersecurity Home Lab Setup

**Building and configuring a virtual cybersecurity lab for ethical hacking, penetration testing and network security practice**

</div>

<p align="center">
  <img src="https://img.shields.io/badge/Project-Cybersecurity-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/VirtualBox-v7.2.22-0070C0?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Kali%20Linux-v2026.3-E87500?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Host-Windows%2011-0078D4?style=flat-square&labelColor=000000&logo=windows&logoColor=white" />
  <img src="https://img.shields.io/badge/Network-10.0.0.0%2F24-238F89?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/IP-10.0.0.2-C00000?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Skill-Linux-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Skill-Networking-404040?style=flat-square&labelColor=0070C0" />
  <img src="https://img.shields.io/badge/Skill-Virtualization-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Ethical%20Hacking-E87500?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Penetration%20Testing-C00000?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/GitHub-Portfolio-404040?style=flat-square&labelColor=0070C0&logo=github&logoColor=white" />
</p>

---

## 📌 Project Overview
A documented personal cybersecurity lab built on a Windows 11 host using Oracle VirtualBox and Kali Linux. The lab uses an isolated VirtualBox NAT Network, a static IPv4 address for Kali, a host shared folder, and VirtualBox desktop integration.

> **Scope and safety:** This is a learning environment. Only scan, test, or attack systems that you own or have explicit permission to assess. The NAT Network provides outbound connectivity; it is not a substitute for carefully isolating intentionally vulnerable targets.

---

## Lab overview

| Component | Recorded configuration |
|---|---|
| Host operating system | Windows 11 |
| Hypervisor | Oracle VirtualBox 7.2.22 r175245 |
| Guest operating system | Kali Linux 2026.3 (Kali Rolling) |
| Guest kernel | `7.1.5+kali-amd64` |
| Guest VM | `kali-linux-2026.1-virtualbox-amd64` (original VM name; OS upgraded in place) |
| Guest network interface | `eth0` |
| VirtualBox network mode | NAT Network |
| NAT Network name | `NatNetwork` |
| IPv4 subnet | `10.0.0.0/24` |
| Kali static IPv4 | `10.0.0.2/24` |
| Default gateway | `10.0.0.1` |
| DNS resolver configured | `8.8.8.8` |
| DHCP on NAT Network | Enabled |
| Shared folder | `Downloads`, mounted in Kali at `/media/sf_Downloads` |
| Shared Clipboard | Bidirectional |
| Drag and Drop | Bidirectional |
| Guest Additions kernel modules | `7.2.22 r175245` (loaded and verified) |

The VM was originally imported as a Kali 2026.1 VirtualBox appliance and then updated in place. The final guest reports `VERSION_ID="2026.3"` in `/etc/os-release`.

---
## Build and configuration summary
**Create the NAT Network**
In VirtualBox Manager, open Tools / Network (the exact menu wording can vary by VirtualBox release), select NAT Networks, and create or edit:
- Name: NatNetwork
- IPv4 Prefix: 10.0.0.0/24
- DHCP: Enabled
The Kali VM's Adapter 1 is attached to NAT Network and the network name is NatNetwork. The virtual cable is connected.

**NAT Network Configuration**

![NAT Network Settings](./Screenshot%202026-11-06%20050155.png)

**VirtualBox Network Adapter Configuration**

![VirtualBox Adapter Settings](./Screenshot%202026-11-06%20050621.png)

---
**Configure Kali networking**
The verified guest settings are:
- Interface: eth0
- Address: 10.0.0.2/24
- Gateway: 10.0.0.1
- DNS: 8.8.8.8
The configuration was applied through Kali's NetworkManager connection settings. Exact connection profile names can differ between installations.

![Cybersecurity Lab Screenshot](./Screenshot%202026-10-30%20154024.png)

---

**Configure the shared folder**

A VirtualBox shared folder named Downloads was configured with the Windows host's Downloads directory as its source

---

**Enable clipboard and drag-and-drop**

In the powered-off VM settings, set:
- General → Advanced → Shared Clipboard: Bidirectional
- General → Advanced → Drag and Drop: Bidirectional
Both directions were manually tested after the Guest Additions update and after the Kali operating-system upgrade:
- Windows → Kali
- Kali → Windows
Both clipboard and drag-and-drop worked in both directions.

---


