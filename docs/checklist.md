# Implementation Checklist

- [x] 1. Network design and layout (physical + logical) in Packet Tracer
- [x] 2. Base device config (hostnames, passwords, banners, no domain-lookup, SSH on routers/L3)
- [x] 3. VLANs, access ports, trunks
- [x] 4. Port Security (sticky MAC, shutdown violation)
- [x] 5. IP addressing (SVIs + router interfaces)
- [x] 6. OSPF on routers and multilayer switches
- [x] 7. Static IPs for DHCP, DNS, Web, Email servers
- [ ] 8. DHCP scopes per VLAN + `ip helper-address` — **not working yet**

## Pending
- [ ] 9. Wireless (APs/WLANs per department)
- [ ] 10. IPSec Site-to-Site VPN HQ↔Branch
- [ ] 11. Default static routes on ALL routers and MLS devices
- [ ] 12. PAT + extended ACLs
- [ ] 13. Final verification: inter-VLAN ping, VPN, DHCP leases, SSH, PAT/ACL behaviour
