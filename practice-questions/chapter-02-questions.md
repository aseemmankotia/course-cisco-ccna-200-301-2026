## Chapter 2: IPv4 Subnetting, VLSM, IPv6, and Transport Protocols — Practice Questions

**Q1.** A network engineer must subnet 192.168.1.0/24 using VLSM for four departments: Sales (50 hosts), Engineering (25 hosts), Guest (10 hosts), and a WAN link (2 hosts). Which allocation correctly assigns subnets with minimal waste?

A) Sales: 192.168.1.0/25, Engineering: 192.168.1.128/27, Guest: 192.168.1.160/28, WAN: 192.168.1.176/30
B) Sales: 192.168.1.0/27, Engineering: 192.168.1.32/27, Guest: 192.168.1.64/28, WAN: 192.168.1.80/30
C) Sales: 192.168.1.0/26, Engineering: 192.168.1.32/27, Guest: 192.168.1.64/28, WAN: 192.168.1.80/30
D) Sales: 192.168.1.0/26, Engineering: 192.168.1.64/27, Guest: 192.168.1.96/28, WAN: 192.168.1.112/30

<details>
<summary>Answer</summary>

**Correct: D**

Largest requirement first: /26 gives 62 hosts for Sales, /27 gives 30 hosts for Engineering starting at the next available boundary (.64), /28 gives 14 hosts for Guest at .96, and /30 gives exactly 2 usable hosts for the WAN link at .112 — no overlapping ranges.

**Why the others are wrong:**
- Uses a /25 (126 hosts) for only 50 hosts, wasting 76 addresses when a /26 suffices.
- Engineering's /27 starting at .32 overlaps address space Sales already needs beyond .64 boundary alignment, and Sales /27 is too small for 50 hosts (only 30 usable).
- Sales /26 is correct size but Engineering subnet at .32 falls inside the Sales /26 block (.0–.63), causing an overlap.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** Which sequence correctly describes the TCP three-way handshake used to establish a connection?

A) ACK, SYN, SYN-ACK
B) SYN, ACK, FIN
C) SYN-ACK, SYN, ACK
D) SYN, SYN-ACK, ACK

<details>
<summary>Answer</summary>

**Correct: D**

The client sends SYN, the server responds with SYN-ACK, and the client completes the connection with ACK — establishing a reliable, connection-oriented session before data transfer.

**Why the others are wrong:**
- Reverses the required order; ACK cannot be sent before the connection is initiated.
- FIN is used to terminate a connection (four-way close), not establish one.
- The server cannot send SYN-ACK before receiving the client's initial SYN.

</details>

---

**Q3.** Which IPv6 address type replaces the functionality of IPv4 broadcast for reaching all hosts on a local link?

A) Anycast address
B) Link-local unicast address
C) Unique local address
D) Multicast address (e.g., FF02::1)

<details>
<summary>Answer</summary>

**Correct: D**

IPv6 eliminates broadcast entirely; FF02::1 (all-nodes multicast, link-local scope) is used to reach every host on the local segment, replacing IPv4's broadcast behavior.

**Why the others are wrong:**
- Anycast delivers to the nearest single member of a group, not all hosts.
- Link-local unicast (FE80::/10) addresses a single interface, not all hosts.
- Unique local addresses (FC00::/7) are for private routing scope, not all-hosts delivery.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q4.** A switch receives a frame destined for MAC address 00:1A:2B:3C:4D:5E and forwards it out every port except the port on which it arrived. What does this behavior indicate?

A) The destination MAC address is not yet present in the switch's MAC address table
B) The destination MAC address is a broadcast address
C) The switch has detected a duplicate MAC address and is isolating the port
D) The VLAN is misconfigured and traffic is looping

<details>
<summary>Answer</summary>

**Correct: A**

When a switch does not have an entry for the destination MAC in its CAM table, it performs unknown unicast flooding, sending the frame out all ports (except the ingress port) within the VLAN until it learns the correct port from a reply.

**Why the others are wrong:**
- A broadcast MAC (FFFF.FFFF.FFFF) always floods, but this is a specific unicast address, indicating the table simply lacks the entry.
- Duplicate MAC detection does not cause flooding; it causes MAC flapping log messages.
- Flooding an unknown unicast is normal switch behavior, not evidence of a loop.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q5.** A company needs to run multiple isolated instances of the same application on a single physical server with minimal resource overhead and fast startup times. Which virtualization technology BEST meets this requirement?

A) Type 1 hypervisor with separate virtual machines per instance
B) Virtual Routing and Forwarding (VRF) instances
C) Type 2 hypervisor running on a host operating system
D) Containers sharing the host OS kernel

<details>
<summary>Answer</summary>

**Correct: D**

Containers package the application and its dependencies while sharing the host OS kernel, resulting in far less overhead and much faster startup than full virtual machines.

**Why the others are wrong:**
- Type 1 hypervisors run full guest operating systems per VM, consuming significantly more resources and taking longer to boot than containers.
- VRF is a Layer 3 network virtualization construct for isolating routing tables, not an application/OS virtualization technology.
- Type 2 hypervisors run on top of a host OS and still require a full guest OS per instance, making them heavier than containers.

</details>

---

**Q6.** Which set of channels represents the non-overlapping 2.4 GHz Wi-Fi channels commonly used in the United States to avoid co-channel interference?

A) 1, 5, 9
B) 2, 7, 12
C) 3, 8, 13
D) 1, 6, 11

<details>
<summary>Answer</summary>

**Correct: D**

Each 2.4 GHz channel occupies roughly 22 MHz; channels 1, 6, and 11 are spaced 5 channels apart, giving enough separation to avoid overlap in the 2.4 GHz band available in the US (channels 1–11).

**Why the others are wrong:**
- Channels 1, 5, and 9 are too close together and their frequency ranges overlap.
- Channels 2, 7, and 12 overlap adjacent channels, and channel 12 has restricted power in the US.
- Channels 3, 8, and 13 overlap adjacent channels, and channel 13 is not permitted for use in the US.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q7.** What is the correctly compressed representation of the IPv6 address 2001:0db8:0000:0000:0000:ff00:0042:8329?

A) 2001:db8:0:0:0:ff00:42:8329
B) 2001::db8::ff00:42:8329
C) 2001:db8::ff00:42:8329
D) 2001:db8:ff00::42:8329

<details>
<summary>Answer</summary>

**Correct: C**

Leading zeros in each hextet are dropped and the longest run of consecutive all-zero hextets (three groups of 0000) is replaced once with '::', producing 2001:db8::ff00:42:8329.

**Why the others are wrong:**
- This form drops leading zeros correctly but fails to use '::' compression, making it valid but not the 'correctly compressed' (shortest) form as required.
- The double '::' is illegal — '::' can appear only once per address because its expansion would be ambiguous otherwise.
- This rearranges the zero groups incorrectly and does not match the original address's hextet positions.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q8.** A host is assigned IP address 172.16.45.13 with subnet mask 255.255.240.0. What is the network address for this host's subnet?

A) 172.16.0.0
B) 172.16.44.0
C) 172.16.48.0
D) 172.16.32.0

<details>
<summary>Answer</summary>

**Correct: D**

255.255.240.0 is a /20 mask, giving a block size of 16 in the third octet. The blocks are 0,16,32,48... The value 45 falls between 32 and 48, so the network address is 172.16.32.0.

**Why the others are wrong:**
- 172.16.0.0 would only be correct for a /16 mask, not /20.
- 172.16.44.0 is not a valid subnet boundary since block size is 16, not 1.
- 172.16.48.0 is the start of the NEXT subnet block, not the one containing .45.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

