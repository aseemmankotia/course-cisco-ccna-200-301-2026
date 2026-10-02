## Chapter 9: Security Concepts, AAA, and Device Hardening — Flashcards

| # | Front (Question) | Back (Answer) |
|---|-----------------|---------------|
| 1 | RADIUS default UDP ports for authentication and accounting? | 1812 (authentication) and 1813 (accounting). Legacy ports 1645/1646 may appear on older/exam-legacy questions. Exam tip: RADIUS = UDP. |
| 2 | TACACS+ default port? | TCP 49. Exam tip: TACACS+ = TCP, encrypts entire packet body (Cisco proprietary). |
| 3 | RADIUS vs TACACS+ — encryption scope? | RADIUS encrypts only the password field. TACACS+ encrypts the entire packet payload. Exam tip: 'entire packet' = TACACS+. |
| 4 | RADIUS vs TACACS+ — AAA separation? | RADIUS combines authentication + authorization into one step. TACACS+ separates authentication, authorization, and accounting into three distinct processes (enables per-command authorization). |
| 5 | Which AAA protocol supports per-command authorization/logging? | TACACS+. Used when auditors need to see exactly which commands each admin ran on a device. |
| 6 | CIA Triad — three components? | Confidentiality (prevent unauthorized disclosure), Integrity (prevent unauthorized modification), Availability (ensure uptime/access). Exam gives a scenario and asks which one applies. |
| 7 | Command to encrypt plaintext passwords in running-config? | service password-encryption — applies weak, reversible Type 7 encryption. Does NOT strengthen security, only obscures casual viewing. Does not affect enable secret (already hashed). |
| 8 | Command to set a strongly hashed privileged EXEC password? | enable secret <password> — uses MD5 (Type 5) or newer PBKDF2/scrypt hashing (Type 8/9) depending on IOS version. Always takes precedence over 'enable password' if both are set. |
| 9 | Commands to restrict VTY lines to SSH-only management? | line vty 0 15 → transport input ssh. Also requires: username/password or AAA, 'login local', a hostname/domain-name, and 'crypto key generate rsa'. |
| 10 | Minimum steps to enable SSH on a Cisco device? | 1) hostname + ip domain-name, 2) crypto key generate rsa (modulus ≥1024, 2048 recommended), 3) username/password or AAA, 4) line vty → login local + transport input ssh, 5) (optional) ip ssh version 2. |
| 11 | Site-to-site VPN vs remote-access VPN? | Site-to-site: connects two fixed networks/sites (always-on, e.g., branch to HQ) using a gateway device on each end. Remote-access: connects an individual client (e.g., telecommuter laptop) to a network via client software. |
| 12 | What does IPsec provide conceptually (exam level)? | Confidentiality (encryption, e.g., AES), Integrity (hashing, e.g., SHA), and Authentication (verifying peer identity). Exam tests recognizing these three pillars, not deep protocol math. |
