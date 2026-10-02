# Practice Test 2: CCNA 200-301 (v1.1) Exam Prep: Complete Course

- **Questions:** 46
- **Time limit:** 90 minutes
- **Passing score:** 70%%

> Answers are in `answer-key-2.md`. Track results in `score-tracker.md`.

---

**Q1.** A network engineer is subnetting 192.168.20.0/24 using VLSM to support four LANs: Sales (100 hosts), Engineering (50 hosts), Guest (20 hosts), and a point-to-point WAN link (2 hosts). Which subnet mask should be assigned to the Engineering LAN to support exactly 50 hosts while minimizing wasted address space?

A) 255.255.255.224 (/27) — supports only 30 usable hosts, insufficient for 50
B) 255.255.255.192 (/26) — supports 62 usable hosts, closest efficient fit for 50 hosts
C) 255.255.255.0 (/24) — wastes over 200 addresses on a 50-host segment
D) 255.255.255.128 (/25) — supports 126 usable hosts, wastes 76 addresses

---

**Q2.** A technician examines a Windows host's IPv6 configuration and finds the address FE80::A1B2:3C4D:5E6F:7A8B assigned to the network adapter with no default gateway populated for it. What best describes this address and its scope?

A) Unique local address, used for routing within a private organization across multiple sites
B) Global unicast address, routable across the public internet
C) Link-local address, automatically generated, valid only on the local link and non-routable
D) Multicast address identifying a group of all IPv6 nodes on the segment

---

**Q3.** An engineer is planning a 2.4 GHz wireless deployment with three access points placed to minimize co-channel interference. Which set of channels should be configured on the APs?

A) 1, 6, 11
B) 2, 7, 12
C) 3, 8, 13
D) 1, 5, 9

---

**Q4.** A company is deploying a VoIP solution and needs to select the transport protocol for the real-time voice media stream (RTP), where minimizing latency is more important than guaranteeing delivery of every packet. Which characteristic makes the correct protocol the right choice for this traffic?

A) TCP, because its three-way handshake guarantees the call setup is reliable before voice data flows
B) TCP, because its sliding window and acknowledgments ensure no voice packets are ever lost
C) UDP, because it has no connection establishment or retransmission overhead, minimizing latency for time-sensitive media
D) UDP, because it guarantees in-order delivery of every voice packet

---

**Q5.** A data center architect needs a fabric where any two servers experience the same number of hops and predictable, low latency regardless of which leaf switches they attach to. Which topology BEST meets this requirement?

A) Three-tier core-distribution-access hierarchy
B) Hub-and-spoke WAN topology
C) Collapsed two-tier core/access topology
D) Spine-leaf (Clos) topology with every leaf connected to every spine

---

**Q6.** A service provider router hosts routing tables for multiple customers on the same physical device and must keep each customer's routes completely isolated from one another, even if customers use overlapping private IP address ranges. Which virtualization technology should be implemented on the router?

A) VLAN
B) Virtual machine
C) Container
D) VRF (Virtual Routing and Forwarding)

---

**Q7.** A network engineer must subnet 192.168.10.0/24 using VLSM to create four subnets with these host requirements: Subnet A = 50 hosts, Subnet B = 25 hosts, Subnet C = 12 hosts, Subnet D = 2 hosts (point-to-point WAN link). Following VLSM best practices (allocate the largest requirement first, using the smallest mask that satisfies it), which subnet mask should be assigned to Subnet A?

A) /25
B) /27
C) /26
D) /24

---

**Q8.** An engineer reviews four IPv6 addresses configured on lab devices and must identify the Unique Local Address (ULA). Which address below is a valid ULA?

A) 2001:DB8:ACAD:1::1
B) FE80::1
C) FDA1:2B3C:4D5E:0001::1
D) FF02::1

---

**Q9.** A company needs to connect switches in two buildings located 2 km apart and requires a 10 Gbps link between them. Which cabling and transceiver solution BEST meets this requirement?

A) Cat6a UTP copper cabling
B) Multimode fiber (OM3) with 10GBASE-SR transceivers
C) Single-mode fiber with 10GBASE-LR transceivers
D) Coaxial RG-6 cable

---

**Q10.** Two switches, SW1 and SW2, are connected via a single trunk link running 802.1Q. SW1's trunk interface is configured with the native VLAN set to 1 (default), while SW2's trunk interface has been configured with native VLAN 99. Console logs on both switches show recurring CDP native VLAN mismatch warnings, and untagged traffic destined for VLAN 1 is unexpectedly appearing in VLAN 99 on SW2. What must be done to correctly resolve this issue?

A) Disable CDP on both trunk interfaces to suppress the mismatch warnings
B) Change SW2's native VLAN to VLAN 1 so it matches SW1's native VLAN configuration
C) Reconfigure the trunk encapsulation to ISL on both switches
D) Convert the link from a trunk port to an access port assigned to VLAN 99

---

**Q11.** You are bundling four physical links between SW1 and SW2 into a single logical interface. On SW1, all four interfaces are configured with 'channel-group 1 mode active'. Which configuration on SW2's corresponding four interfaces will successfully form the EtherChannel using LACP?

A) channel-group 1 mode active or channel-group 1 mode passive on all four interfaces
B) channel-group 1 mode auto on all four interfaces
C) channel-group 1 mode desirable on all four interfaces
D) channel-group 1 mode on for all four interfaces

---

**Q12.** Three switches participate in Rapid PVST+ for VLAN 10: SW1 has bridge priority 32768, SW2 has bridge priority 24576, and SW3 has bridge priority 32768 with a lower MAC address than SW1. Which switch becomes the root bridge for VLAN 10?

A) SW2, because it has the lowest bridge priority value
B) SW3, because when priorities tie the switch with the lowest MAC address wins
C) SW1, because it is the first switch listed in the topology
D) The switch with the highest configured port priority on its lowest-numbered port

---

**Q13.** An access switchport connects to a user's PC. The PC is frequently powered on and off, and each time this happens the switch generates a topology change notification (TCN) that triggers unnecessary STP recalculation across the network. The administrator also wants to guarantee that if someone accidentally connects a switch to this port instead of a PC, the port is automatically disabled. Which configuration should be applied to this port?

A) Configure both PortFast and BPDU Guard together
B) Configure BPDU Guard only
C) Configure PortFast only
D) Configure Root Guard on the port

---

**Q14.** A network engineer is comparing Layer 2 discovery protocols supported on Cisco switches for a mixed-vendor environment that includes some non-Cisco devices. Which statement correctly describes the two protocols?

A) CDP is an IEEE standard supported by all vendors, while LLDP is Cisco-proprietary and only works between Cisco devices
B) LLDP is defined by IEEE 802.1AB and is vendor-neutral, while CDP is a Cisco-proprietary protocol supported only on Cisco equipment
C) Both CDP and LLDP require an IP address to be configured on the interface before neighbor information can be exchanged
D) CDP and LLDP both operate over TCP port 179 to exchange neighbor advertisements

---

**Q15.** An administrator needs to log into a Cisco Wireless LAN Controller's HTTPS-based web GUI from a laptop located on a management subnet that is different from the subnets used by the lightweight access points and wireless clients. Which WLC interface handles this type of administrative access, such as SSH, HTTPS, and SNMP traffic to the controller itself?

A) The dynamic interface mapped to the client VLAN
B) The management interface, which handles administrative traffic to the controller
C) The virtual interface used for mobility and web authentication redirection
D) The AP-manager interface used to terminate CAPWAP tunnels from access points

---

**Q16.** SW1 and SW2 are connected by a single physical link intended to become an EtherChannel. SW1 is configured with 'channel-group 5 mode passive' and SW2 is also configured with 'channel-group 5 mode passive'. 'show etherchannel summary' shows the port in an independent (I) state on both switches and no Po5 interface forms. What change will allow the EtherChannel to form using LACP?

A) Change both switches to 'channel-group 5 mode on' to force the channel up
B) Change SW1 to 'channel-group 5 mode active', leaving SW2 as passive
C) Disable spanning-tree PortFast on both physical interfaces before enabling the channel
D) Change both switches to 'channel-group 5 mode auto' since that is the LACP negotiation keyword

---

**Q17.** Four switches participate in Rapid PVST+ for VLAN 10:
SW1: priority 4096, MAC 0011.1111.1111
SW2: priority 4096, MAC 0022.2222.2222
SW3: priority 8192, MAC 0000.0000.0001
SW4: priority 32768 (default), MAC 0000.0000.0000
Which switch becomes the root bridge for VLAN 10?

A) SW1, because it has the lowest bridge priority and, among priority ties, the lowest MAC address
B) SW3, because it has the lowest MAC address among all four switches
C) SW4, because it has the lowest numeric priority value once extended system ID is applied
D) SW2, because ties in priority are broken by the highest MAC address

---

**Q18.** A lightweight access point is configured to join a wireless LAN controller (WLC) using CAPWAP. Which UDP port does the AP use to establish the CAPWAP control channel to the WLC?

A) UDP 4172
B) UDP 2246
C) UDP 5246
D) UDP 5247

---

**Q19.** A router's IPv4 routing table contains the following entries for a packet destined to 192.168.1.140:
- 192.168.1.0/24 via R1 (OSPF, AD 110)
- 192.168.1.128/25 via R2 (static, AD 1)
- 192.168.1.128/26 via R3 (RIP, AD 120)
- 0.0.0.0/0 via R4 (default route)

Which route does the router actually use to forward this packet?

A) The default route via R4, because it is always the gateway of last resort
B) The route via R2 (192.168.1.128/25), because static routes have the lowest administrative distance
C) The route via R1 (192.168.1.0/24), because OSPF is preferred over RIP
D) The route via R3 (192.168.1.128/26), because it has the longest prefix match

---

**Q20.** A router learns 172.16.20.0/24 from three sources simultaneously: a static route (AD 1), an OSPF route (AD 110), and a RIP route (AD 120). All three advertise the identical prefix and mask. Which route is installed in the routing table?

A) The RIP route, because hop count is the simplest and most reliable metric
B) The OSPF route, because it is a link-state protocol with full topology awareness
C) The static route, because it has the lowest administrative distance
D) All three routes are installed and traffic is load-balanced across them

---

**Q21.** A network has a primary route to 10.1.1.0/24 learned dynamically via OSPF (AD 110). An administrator wants to configure a floating static route out of Serial0/0/1 that only becomes active if the OSPF route disappears. Which command correctly accomplishes this?

A) ip route 10.1.1.0 255.255.255.0 Serial0/0/1 90
B) ip route 10.1.1.0 255.255.255.0 Serial0/0/1 1
C) ip route 10.1.1.0 255.255.255.0 Serial0/0/1 130
D) ip route 10.1.1.0 255.255.255.0 Serial0/0/1

---

**Q22.** You need to configure an IPv6 static route to 2001:db8:acad:2::/64 that points out interface GigabitEthernet0/1 using the next-hop link-local address fe80::2. Which command is syntactically correct and functional?

A) ipv6 route 2001:db8:acad:2::/64 GigabitEthernet0/1 fe80::2
B) ipv6 route 2001:db8:acad:2::/64 fe80::2
C) ipv6 route 2001:db8:acad:2::/64 GigabitEthernet0/1
D) ipv6 route fe80::2 2001:db8:acad:2::/64 GigabitEthernet0/1

---

**Q23.** Router R1 has Gi0/0 connected to a LAN of hosts and Gi0/1 connected via a WAN link to R2; both interfaces run OSPF. The administrator configures 'passive-interface GigabitEthernet0/0' under 'router ospf 1'. What is the resulting behavior?

A) Gi0/0 is entirely removed from the OSPF process, and its connected network is no longer advertised at all
B) Gi0/0 stops forwarding IP traffic to and from the LAN hosts
C) Gi0/0's connected network is still advertised in OSPF, but R1 stops sending and receiving OSPF hello packets on Gi0/0, so no neighbor adjacency can form there
D) OSPF hellos stop on Gi0/1 as well, because passive-interface applies to all non-designated interfaces by default

---

**Q24.** R1 (HSRP priority 150, preempt enabled) and R2 (HSRP priority 100, default preempt disabled) are configured in HSRP group 5 sharing virtual IP 10.1.1.1. R1 fails and R2 becomes the active router. After R1 recovers and comes back online, what happens?

A) R1 does not reclaim the active role, because once an HSRP active router changes, the change is permanent
B) R2 remains active permanently because preemption only applies during the very first election
C) Both R1 and R2 become active simultaneously, causing a duplicate virtual IP conflict
D) R1 immediately reclaims the active role because it has a higher priority and preempt is enabled on R1

---

**Q25.** A router receives routing information for network 192.168.1.0/24 from two sources: OSPF advertises the route with a metric of 20, and EIGRP advertises the same network with a metric of 28160. Both protocols are running with their default administrative distances. Which route is installed in the routing table?

A) The OSPF route, because OSPF has a lower metric value
B) The EIGRP route, because EIGRP has a lower administrative distance than OSPF
C) Both routes are installed and load-balanced equally
D) The router selects the route based on which protocol converged first

---

**Q26.** A network administrator wants to configure a backup default route that will only be used if the primary default route learned via OSPF (default AD 110) becomes unavailable. The backup next-hop address is 209.165.200.1. Which command correctly configures this as a floating static route?

A) ip route 0.0.0.0 0.0.0.0 209.165.200.1 90
B) ip route 0.0.0.0 0.0.0.0 209.165.200.1 130
C) ip route 0.0.0.0 0.0.0.0 209.165.200.1 1
D) ip default-gateway 209.165.200.1

---

**Q27.** A router's routing table contains the following routes, learned from different sources with varying administrative distances:
10.0.0.0/8 via EIGRP, AD 90
10.1.1.0/24 via RIP, AD 120
10.1.0.0/16 via OSPF, AD 110
A packet arrives destined for 10.1.1.5. Which route does the router use to forward this packet?

A) The 10.0.0.0/8 route, because EIGRP has the lowest administrative distance
B) The 10.1.0.0/16 route, because OSPF is preferred over RIP
C) The router load balances the packet across all three matching routes
D) The 10.1.1.0/24 route, because it is the most specific matching prefix

---

**Q28.** Router R1 has the following interfaces, all in the 'up/up' state, with OSPF enabled system-wide and no router-id manually configured:
Loopback0: 1.1.1.1/32
GigabitEthernet0/0: 10.0.0.1/24
GigabitEthernet0/1: 10.0.0.2/24
When the OSPF process starts on R1, which IP address becomes its OSPF router ID?

A) 1.1.1.1, because loopback interfaces always take priority over physical interfaces during router-id selection
B) 10.0.0.2, because it is the highest IP address among all interfaces
C) 10.0.0.1, because it is the first interface configured
D) 0.0.0.0, because a router-id must be manually configured for OSPF to function

---

**Q29.** Which statement accurately describes default HSRP (Hot Standby Router Protocol) behavior on Cisco routers?

A) The default HSRP priority is 0, and preemption is enabled by default so the highest-priority router always becomes active immediately
B) HSRP uses a single shared virtual MAC address defined by the IEEE 802.1Q standard, identical to the one used by VRRP
C) HSRP requires a minimum of three routers in a group to establish an active/standby relationship
D) The default HSRP priority is 100, and a router will not automatically resume the active role after recovering from a failure unless preemption is explicitly configured

---

**Q30.** A network administrator has 50 internal hosts that need internet access, but the ISP has allocated only 4 public IP addresses (203.0.113.1-203.0.113.4). Access list 1 already matches the internal 10.0.0.0/24 network. Which NAT configuration correctly meets this requirement?

A) ip nat pool NATPOOL 203.0.113.1 203.0.113.4 netmask 255.255.255.252 followed by ip nat inside source list 1 pool NATPOOL (no overload)
B) ip nat inside source static 10.0.0.0 203.0.113.1
C) ip nat outside source list 1 pool NATPOOL overload
D) ip nat pool NATPOOL 203.0.113.1 203.0.113.4 netmask 255.255.255.252 followed by ip nat inside source list 1 pool NATPOOL overload

---

**Q31.** A router is configured with 'ntp server 192.168.1.1' and that server currently reports stratum 2. Several downstream switches synchronize their clocks to this router. What stratum value will those downstream switches report?

A) Stratum 1
B) Stratum 2
C) Stratum 0
D) Stratum 3

---

**Q32.** Clients on VLAN 20 are not receiving IP addresses from a DHCP server located on VLAN 10. The router serving as the VLAN 20 default gateway shows zero DHCP relay statistics incrementing on that interface. Which command is missing on the VLAN 20 SVI?

A) ip dhcp relay information option
B) ip helper-address <DHCP server IP>
C) ip forward-protocol udp 67
D) service dhcp

---

**Q33.** An administrator wants a router to send only Emergency, Alert, Critical, and Error messages to the syslog server, suppressing Warning and all less severe messages. Which command accomplishes this?

A) logging trap errors
B) logging trap warnings
C) logging trap debugging
D) logging trap notifications

---

**Q34.** A service provider needs to strictly enforce a contracted bandwidth limit on a customer's egress interface. Any traffic exceeding the rate must be dropped immediately rather than buffered or delayed. Which QoS mechanism satisfies this requirement?

A) Weighted fair queuing
B) Low latency queuing (LLQ)
C) Traffic shaping with a shaping queue
D) Traffic policing

---

**Q35.** A company wants to prevent rogue DHCP servers from handing out addresses on the access layer and also prevent attackers from poisoning the ARP cache of hosts in the same VLAN. Which combination of switch features and trust configuration correctly addresses both requirements?

A) Enable DHCP snooping and Dynamic ARP Inspection; configure the uplink port to the DHCP server as trusted, leave access ports untrusted
B) Enable Dynamic ARP Inspection only; trust all VLAN interfaces
C) Enable DHCP snooping only; configure all access ports as trusted
D) Enable port security on all ports; trust the uplink port to the DHCP server

---

**Q36.** A switch port is configured with 'switchport port-security maximum 1', 'switchport port-security violation restrict', and 'switchport port-security mac-address sticky'. The port learns MAC AAAA.AAAA.AAAA from the first connected PC. Later, a different device with a new MAC address is connected to the same port while the original device is still active. What happens?

A) The port drops packets from the new device, logs a violation, but the port stays up and the original device continues to be allowed
B) The interface converts the sticky MAC to a dynamic entry and relearns the new address
C) SNMP trap is sent and the port is placed into err-disabled state after 3 violations
D) The port shuts down err-disabled and must be manually re-enabled

---

**Q37.** A network admin needs junior engineers to be limited to 'show' commands on routers while senior engineers retain full 'configure terminal' access, along with detailed per-command accounting logs for auditing. Which Cisco AAA protocol choice best meets this requirement?

A) RADIUS, because it combines authentication and authorization in one packet
B) 802.1X, because it authenticates devices before granting network access
C) TACACS+, because it separates authentication, authorization, and accounting and supports command-level authorization
D) Kerberos, because it provides ticket-based authentication for CLI access

---

**Q38.** A company needs to block only host 10.10.20.55 from reaching the web server 172.16.5.10 on any protocol/port, while allowing that host and all other hosts to reach every other destination normally. Which ACL configuration and placement correctly achieves this?

A) access-list 101 deny tcp 10.10.20.0 0.0.0.255 host 172.16.5.10 eq 80 followed by permit ip any any, applied outbound on the router interface connected to the server
B) access-list 101 deny ip host 10.10.20.55 host 172.16.5.10 followed by permit ip any any, applied inbound on the router interface closest to 10.10.20.55
C) access-list 1 deny host 10.10.20.55 followed by permit any, applied inbound on the interface closest to the server
D) access-list 101 deny ip host 10.10.20.55 host 172.16.5.10 with no additional permit statement, applied outbound on the interface closest to the source

---

**Q39.** Which statement accurately differentiates WPA2-Personal from WPA3-Personal?

A) WPA3-Personal uses Simultaneous Authentication of Equals (SAE) to resist offline dictionary attacks, while WPA2-Personal uses a 4-way handshake with PSK vulnerable to offline capture
B) WPA2-Personal requires 802.1X authentication with a RADIUS server, whereas WPA3-Personal only supports PSK
C) WPA3-Personal disables encryption entirely for guest network compatibility
D) WPA2-Personal uses AES-256 exclusively, while WPA3-Personal uses AES-128 for backward compatibility

---

**Q40.** A company connects two branch offices over the internet and needs all inter-site traffic encrypted while also allowing OSPF to form a dynamic routing adjacency between the two branch routers. Which solution meets both requirements?

A) A GRE tunnel alone between the two branch routers
B) Site-to-site SSL VPN using a web browser client on each router
C) Standard IPsec tunnel mode using ESP for the site-to-site connection
D) A GRE tunnel encapsulated inside an IPsec tunnel (GRE over IPsec)

---

**Q41.** A switch runs both DHCP snooping and Dynamic ARP Inspection (DAI), with all access ports configured as untrusted for both features. A printer on port Gi1/0/8 has a manually configured static IP address. After DAI is enabled, the printer immediately loses network connectivity, while all DHCP client PCs on other access ports continue to work normally. What is the MOST likely cause of the printer's connectivity loss?

A) The port's DAI ARP rate limit was exceeded, causing the switch to err-disable the port
B) Port security detected a MAC address violation on Gi1/0/8 and shut down the port
C) The uplink port to the DHCP server is not trusted for DHCP snooping, so the printer cannot renew its lease
D) DAI validates ARP packets against the DHCP snooping binding table, and since the printer's IP was statically assigned it has no binding entry, so its ARP traffic is dropped

---

**Q42.** A network team needs to push initial configuration to 500 newly racked switches over SSH, from a central server, without installing any agent software on the switches themselves and without requiring the switches to periodically check in for updates. Which automation tool BEST fits this push-based, agentless requirement?

A) Puppet
B) Ansible
C) Chef
D) Manual CLI scripting via a terminal server

---

**Q43.** A network engineer is using a REST API on Cisco DNA Center to update ONLY the VLAN name on an existing interface object, leaving all other interface properties unchanged. Which HTTP method is the MOST appropriate for this partial update?

A) PUT
B) POST
C) PATCH
D) GET

---

**Q44.** In a Cisco DNA Center controller-based architecture, third-party orchestration software needs to programmatically request the deployment of a new network policy. Through which interface does this external application communicate with the controller?

A) Southbound API (e.g., NETCONF/OpenFlow to devices)
B) Northbound API
C) Device console/CLI
D) SNMP trap listener on the switch

---

**Q45.** Given the following JSON returned by a device inventory API:
{
  "hostname": "R1",
  "interfaces": ["Gig0/0", "Gig0/1"],
  "management": {
    "ip": "10.1.1.1",
    "enabled": true
  },
  "port_count": 24
}
What JSON data type is the value associated with the key "management"?

A) Object
B) String
C) Boolean
D) Array

---

**Q46.** In controller-based network architectures such as Cisco DNA Center, which statement BEST describes how the control plane changes compared to traditional per-device (CLI-based) network management?

A) The control plane remains distributed across each individual device, completely unchanged from traditional networking
B) The control plane is centralized on the controller, enabling network-wide policy enforcement and abstraction away from individual device CLI configuration
C) The control plane is eliminated entirely, and devices forward traffic using only hard-coded static rules
D) The control plane is replaced by SNMP polling, which is used to centrally push configuration changes to devices

---

