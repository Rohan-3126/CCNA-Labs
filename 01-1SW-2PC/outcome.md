## Verification

### VPCS1
**Ping PC2**

```text
PC1> ping 10.1.1.200

84 bytes from 10.1.1.200 icmp_seq=1 ttl=64 time=2.516 ms
84 bytes from 10.1.1.200 icmp_seq=2 ttl=64 time=1.590 ms
84 bytes from 10.1.1.200 icmp_seq=3 ttl=64 time=1.331 ms
84 bytes from 10.1.1.200 icmp_seq=4 ttl=64 time=2.065 ms
84 bytes from 10.1.1.200 icmp_seq=5 ttl=64 time=2.886 ms
```

---

### VPCS2
**Ping PC1**

```text
PC2> ping 10.1.1.100

84 bytes from 10.1.1.100 icmp_seq=1 ttl=64 time=4.710 ms
84 bytes from 10.1.1.100 icmp_seq=2 ttl=64 time=4.055 ms
84 bytes from 10.1.1.100 icmp_seq=3 ttl=64 time=4.252 ms
84 bytes from 10.1.1.100 icmp_seq=4 ttl=64 time=3.987 ms
84 bytes from 10.1.1.100 icmp_seq=5 ttl=64 time=3.382 ms
```

---

### Switch Verification

#### MAC Address Table

```text
SW1# show mac address-table

          Mac Address Table
-------------------------------------------

Vlan    Mac Address       Type       Ports
----    -----------       --------   -----
1       0050.7966.6800    DYNAMIC    Gi0/2
1       0050.7966.6801    DYNAMIC    Gi0/3

Total Mac Addresses for this criterion: 2
```

#### Interface Status

```text
SW1# show interfaces status

Port    Name    Status      Vlan    Duplex   Speed   Type
Gi0/0           notconnect  1       auto     auto    unknown
Gi0/1           notconnect  1       auto     auto    unknown
Gi0/2           connected   1       auto     auto    unknown
Gi0/3           connected   1       auto     auto    unknown
Gi1/0           notconnect  1       auto     auto    unknown
Gi1/1           notconnect  1       auto     auto    unknown
Gi1/2           notconnect  1       auto     auto    unknown
Gi1/3           notconnect  1       auto     auto    unknown
```

## Observations

- End-to-end connectivity between both hosts was successful.
- The switch dynamically learned both hosts' MAC addresses.
- No manual switch configuration was required.
- ARP resolution occurred before ICMP communication.
- Both active hosts appear in the MAC address table on their respective switch ports.
