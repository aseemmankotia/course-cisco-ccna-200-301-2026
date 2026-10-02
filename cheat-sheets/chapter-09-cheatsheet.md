## Chapter 9 Cheat Sheet — Security, AAA, Hardening

### CIA Triad
| Component | Meaning | Example Control |
|---|---|---|
| Confidentiality | Prevent unauthorized disclosure | Encryption |
| Integrity | Prevent unauthorized modification | Hashing (SHA) |
| Availability | Ensure access when needed | Redundancy, DDoS protection |

### Threats / Vulnerabilities / Exploits
- **Vulnerability** = weakness (unpatched OS)
- **Exploit** = code/method that takes advantage of the vulnerability
- **Threat** = potential danger that could exploit a vulnerability
- **Mitigation** = control that reduces risk (patching, firewalls, ACLs)

### AAA — RADIUS vs TACACS+
| Feature | RADIUS | TACACS+ |
|---|---|---|
| Transport | UDP | TCP |
| Port | 1812/1813 (auth/acct) | 49 |
| Encryption | Password only | Entire packet |
| AAA model | Combines authN+authZ | Separates authN, authZ, acct |
| Command authorization | No | Yes |
| Vendor | Open standard | Cisco proprietary |

### Local vs AAA Authentication
- Local: `username admin secret cisco123` + `line vty 0 15` → `login local`
- AAA: `aaa new-model` → `aaa authentication login default group tacacs+ local` (local = fallback)

### Enable / Line Security
```
enable secret <strong-password>      ! hashed, always wins over enable password
service password-encryption          ! weak Type 7 obfuscation of plaintext pw
line con 0
 password <pw>
 login
line vty 0 15
 login local
 transport input ssh                 ! SSH only, no telnet
```

### SSH Setup Checklist
1. `hostname R1`
2. `ip domain-name lab.local`
3. `crypto key generate rsa` (≥1024 bits, 2048 recommended)
4. `username admin secret cisco123`
5. `line vty 0 15` → `login local` → `transport input ssh`
6. `ip ssh version 2` (optional but recommended)

### VPN Types
| Type | Use Case |
|---|---|
| Site-to-site | Connects two networks (branch ↔ HQ), always-on |
| Remote-access | Individual user connects via VPN client software |

### IPsec (Conceptual)
- **Confidentiality** → Encryption (AES)
- **Integrity** → Hashing (SHA)
- **Authentication** → Verifies peer identity (PSK or certificates)

### Security Program Elements
- User awareness & training (phishing simulations)
- Physical access control (badges, mantraps, cameras)
- Policies (password policy, acceptable use)

### Common Exam Traps
- Assuming RADIUS encrypts the whole packet — it only encrypts the password.
- Forgetting `enable secret` always overrides `enable password`.
- Enabling `service password-encryption` and thinking it's strong encryption — it's reversible Type 7.
- Leaving `transport input all` instead of `ssh` when asked to disable Telnet.
