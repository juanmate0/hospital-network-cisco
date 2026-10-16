# Configuration Guide

Apply in this order. Every command block lives in [`/configs`](../configs).

1. **Base config** — hostname, console/enable passwords, banner, `no ip domain-lookup`,
   `service password-encryption` → `department-switches.txt`
2. **SSH** (routers + L3 switches) — domain name, local user, RSA key, `transport input ssh` → `multilayer-switches.txt`, `routers.txt`
3. **VLANs & trunks** → `multilayer-switches.txt`, `department-switches.txt`
4. **Routed ports + SVIs** → `multilayer-switches.txt`, `dhcp-relay-svis.txt`
5. **OSPF + default routes** → `ospf.txt`
6. **Port Security** → `port-security.txt`
7. **DHCP relay** → `dhcp-relay-svis.txt`

## Hardening notes
- Lab uses `enable password cisco`; production should use `enable secret` + strong passwords.
- RSA 1024 is a lab value; use 2048+ and `ip ssh version 2` in production.
- Recommended next step: `ip ssh version 2`, `login block-for`, and shutdown of unused ports.
