## Chapter 10: ACLs, Layer 2 Security, and Wireless Security — Flashcards

| # | Front (Question) | Back (Answer) |
|---|-----------------|---------------|
| 1 | Standard ACL number ranges? | 1–99 and 1300–1999. Filters by source IP address only. Exam tip: place close to the destination. |
| 2 | Extended ACL number ranges? | 100–199 and 2000–2699. Filters by source, destination, protocol, and port. Exam tip: place close to the source. |
| 3 | How do you calculate a wildcard mask from a subnet mask? | Subtract the subnet mask from 255.255.255.255. Example: /24 (255.255.255.0) → wildcard 0.0.0.255. |
| 4 | Wildcard mask for a /22 network? | 0.0.3.255 — matches a block of 1024 addresses. Exam trap: don't confuse with the /22 subnet mask (255.255.252.0). |
| 5 | ACL placement rule: standard ACL | Place as close to the DESTINATION as possible — because it filters by source only and could otherwise block traffic meant for other destinations. |
| 6 | ACL placement rule: extended ACL | Place as close to the SOURCE as possible — it can precisely match src/dst/port, so it can be filtered immediately without wasting bandwidth. |
| 7 | Port security violation mode: protect | Drops violating frames silently. No log message, no counter increment, port stays up. |
| 8 | Port security violation mode: restrict | Drops violating frames, generates a syslog message, and increments the violation counter. Port stays up. |
| 9 | Port security violation mode: shutdown | Default mode. Puts the port into err-disabled state on violation — requires 'shutdown'/'no shutdown' or errdisable recovery to restore. |
| 10 | What does DHCP snooping do? | Classifies ports as trusted/untrusted and blocks DHCP server messages (offer/ack) from untrusted ports, preventing rogue DHCP servers. Builds the binding table used by DAI. |
| 11 | What does Dynamic ARP Inspection (DAI) do? | Validates ARP packets against the DHCP snooping binding table (IP-to-MAC) to prevent ARP spoofing / man-in-the-middle attacks. Requires DHCP snooping to be enabled first. |
| 12 | WPA2 vs WPA3 — key difference? | WPA2 uses AES-CCMP with a 4-way handshake (vulnerable to offline dictionary attacks on weak PSKs). WPA3 uses SAE (Simultaneous Authentication of Equals), providing forward secrecy and resistance to offline password cracking. |
