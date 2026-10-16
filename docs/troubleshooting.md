# Troubleshooting Log

## Useful commands
```
show vlan brief
show interfaces status
show interfaces trunk
show run | section interface FastEthernet0/3
show ip route
show ip ospf neighbor
show ip interface brief
show port-security
```

## Issue 1 — Ports in the wrong VLAN / trunk
**Symptom:** hosts on `fa0/1-2` had no connectivity.
**Fix:** removed the stale access VLAN and set the uplinks as trunks.
```
interface range fa0/1-2
 no switchport access vlan
 switchport mode trunk
```

## Issue 2 — DHCP Relay not working (OPEN)
**Symptom:** ping from the DHCP server to the gateway/VLANs fails.
**Checked so far:** `ip helper-address 192.168.102.67` on all SVIs; router subinterface `Gi0/2.70` (192.168.102.65/28).
**Next things to check:**
- [ ] Is the server subnet (192.168.102.64/28) advertised in OSPF everywhere?
- [ ] Does the server's default gateway equal 192.168.102.65?
- [ ] Is VLAN 70 trunked/allowed on the link to the router, and is the parent interface `no shutdown`?
- [ ] Is there an overlap between SVI VLAN 70 (192.168.101.129/27) and the server VLAN 70 (192.168.102.64/28)?
- [ ] Does each DHCP pool have the right default gateway and a matching network?
