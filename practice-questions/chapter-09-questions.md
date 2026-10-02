## Chapter 9: Security Concepts, AAA, and Device Hardening — Practice Questions

**Q1.** A company wants centralized authentication for all network administrators AND the ability to log every individual command each admin runs on routers and switches for auditing. Which solution BEST meets these requirements?

A) RADIUS server for AAA
B) TACACS+ server for AAA
C) Local username/password database
D) SNMPv3 with per-user credentials

<details>
<summary>Answer</summary>

**Correct: B**

TACACS+ separates authentication, authorization, and accounting and supports per-command authorization/accounting, which is required for granular command logging.

**Why the others are wrong:**
- RADIUS combines authentication and authorization and encrypts only the password field; it does not support per-command authorization.
- Local authentication cannot centralize accounts across many devices or log commands per user.
- SNMPv3 is for monitoring/management, not for AAA authentication or command logging.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** During a security audit, a company confirms that customer data was not modified while traveling across the network. Which principle of the CIA triad does this verify?

A) Confidentiality
B) Availability
C) Integrity
D) Non-repudiation

<details>
<summary>Answer</summary>

**Correct: C**

Integrity ensures data is not altered in transit or at rest, typically verified with hashing.

**Why the others are wrong:**
- Confidentiality ensures data is not disclosed to unauthorized parties, not that it wasn't modified.
- Availability ensures systems/data are accessible when needed, unrelated to modification.
- Non-repudiation is not part of the CIA triad tested on 200-301.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q3.** A network engineer must ensure that only SSH is allowed for remote management of a switch and that Telnet is completely disabled on all VTY lines. Which configuration accomplishes this?

A) line vty 0 15 / transport input ssh
B) line vty 0 15 / transport input all
C) line vty 0 15 / transport input telnet ssh
D) line con 0 / transport input ssh

<details>
<summary>Answer</summary>

**Correct: A**

'transport input ssh' on the VTY lines restricts remote access to SSH only, disabling Telnet.

**Why the others are wrong:**
- 'transport input all' allows both Telnet and SSH, failing the requirement.
- 'transport input telnet ssh' still allows Telnet.
- The console line (con 0) is for local access, not remote VTY management.

</details>

---

**Q4.** Which AAA protocol uses UDP ports 1812 and 1813 and encrypts only the password in the access-request packet?

A) RADIUS
B) TACACS+
C) Kerberos
D) LDAPS

<details>
<summary>Answer</summary>

**Correct: A**

RADIUS uses UDP 1812 (authentication) and 1813 (accounting), encrypting only the password field while the rest of the packet is sent in clear text.

**Why the others are wrong:**
- TACACS+ uses TCP port 49 and encrypts the entire packet body.
- Kerberos uses tickets over TCP/UDP 88 and is not a Cisco AAA protocol tested here.
- LDAPS is a directory access protocol over TCP 636, not an AAA protocol for network device access.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q5.** An employee working from home needs to securely connect their laptop to the corporate network over the internet. Which VPN type should be deployed?

A) Site-to-site VPN
B) Remote-access VPN
C) GRE tunnel
D) 802.1Q trunk

<details>
<summary>Answer</summary>

**Correct: B**

A remote-access VPN allows an individual client to establish a secure encrypted tunnel into the corporate network, typically using client software.

**Why the others are wrong:**
- Site-to-site VPN connects two networks (e.g., two offices), not a single remote user.
- GRE is a tunneling protocol with no built-in encryption; it does not by itself secure remote user traffic.
- 802.1Q trunking is a Layer 2 VLAN tagging technology, unrelated to remote connectivity over the internet.

</details>

---

**Q6.** Which command encrypts all currently configured plaintext passwords (such as line and username passwords) in the running-config using a reversible Type 7 cipher?

A) enable secret
B) service password-encryption
C) crypto key generate rsa
D) aaa authentication login default local

<details>
<summary>Answer</summary>

**Correct: B**

'service password-encryption' applies weak, reversible Type 7 encryption to plaintext passwords stored in the configuration, hiding them from casual viewing.

**Why the others are wrong:**
- 'enable secret' creates a strongly hashed privileged EXEC password but does not encrypt other passwords.
- 'crypto key generate rsa' generates keys for SSH, unrelated to password encryption.
- This AAA command defines the authentication method list; it does not encrypt passwords.

</details>

---

**Q7.** A router is configured with both 'enable password cisco123' and 'enable secret cisco456'. Which password is used to enter privileged EXEC mode?

A) cisco123, because it was configured first
B) Both are accepted
C) Neither works until service password-encryption is enabled
D) cisco456, because enable secret always takes precedence

<details>
<summary>Answer</summary>

**Correct: D**

When both are configured, IOS always uses 'enable secret' (hashed) over 'enable password' (plaintext), regardless of configuration order.

**Why the others are wrong:**
- Order of configuration does not matter; enable secret always wins.
- Only one password is valid at a time — enable secret.
- service password-encryption only affects Type 7 passwords, not which enable password is authoritative.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q8.** Which statement correctly distinguishes a vulnerability from an exploit?

A) A vulnerability is the tool or code used to attack a weakness; an exploit is the weakness itself
B) A vulnerability and an exploit are the same thing
C) A vulnerability only applies to software, while an exploit only applies to hardware
D) A vulnerability is a weakness in a system; an exploit is the mechanism used to take advantage of that weakness

<details>
<summary>Answer</summary>

**Correct: D**

A vulnerability is a flaw or weakness (e.g., unpatched software); an exploit is the method or code that leverages that weakness to cause harm.

**Why the others are wrong:**
- This reverses the definitions.
- They are related but distinct terms tested separately on the exam.
- Both terms can apply to software or hardware weaknesses.

</details>

---

