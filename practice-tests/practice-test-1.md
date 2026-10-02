# Practice Test 1: CCNA 200-301 (v1.1) Exam Prep: Complete Course

- **Questions:** 46
- **Time limit:** 90 minutes
- **Passing score:** 70%%

> Answers are in `answer-key-1.md`. Track results in `score-tracker.md`.

---

**Q1.** A network engineer must create a subnet from 192.168.10.0/24 that supports exactly 30 usable host addresses with the least amount of wasted address space. Which subnet mask should be used?

A) 255.255.255.192 (/26)
B) 255.255.255.240 (/28)
C) 255.255.255.224 (/27)
D) 255.255.255.128 (/25)

---

**Q2.** Which IPv6 address range is automatically assigned to every IPv6-enabled interface, is used for on-link communication such as neighbor discovery, and is never routed beyond the local segment?

A) FF00::/8
B) FE80::/10
C) FC00::/7
D) 2000::/3

---

**Q3.** A company is deploying a real-time voice application where minimizing latency is critical and occasional dropped packets are acceptable since the human ear tolerates minor gaps. Which transport-layer protocol should the application use?

A) TCP
B) HTTP
C) UDP
D) ICMP

---

**Q4.** An engineer needs to connect two buildings on a campus that are 8 kilometers apart with a single network link. Which cabling option should be selected?

A) Cat6 UTP copper cable
B) Single-mode fiber
C) Multimode fiber (OM3)
D) RG-6 coaxial cable

---

**Q5.** When a Layer 2 switch receives a frame whose destination MAC address is not present in its MAC address table, what action does the switch take?

A) Drop the frame silently
B) Flood the frame out all ports except the ingress port
C) Send an ARP request to discover the MAC address
D) Forward the frame only to the default gateway

---

**Q6.** An engineer is deploying three access points in the 2.4 GHz band within range of each other and must avoid co-channel and adjacent-channel interference. Which set of channels should be configured on the APs?

A) Channels 1, 2, 3
B) Channels 3, 6, 9
C) Channels 2, 7, 12
D) Channels 1, 6, 11

---

**Q7.** A network engineer must subnet 192.168.10.0/24 using VLSM to create four subnets with these host requirements: Subnet A = 100 hosts, Subnet B = 50 hosts, Subnet C = 20 hosts, Subnet D = 10 hosts. Which subnet mask should be assigned to Subnet A to satisfy its requirement with the least wasted address space?

A) 255.255.255.128 (/25)
B) 255.255.255.192 (/26)
C) 255.255.255.0 (/24)
D) 255.255.255.224 (/27)

---

**Q8.** Which IPv6 address type is automatically assigned to every IPv6-enabled interface and is used exclusively for communication with other devices on the same physical or logical link, never being routed off that link?

A) Link-local address
B) Unique local address
C) Global unicast address
D) Multicast address

---

**Q9.** A company needs to connect two buildings located 8 kilometers apart and requires 10 Gbps of bandwidth between the sites. Which cabling type BEST meets this requirement?

A) Cat6a UTP copper cable
B) Single-mode fiber (OS2)
C) Multi-mode fiber (OM3)
D) Cat5e UTP copper cable

---

**Q10.** A switch port connects to a single end-user PC. The PC should belong only to VLAN 20 and should not receive any tagged frames. Which configuration is correct for this port?

A) switchport mode trunk; switchport trunk allowed vlan 20
B) switchport mode dynamic desirable; switchport access vlan 20
C) switchport mode access; switchport access vlan 20
D) switchport mode trunk; switchport trunk native vlan 20

---

**Q11.** Two switches are connected by an 802.1Q trunk. SW1 is configured with native VLAN 1 and SW2 with native VLAN 99. CDP reports a native VLAN mismatch, and untagged traffic intended for VLAN 1 is being delivered incorrectly. Which action resolves this issue?

A) Set both switches' native VLAN to the same value
B) Disable CDP on the trunk link
C) Add an allowed VLAN list that includes only the tagged VLANs
D) Change the trunk to access mode on both switches

---

**Q12.** Which statement correctly differentiates CDP and LLDP as used on Cisco switches?

A) CDP is an IEEE standard, while LLDP is Cisco proprietary
B) Both protocols are IEEE standards
C) CDP is Cisco proprietary, while LLDP (IEEE 802.1AB) is a vendor-neutral standard usable for multivendor discovery
D) LLDP works only on Cisco devices, while CDP is vendor neutral

---

**Q13.** You need to configure an EtherChannel between two switches using the IEEE-standard negotiation protocol, with both switch ports set to actively initiate negotiation. Which command should be applied on both ends of the link?

A) channel-group 1 mode on
B) channel-group 1 mode active
C) channel-group 1 mode auto
D) channel-group 1 mode desirable

---

**Q14.** Three switches run Rapid PVST+. SW1 currently has the lowest bridge ID and is root for all VLANs. The administrator wants SW2 to become the root bridge for VLAN 10 only, without affecting root bridge selection for any other VLAN. Which single configuration change best achieves this?

A) On SW1: spanning-tree vlan 10 priority 0
B) On SW1: shut down all trunk ports
C) On SW2: spanning-tree vlan 10 root primary
D) On SW2: spanning-tree portfast

---

**Q15.** A company is deploying a WLC-based wireless network and wants the strongest currently available WLAN security option that uses Simultaneous Authentication of Equals (SAE) and provides forward secrecy for client connections. Which security setting should be selected for the WLAN?

A) WEP
B) Open authentication with MAC filtering
C) WPA3-Personal (SAE)
D) WPA2-Personal (PSK)

---

**Q16.** A network engineer connects SW1 and SW2 with two links intended to form a single logical EtherChannel. SW1's interfaces are configured with 'channel-group 10 mode active'. SW2's interfaces are configured with 'channel-group 10 mode desirable'. The channel fails to form. Company policy requires that all future EtherChannels use the IEEE standard protocol for multivendor compatibility. Which change will allow this EtherChannel to form while meeting the company's policy?

A) Change SW2 interfaces to channel-group 10 mode auto
B) Change SW2 interfaces to channel-group 10 mode passive
C) Change SW1 interfaces to channel-group 10 mode desirable
D) Change SW1 interfaces to channel-group 10 mode on

---

**Q17.** Which command configures a Catalyst switch to become the root bridge for VLAN 10 by directly setting its bridge priority to the lowest usable numeric value?

A) spanning-tree vlan 10 root primary
B) spanning-tree vlan 10 priority 4096
C) spanning-tree bridge priority 0
D) spanning-tree vlan 10 priority 0

---

**Q18.** A university requires that each wireless user authenticate with unique corporate credentials against a centralized RADIUS server, and compliance rules mandate encryption stronger than WPA2 pre-shared key methods. Which WLAN security setting should be configured on the WLC?

A) WPA3-Enterprise (802.1X)
B) WPA2-Personal (PSK)
C) Open authentication with MAC filtering
D) WPA2-Enterprise (802.1X)

---

**Q19.** A router learns the following routes to reach destination network 172.16.10.0/24: an OSPF route with administrative distance 110 and metric 20, an EIGRP route with administrative distance 90 and metric 3072, and a static route with administrative distance 1 (no AD specified in the configuration). Which route is installed in the routing table?

A) The static route, because it has the lowest administrative distance
B) The OSPF route, because OSPF has the best metric calculation
C) The EIGRP route, because EIGRP metrics are more granular
D) All three routes, because the router load-balances across all available paths to the same destination

---

**Q20.** A router's routing table contains the following entries: 10.1.0.0/16 via 192.168.1.1, 10.1.1.0/24 via 192.168.2.1, and 10.0.0.0/8 via 192.168.3.1. A packet arrives destined for 10.1.1.50. Which next hop does the router use to forward the packet?

A) 192.168.1.1, because it is listed first in the routing table
B) 192.168.3.1, because the /8 summary route takes priority for aggregation
C) The router load-balances the packet across all three next hops since all three prefixes match the destination
D) 192.168.2.1, because it is the longest prefix match for the destination address

---

**Q21.** A network has a primary route to 172.20.0.0/24 learned via OSPF (administrative distance 110). An engineer wants to configure a floating static route to 172.20.0.0/24 via next hop 10.1.1.2 that is used ONLY as a backup if the OSPF route is lost. Which command correctly accomplishes this?

A) ip route 172.20.0.0 255.255.255.0 10.1.1.2
B) ip route 172.20.0.0 255.255.255.0 10.1.1.2 90
C) ip route 172.20.0.0 255.255.255.0 10.1.1.2 1
D) ip route 172.20.0.0 255.255.255.0 10.1.1.2 115

---

**Q22.** An administrator needs to configure a default route on an IPv6-enabled router, sending traffic out interface GigabitEthernet0/1 to next-hop address 2001:DB8::1. Which command is correct?

A) ip route 0.0.0.0 0.0.0.0 GigabitEthernet0/1 2001:DB8::1
B) ipv6 route ::/0 GigabitEthernet0/1 2001:DB8::1
C) ipv6 route 0.0.0.0/0 GigabitEthernet0/1 2001:DB8::1
D) route ipv6 ::/0 GigabitEthernet0/1 2001:DB8::1

---

**Q23.** Routers R1 and R2 are directly connected via a point-to-point serial link. R1's interface is configured for OSPF area 0, and R2's interface on the same link is configured for OSPF area 1. Both routers have matching hello and dead timers and matching subnet masks. What is the result of this configuration?

A) The routers do not form an OSPF neighbor relationship at all because the area ID on the shared link does not match
B) The routers form a full OSPF adjacency because the hello and dead timers match
C) The routers reach the 2-way neighbor state but never form a full adjacency because they cannot exchange LSAs across mismatched areas
D) The routers form an adjacency, and OSPF automatically performs route summarization between the two mismatched areas

---

**Q24.** Routers R1 and R2 are configured with HSRP for the 192.168.1.0/24 subnet, sharing virtual IP address 192.168.1.1. R1 is currently the active router and R2 is standby. All hosts on the subnet use 192.168.1.1 as their default gateway. R1 suddenly fails. What happens to host traffic leaving the subnet?

A) All hosts lose connectivity until their ARP cache entries time out and they discover R2's real IP address
B) Hosts must be manually reconfigured with R2's physical IP address as their new default gateway
C) R2 detects R1's failure, transitions to the active role, and begins forwarding traffic using the same virtual IP and virtual MAC address, so hosts experience minimal disruption
D) HSRP requires an underlying routing protocol such as OSPF to trigger failover, so traffic is dropped until OSPF reconverges

---

**Q25.** R1 learns 10.10.20.0/24 via EIGRP (AD 90) through its primary WAN link. A network engineer wants to configure a backup route to the same network through a secondary ISP link that is used ONLY if the EIGRP route disappears from the routing table. Which static route configuration achieves this?

A) ip route 10.10.20.0 255.255.255.0 192.168.1.2
B) ip route 10.10.20.0 255.255.255.0 192.168.1.2 90
C) ip route 10.10.20.0 255.255.255.0 192.168.1.2 95
D) ip route 0.0.0.0 0.0.0.0 192.168.1.2

---

**Q26.** R2 has multiple loopback interfaces and several active physical interfaces with varying IP addresses. The engineer wants R2's OSPF Router ID to be deterministic and unaffected by interface flaps or the addition/removal of loopbacks in the future. Which configuration guarantees this outcome?

A) Configure a loopback interface with the highest IP address among all interfaces on R2
B) Do nothing and let OSPF auto-select the highest IP address among active physical interfaces
C) Reload the router after all interfaces are configured so OSPF recalculates the ID
D) Manually configure the router-id command under the OSPF process

---

**Q27.** A branch office LAN has two routers, R1 and R2, both connected to the same VLAN and both capable of routing to the internet. Hosts on the LAN are statically configured with a single default gateway IP address. The network administrator needs traffic to automatically fail over to R2 if R1 goes down, without any reconfiguration on the end-host devices. Which technology should be implemented?

A) OSPF
B) Spanning Tree Protocol (STP)
C) HSRP
D) DHCP

---

**Q28.** A network engineer needs to send all traffic destined for a single specific server at 192.168.5.10 out a different next hop than the rest of the 192.168.5.0/24 subnet, which uses a different default gateway for all other hosts. Which type of static route should be configured to accomplish this without affecting the rest of the subnet?

A) ip route 192.168.5.10 255.255.255.255 [next-hop]
B) ip route 192.168.5.0 255.255.255.0 [next-hop]
C) ip route 0.0.0.0 0.0.0.0 [next-hop]
D) A floating static route with an increased administrative distance for 192.168.5.0/24

---

**Q29.** An engineer runs 'passive-interface GigabitEthernet0/1' under 'router ospf 1' on R1. What is the resulting effect on GigabitEthernet0/1?

A) The interface is removed from the OSPF process entirely and no longer participates in IP routing
B) The interface becomes a stub network that requires manual redistribution to be reachable
C) The interface's connected network is no longer advertised in OSPF LSAs
D) The interface stops sending and receiving OSPF Hello packets, preventing neighbor adjacencies, while its connected network is still advertised in OSPF

---

**Q30.** A network administrator needs internal hosts on 10.1.1.0/24 to access the internet using a single public IP address, 203.0.113.5, which is already assigned to the router's outside interface. Which configuration BEST meets this requirement?

A) ip nat inside source static 10.1.1.0 203.0.113.5
B) ip nat inside source list 1 interface GigabitEthernet0/1 overload
C) ip nat inside source list 1 pool PUBLICPOOL overload
D) ip nat outside source list 1 interface GigabitEthernet0/1 overload

---

**Q31.** Which statement accurately describes NTP stratum levels as tested on the CCNA exam?

A) Higher stratum numbers indicate closer proximity to the authoritative time source
B) Stratum 0 servers are the devices most commonly used for client synchronization directly over the network
C) Stratum 1 servers are directly connected to an authoritative time source such as a GPS or atomic clock, and the stratum number increases by 1 for each additional hop away from that source
D) Stratum level has no effect on which time source a client selects when multiple NTP servers are available

---

**Q32.** A router connects VLAN 10 (clients) and VLAN 20, which contains a DHCP server at 192.168.20.10. Clients on VLAN 10 are not receiving IP addresses via DHCP. Which single configuration, applied on the VLAN 10 SVI, resolves this issue?

A) ip dhcp relay 192.168.20.10
B) ip dhcp pool 192.168.20.10
C) ip forward-protocol udp 67
D) ip helper-address 192.168.20.10

---

**Q33.** Which syslog severity level number corresponds to 'Alert' messages, indicating a condition requiring immediate action?

A) 3
B) 0
C) 2
D) 1

---

**Q34.** A service provider needs to enforce a contracted bandwidth rate on an ingress interface by immediately dropping or remarking traffic that exceeds the rate, without buffering the excess packets. Which QoS mechanism should be applied?

A) Traffic policing
B) Traffic shaping
C) Weighted fair queuing (WFQ)
D) Weighted random early detection (WRED)

---

**Q35.** A network engineer configures port security on an access-layer switch port. The requirement states: when an unauthorized MAC address is detected, the offending frames must be dropped, a syslog/SNMP notification must be generated, and the port must remain in a forwarding (up) state. Which port security violation mode satisfies this requirement?

A) shutdown
B) protect
C) sticky
D) restrict

---

**Q36.** An attacker connects an unauthorized DHCP server to an access switch port and begins issuing rogue IP configurations, including a malicious default gateway, to clients on the VLAN. Which security feature should be enabled on the switch to prevent this specific attack?

A) DHCP snooping
B) Port security
C) Dynamic ARP Inspection (DAI)
D) 802.1X

---

**Q37.** A company needs an ACL that denies only Telnet traffic sourced from host 10.1.1.10 destined to server 10.1.1.100, while permitting all other traffic. Which pair of ACL statements correctly implements this?

A) access-list 101 deny tcp host 10.1.1.100 host 10.1.1.10 eq 23 / access-list 101 permit ip any any
B) access-list 101 deny tcp host 10.1.1.10 host 10.1.1.100 eq 21 / access-list 101 permit ip any any
C) access-list 101 deny tcp any host 10.1.1.100 eq 23 / access-list 101 permit ip any any
D) access-list 101 deny tcp host 10.1.1.10 host 10.1.1.100 eq 23 / access-list 101 permit ip any any

---

**Q38.** An administrator wants to prevent a malicious host on the LAN from sending forged ARP replies that map the default gateway's IP address to the attacker's own MAC address, enabling a man-in-the-middle attack. Which feature directly addresses this threat?

A) DHCP snooping
B) Dynamic ARP Inspection (DAI)
C) Port security
D) Standard ACL

---

**Q39.** Which statement correctly differentiates WPA3-Personal from WPA2-Personal?

A) WPA3-Personal requires an external RADIUS server for authentication, while WPA2-Personal does not require any backend server
B) WPA3-Personal uses SAE (Simultaneous Authentication of Equals) to resist offline dictionary attacks, while WPA2-Personal relies on a PSK-based four-way handshake that is vulnerable to offline password-guessing attacks
C) WPA3-Personal uses TKIP encryption for backward compatibility, while WPA2-Personal uses AES encryption exclusively
D) WPA3-Personal and WPA2-Personal are functionally identical; the only change in WPA3 is the method used to broadcast the SSID

---

**Q40.** A company wants centralized authentication for administrators logging into network devices, with the ability to authorize specific commands on a per-user basis, and full encryption of the entire authentication packet (not just the password). Which AAA protocol should be selected?

A) RADIUS
B) Kerberos
C) 802.1X
D) TACACS+

---

**Q41.** A switch port connects to an untrusted access-layer segment where end users plug in laptops. The network administrator wants to prevent rogue DHCP servers from being connected to this segment and handing out incorrect IP configurations to clients. Which feature should be configured on the switch to BEST meet this requirement?

A) Dynamic ARP Inspection on the port
B) Port security with a maximum of one MAC address
C) DHCP snooping with the port configured as untrusted
D) Standard ACL applied inbound on the port

---

**Q42.** A network engineer manages 200 switches individually via SSH and CLI, making configuration changes one device at a time, which is time consuming and error-prone. The engineer wants to push consistent VLAN configurations to all switches simultaneously from a single management platform. Which approach BEST meets this requirement?

A) Deploy Cisco DNA Center to manage devices via a controller-based architecture
B) Write a Python script to SSH into each switch and push CLI commands sequentially
C) Use SNMPv2 polling to monitor VLAN status on each switch
D) Configure each switch with local SPAN sessions

---

**Q43.** A REST API returns the following JSON data:
{
  "interface": {
    "name": "GigabitEthernet0/1",
    "status": "up",
    "vlans": [10, 20, 30]
  }
}
Which statement about this JSON data is correct?

A) "vlans" is a JSON object containing three key-value pairs
B) "vlans" is a JSON array containing three numeric values
C) "interface" is a JSON array containing three elements
D) "status" is a JSON array with a single string value

---

**Q44.** An engineer is writing a script that uses a REST API to create a new VLAN entry on a network controller. Which HTTP verb should the script send along with the new VLAN configuration data?

A) POST
B) GET
C) DELETE
D) PUT

---

**Q45.** Which of the following correctly represents valid JSON syntax for an object with a key named 'hostname' and a value of 'Router1'?

A) {"hostname": "Router1"}
B) {hostname: Router1}
C) ["hostname", "Router1"]
D) <hostname>Router1</hostname>

---

**Q46.** In a Cisco SD-Access fabric architecture, which statement correctly describes the relationship between the underlay and overlay networks?

A) The overlay is the physical network providing IP connectivity, while the underlay is the virtual network built on top using tunneling
B) The underlay is the physical network providing IP connectivity, while the overlay is the virtual network built on top using tunneling protocols such as VXLAN
C) The underlay and overlay are identical layers used interchangeably to describe the same fabric role
D) The underlay only exists in traditional networks and is not part of controller-based architectures

---

