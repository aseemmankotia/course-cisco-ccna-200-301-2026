## Chapter 2: IPv4 Subnetting, VLSM, IPv6, and Transport Protocols — Flashcards

| # | Front (Question) | Back (Answer) |
|---|-----------------|---------------|
| 1 | IPv6 link-local address prefix? | FE80::/10. Exam tip: every IPv6 interface auto-configures one; used for neighbor discovery and routing protocols, never routed off-link. |
| 2 | IPv6 Unique Local Address (ULA) prefix? | FC00::/7, commonly seen as FD00::/8 in practice. Exam tip: private-address equivalent of IPv4 RFC1918 space, not globally routable. |
| 3 | IPv6 multicast address prefix and key well-known addresses? | FF00::/8. FF02::1 = all-nodes (link-local), FF02::2 = all-routers (link-local). Exam tip: IPv6 has no broadcast — multicast replaces it. |
| 4 | TCP vs UDP: which is connection-oriented with a handshake? | TCP (SYN, SYN-ACK, ACK). Exam tip: UDP is connectionless — no handshake, no retransmission, no flow control; used where speed matters more than reliability (DNS queries, VoIP, DHCP). |
| 5 | Well-known ports: DNS and DHCP? | DNS = port 53 (UDP for queries, TCP for zone transfers). DHCP server = UDP 67, DHCP client = UDP 68. Exam tip: memorize protocol AND transport (TCP/UDP) for each service. |
| 6 | /27 subnet mask — usable hosts? | 255.255.255.224 = /27 = 30 usable hosts (2^5 - 2). Exam tip: formula = 2^(host bits) - 2 for usable hosts on IPv4 subnets. |
| 7 | 2.4 GHz non-overlapping channels (US)? | Channels 1, 6, 11. Exam tip: 5 GHz offers many more non-overlapping 20 MHz channels (e.g., 36, 40, 44, 48...) due to wider available spectrum. |
| 8 | VM vs Container: what do containers share with the host? | Containers share the host OS kernel; VMs each run a full independent guest OS via a hypervisor. Exam tip: containers = lighter, faster startup, less isolation than VMs. |
| 9 | What is a VRF and how does it differ from a VM? | Virtual Routing and Forwarding creates multiple isolated Layer 3 routing tables on one physical router/switch. Exam tip: VRF virtualizes network routing, not compute — don't confuse with server virtualization. |
| 10 | Switch behavior when destination MAC is unknown? | Unknown unicast flooding — the frame is sent out all ports (except ingress) in the VLAN. Exam tip: switches learn source MAC + ingress port on every received frame to populate the MAC address table. |
| 11 | IPv6 address compression rule: how many times can '::' appear in an address? | Only once per address. Exam tip: leading zeros per hextet are dropped individually; '::' replaces only the longest single run of consecutive all-zero hextets. |
| 12 | VLSM: what problem does it solve and what's the allocation strategy? | VLSM assigns variable-length subnet masks sized to actual host needs, minimizing address waste. Exam tip: always allocate the largest host requirement first, then work down to the smallest (e.g., WAN /30 links last). |
