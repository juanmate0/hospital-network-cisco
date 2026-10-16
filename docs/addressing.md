# IP Addressing Plan

## Department VLANs

| VLAN | Site | Subnet | Mask | Gateway (SVI) |
|------|------|--------|------|---------------|
| 10 | HQ | 192.168.100.0 | /26 | 192.168.100.1 |
| 20 | HQ | 192.168.100.64 | /26 | 192.168.100.65 |
| 30 | HQ | 192.168.100.128 | /26 | 192.168.100.129 |
| 40 | HQ | 192.168.100.192 | /26 | 192.168.100.193 |
| 50 | HQ | 192.168.101.0 | /26 | 192.168.101.1 |
| 60 | HQ | 192.168.101.64 | /26 | 192.168.101.65 |
| 70 | Branch | 192.168.101.128 | /27 | 192.168.101.129 |
| 80 | Branch | 192.168.101.160 | /27 | 192.168.101.161 |
| 90 | Branch | 192.168.101.192 | /27 | 192.168.101.193 |
| 100 | Branch | 192.168.101.224 | /27 | 192.168.101.225 |
| 110 | Branch | 192.168.102.0 | /27 | 192.168.102.1 |
| 120 | Branch | 192.168.102.32 | /27 | 192.168.102.33 |

## Server room
| Network | Mask | Notes |
|---------|------|-------|
| 192.168.102.64 | /28 | Static IPs. Router gateway 192.168.102.65. DHCP server 192.168.102.67 |

## Point-to-point links (/30)

| Subnet | Link |
|--------|------|
| 192.168.102.80/30 | DI-MLS1 ↔ Left router |
| 192.168.102.84/30 | DI-MLS2 ↔ Left router |
| 192.168.102.88/30 | Left router ↔ Right router (serial) |
| 192.168.102.92/30 | DD-MLS1 ↔ Right router |
| 192.168.102.96/30 | DD-MLS2 ↔ Right router |

## WAN / ISP links (/30)

| Subnet | Link |
|--------|------|
| 195.136.17.0/30 | Left router ↔ ISP1 |
| 195.136.17.4/30 | Left router ↔ ISP2 |
| 195.136.17.8/30 | Right router ↔ ISP1 |
| 195.136.17.12/30 | Right router ↔ ISP2 |

## Default routes (ISP failover)

| Router | Primary | Backup (AD 70) |
|--------|---------|----------------|
| Left (HQ) | 195.136.17.2 (ISP1) | 195.136.17.6 (ISP2) |
| Right (Branch) | 195.136.17.14 (ISP2) | 195.136.17.10 (ISP1) |
