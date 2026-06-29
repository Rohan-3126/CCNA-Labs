========================================
Verification
========================================

#VPCS1

ping 192.168.1.20

Result:
Successful replies received.

PC1> ping 10.1.1.200

84 bytes from 10.1.1.200 icmp_seq=1 ttl=64 time=2.516 ms
84 bytes from 10.1.1.200 icmp_seq=2 ttl=64 time=1.590 ms
84 bytes from 10.1.1.200 icmp_seq=3 ttl=64 time=1.331 ms
84 bytes from 10.1.1.200 icmp_seq=4 ttl=64 time=2.065 ms
84 bytes from 10.1.1.200 icmp_seq=5 ttl=64 time=2.886 ms


----------------------------------------

#VPCS2

ping 192.168.1.10

Result:
Successful replies received.

PC2> ping 10.1.1.100

84 bytes from 10.1.1.100 icmp_seq=1 ttl=64 time=4.710 ms
84 bytes from 10.1.1.100 icmp_seq=2 ttl=64 time=4.055 ms
84 bytes from 10.1.1.100 icmp_seq=3 ttl=64 time=4.252 ms
84 bytes from 10.1.1.100 icmp_seq=4 ttl=64 time=3.987 ms
84 bytes from 10.1.1.100 icmp_seq=5 ttl=64 time=3.382 ms


----------------------------------------

#SW1

SW1>enable
SW1#
SW1#
SW1#show mac address 
SW1#show mac address-table 
          Mac Address Table

Vlan    Mac Address       Type        Ports
----    -----------       --------    -----
   1    0050.7966.6800    DYNAMIC     Gi0/2
   1    0050.7966.6801    DYNAMIC     Gi0/3
Total Mac Addresses for this criterion: 2
SW1#
SW1#
SW1#show interfaces status

Port      Name               Status       Vlan       Duplex  Speed Type 
Gi0/0                        notconnect   1            auto   auto unknown
Gi0/1                        notconnect   1            auto   auto unknown
Gi0/2                        connected    1            auto   auto unknown
Gi0/3                        connected    1            auto   auto unknown
Gi1/0                        notconnect   1            auto   auto unknown
Gi1/1                        notconnect   1            auto   auto unknown
Gi1/2                        notconnect   1            auto   auto unknown
Gi1/3                        notconnect   1            auto   auto unknown


========================================
Observations
========================================

- Both VPCS hosts communicated successfully.
- The switch dynamically learned the MAC addresses of both hosts.
- No manual switch configuration was required.
- ARP resolution occurred before ICMP communication.

