# 🌐 Linux Networking Lab

## Overview
Configured networking on CentOS 7 including static IP,
IP aliasing, firewall zones, traffic capture, and network diagnostics.

## What I Implemented
- ✅ Configured Static IP using network config file
- ✅ Added Second IP Alias on same interface
- ✅ Explored Firewalld zones and services
- ✅ Captured port 80 traffic using tcpdump
- ✅ Verified open ports using ss -tulnp
- ✅ Added local DNS entry in /etc/hosts
- ✅ Traced network path using traceroute and mtr

## Key Commands Used
```bash
# Static IP configure karna
vi /etc/sysconfig/network-scripts/ifcfg-ens33
systemctl restart NetworkManager

# IP Alias add karna
ip addr add 192.168.0.200/24 dev ens33

# Firewalld zones
firewall-cmd --get-active-zones
firewall-cmd --list-all-zones
firewall-cmd --zone=public --add-service=http --permanent
firewall-cmd --reload

# tcpdump — port 80 traffic capture
tcpdump -i ens33 port 80 -v

# Open ports verify karna
ss -tulnp

# Local DNS entry
vi /etc/hosts
# 192.168.0.107 shashiserver.local

# Network path trace
traceroute google.com
mtr google.com
```

## Network Configuration
| Setting | Value |
|---------|-------|
| Interface | ens33 |
| Primary IP | 192.168.0.107/24 |
| Alias IP | 192.168.0.200/24 |
| Gateway | 192.168.0.1 |
| DNS | 8.8.8.8 |
| Active Zone | public |

## Open Ports Found
| Port | Protocol | Service |
|------|----------|---------|
| 22 | TCP | SSH |
| 25 | TCP | SMTP (localhost) |
| 631 | TCP | CUPS Printer (localhost) |
| 10050 | TCP | Zabbix Agent |
| 53 | TCP/UDP | DNS (virbr0) |

## Screenshots
<img width="1332" height="951" alt="Screenshot 2026-03-06 114844" src="https://github.com/user-attachments/assets/88777662-bdec-4ddd-a76e-8412004c129c" />
<img width="1326" height="956" alt="Screenshot 2026-03-06 114814" src="https://github.com/user-attachments/assets/c39b8ba1-5603-4ea2-83f9-c57387d6a902" />
<img width="1325" height="952" alt="Screenshot 2026-03-06 114749" src="https://github.com/user-attachments/assets/804c737e-acc2-408a-8ceb-89737d1a9e0e" />
<img width="1319" height="947" alt="Screenshot 2026-03-06 114713" src="https://github.com/user-attachments/assets/e2777aa1-512f-4699-8c03-377256eded3e" />


## Environment
- OS: CentOS 7
- Hypervisor: VMware Workstation
- Interface: ens33
