## Chapter 8: NAT, NTP, DHCP/DNS, SNMP, Syslog, and QoS — Practice Questions

**Q1.** A network engineer wants to allow 100 inside hosts to reach the internet using a single outside interface IP address on router R1, with GigabitEthernet0/1 as the outside interface. Which configuration accomplishes this?

A) ip nat inside source list 1 interface GigabitEthernet0/1 overload
B) ip nat pool POOL1 203.0.113.1 203.0.113.1 netmask 255.255.255.0 / ip nat inside source list 1 pool POOL1
C) ip nat inside source static 10.1.1.0 203.0.113.1
D) ip nat outside source list 1 interface GigabitEthernet0/1 overload

<details>
<summary>Answer</summary>

**Correct: A**

PAT (overload) using the outside interface's own IP lets many inside hosts share one public address by translating source ports; 'interface' overload is the standard way to configure this without wasting a pool.

**Why the others are wrong:**
- A pool with only one address works but is unnecessarily complex versus using the interface IP directly, and without 'overload' it would fail after the first host uses that IP.
- Static NAT maps one inside address to one outside address permanently — it cannot map an entire subnet (100 hosts) to a single IP.
- 'ip nat outside source' translates traffic from the outside network, not the correct direction for hosts going out to the internet.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** A company has 60 internal hosts and only 5 public IP addresses available for outbound translation. All 60 hosts must be able to access the internet simultaneously. Which NAT design meets this requirement?

A) Dynamic NAT pool of 5 addresses without overload
B) Static NAT with 5 mappings
C) PAT using a /29 subnet assigned directly to each host
D) Dynamic NAT pool of 5 addresses with overload (PAT)

<details>
<summary>Answer</summary>

**Correct: D**

PAT with a pool allows all 60 hosts to share the 5 public addresses simultaneously by multiplexing on port numbers, satisfying the requirement with limited public IPs.

**Why the others are wrong:**
- Without overload, only 5 hosts (one per address) could have active translations at once — the other 55 would be denied.
- Static NAT requires one dedicated public IP per host, and 5 mappings only covers 5 of the 60 hosts.
- PAT does not assign public subnets to hosts; hosts keep private addressing and only the source IP/port is translated at the NAT boundary.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q3.** Clients on VLAN 20 (subnet 10.20.0.0/24) need to receive IP addresses from a centralized DHCP server located on a different subnet reachable via the core router. On which interface should 'ip helper-address' be configured?

A) On the DHCP server's own interface
B) On every interface in the network to be safe
C) On the SVI or router interface for VLAN 20, facing the DHCP clients
D) On the interface directly connected to the DHCP server subnet

<details>
<summary>Answer</summary>

**Correct: C**

The router interface that receives the client's DHCP broadcast (the VLAN 20 gateway/SVI) needs ip helper-address so it can convert the broadcast to a unicast and forward it toward the DHCP server.

**Why the others are wrong:**
- Configuring it on the DHCP server's own interface serves no purpose — the command relays broadcasts away from the segment that receives them.
- Applying it everywhere is unnecessary and can create unwanted forwarding of broadcast traffic on unrelated segments.
- The interface connected to the server subnet is the destination of the relay, not where the broadcast is received; helper-address must sit on the client-facing interface.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q4.** Which protocol synchronizes device clocks across a network using a hierarchical stratum numbering system, where stratum 1 servers are directly connected to an authoritative time source?

A) SNMP
B) Syslog
C) NTP
D) TFTP

<details>
<summary>Answer</summary>

**Correct: C**

NTP (Network Time Protocol) uses stratum levels 0-15 (16 = unsynchronized), where stratum 0 is the reference clock (e.g., GPS/atomic) and stratum 1 servers sync directly to it.

**Why the others are wrong:**
- SNMP is used for network device monitoring and management, not time synchronization.
- Syslog is a logging protocol for sending event messages to a collector; it has no stratum concept.
- TFTP is a simple file transfer protocol used for IOS images and configs, unrelated to time sync.

</details>

---

**Q5.** A network monitoring system needs to receive unsolicited, immediate alerts from devices when a critical event occurs, rather than polling devices periodically. Which mechanism accomplishes this?

A) SNMP GET requests
B) SNMP traps
C) Syslog facility filtering
D) NTP broadcast mode

<details>
<summary>Answer</summary>

**Correct: B**

SNMP traps are unsolicited messages sent from an agent to the manager (UDP 162) the instant a defined event occurs, avoiding the delay of periodic polling.

**Why the others are wrong:**
- SNMP GET is a manager-initiated poll (UDP 161) that requests data on demand — it is not event-driven or unsolicited.
- Syslog facility filtering only categorizes log message sources; it doesn't describe the push-notification mechanism being asked about.
- NTP broadcast mode is used to distribute time information, unrelated to fault/event notification.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q6.** Which syslog severity level number corresponds to 'Critical' condition messages?

A) Level 1
B) Level 3
C) Level 4
D) Level 2

<details>
<summary>Answer</summary>

**Correct: D**

Syslog severity levels are 0-Emergency, 1-Alert, 2-Critical, 3-Error, 4-Warning, 5-Notice, 6-Informational, 7-Debugging — Critical is level 2.

**Why the others are wrong:**
- Level 1 is Alert, one step more severe than Critical.
- Level 3 is Error, one step less severe than Critical.
- Level 4 is Warning, two steps less severe than Critical.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q7.** After configuring dynamic NAT, an engineer wants to confirm that inside local addresses are actively being translated to inside global addresses. Which command should be used?

A) show ip nat statistics
B) show ip nat translations
C) show running-config | include nat
D) show ip route nat

<details>
<summary>Answer</summary>

**Correct: B**

'show ip nat translations' displays the current active NAT translation table, showing inside local/global and outside local/global address pairs.

**Why the others are wrong:**
- 'show ip nat statistics' shows totals like active translations count and hits/misses, but not the actual translation entries themselves.
- Filtering the running-config only shows the NAT configuration commands, not live translation activity.
- 'show ip route nat' is not a valid Cisco IOS command.

</details>

---

**Q8.** A service provider needs to enforce a strict bandwidth limit on a customer link, dropping any traffic that exceeds the contracted rate immediately rather than buffering it. Which QoS mechanism should be used?

A) Traffic shaping
B) Weighted fair queuing
C) Traffic policing
D) Classification and marking

<details>
<summary>Answer</summary>

**Correct: C**

Policing enforces a rate limit by dropping (or remarking) excess traffic immediately without buffering, making it ideal for strict enforcement at a provider edge.

**Why the others are wrong:**
- Shaping buffers excess traffic and delays it to smooth bursts to conform to a rate — it does not drop traffic outright as the first action.
- Weighted fair queuing manages how queued packets are scheduled during congestion; it doesn't enforce a hard rate limit by dropping excess traffic.
- Classification and marking identify and tag traffic for QoS treatment but do not themselves enforce or limit bandwidth.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

