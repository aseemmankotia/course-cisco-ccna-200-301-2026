## Chapter 8: NAT, NTP, DHCP/DNS, SNMP, Syslog, and QoS — Flashcards

| # | Front (Question) | Back (Answer) |
|---|-----------------|---------------|
| 1 | Static NAT vs Dynamic NAT vs PAT (overload) — key difference? | Static = permanent 1:1 mapping. Dynamic = pool of addresses, first-come first-served, 1:1 at a time. PAT/overload = many inside hosts share one (or few) outside IP(s) using port translation. Exam tip: PAT is the only type that allows many-to-one. |
| 2 | NAT overload using outside interface — command? | ip nat inside source list <ACL#> interface <if> overload. Exam tip: no pool needed when reusing the outside interface's own IP. |
| 3 | Command to view active NAT translations? | show ip nat translations. Exam tip: show ip nat statistics gives counts/hits, not the actual entries. |
| 4 | NTP stratum numbering range and meaning? | Stratum 0 = reference clock (GPS/atomic, not a network device). Stratum 1 = directly connected to stratum 0. Range goes up to 15; stratum 16 = unsynchronized. Exam tip: lower stratum number = closer to authoritative source = more accurate. |
| 5 | NTP port number? | UDP port 123. Exam tip: NTP uses client-server model; a device can be both a client and server simultaneously. |
| 6 | DHCP DORA process steps? | Discover (client broadcast) → Offer (server broadcast) → Request (client broadcasts chosen offer) → Acknowledge (server confirms lease). Exam tip: all four messages are broadcast unless a relay agent converts them to unicast. |
| 7 | DHCP Relay command and placement? | ip helper-address <dhcp-server-ip>, configured on the interface (SVI) that receives the client's broadcast. Exam tip: by default it forwards 8 UDP broadcast services, including DHCP, TFTP, and DNS. |
| 8 | Syslog severity levels 0-7 — list in order? | 0 Emergency, 1 Alert, 2 Critical, 3 Error, 4 Warning, 5 Notice, 6 Informational, 7 Debugging. Mnemonic: 'Every Awesome Cisco Engineer Will Need Icecream Daily'. Exam tip: lower number = more severe. |
| 9 | SNMP GET vs SNMP Trap? | GET = manager polls agent for data (UDP 161, on-demand/scheduled). Trap = agent pushes unsolicited alert to manager (UDP 162, event-driven). Exam tip: traps are faster for real-time fault notification. |
| 10 | SSH vs Telnet — key exam distinction? | SSH = TCP port 22, encrypted. Telnet = TCP port 23, sends data (including passwords) in plaintext. Exam tip: SSH is the only secure choice for remote CLI management. |
| 11 | TFTP vs FTP — key exam distinction? | TFTP = UDP port 69, no authentication, used for quick IOS/config transfers. FTP = TCP ports 20/21, supports authentication and is more reliable. Exam tip: TFTP is simpler but less secure. |
| 12 | QoS Policing vs Shaping — key exam distinction? | Policing drops (or remarks) traffic exceeding the rate limit immediately, no buffering — causes retransmissions. Shaping buffers and delays excess traffic to smooth output, avoiding drops. Exam tip: shaping = smoother but adds delay; policing = strict but can drop bursts. |
