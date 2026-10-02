## Chapter 10 Cheat Sheet — ACLs, Layer 2 Security, Wireless

### ACL Types
| Type | Number Range | Filters On | Placement |
|---|---|---|---|
| Standard | 1–99, 1300–1999 | Source IP only | Close to **destination** |
| Extended | 100–199, 2000–2699 | Source, dest, protocol, port | Close to **source** |

**Rule of thumb:** Standard = blunt instrument → place near what you're protecting. Extended = scalpel → place near the traffic origin to save bandwidth.

### Wildcard Mask Quick Math
`Wildcard = 255.255.255.255 - Subnet Mask`

| CIDR | Subnet Mask | Wildcard |
|---|---|---|
| /24 | 255.255.255.0 | 0.0.0.255 |
| /23 | 255.255.254.0 | 0.0.1.255 |
| /22 | 255.255.252.0 | 0.0.3.255 |
| /30 | 255.255.255.252 | 0.0.0.3 |

`host` keyword = wildcard 0.0.0.0. `any` = wildcard 255.255.255.255.

### Port Security
```
switchport port-security
switchport port-security maximum 2
switchport port-security mac-address sticky
switchport port-security violation {protect|restrict|shutdown}
```

| Violation Mode | Drops Traffic? | Logs/Counts? | Port State |
|---|---|---|---|
| protect | Yes | No | Stays up |
| restrict | Yes | Yes | Stays up |
| shutdown (default) | Yes | Yes | Err-disabled |

Recover an err-disabled port: `shutdown` then `no shutdown`, or configure `errdisable recovery`.

### Layer 2 Attack Mitigations
| Threat | Mitigation | Mechanism |
|---|---|---|
| Rogue DHCP server | DHCP snooping | Blocks DHCP server msgs on untrusted ports; builds binding table |
| ARP spoofing / MITM | Dynamic ARP Inspection (DAI) | Validates ARP against DHCP snooping binding table |
| MAC flooding / unauthorized device | Port Security | Limits/authorizes MACs per port |

**Dependency:** DAI requires DHCP snooping to be enabled — the binding table is shared.

### Wireless Security
| Feature | WPA2 | WPA3 |
|---|---|---|
| Encryption | AES-CCMP | AES-GCMP (stronger in Enterprise 192-bit) |
| Key exchange | 4-way handshake (PSK) | SAE (Simultaneous Auth of Equals) |
| Offline attack resistance | Weak PSKs crackable offline | Forward secrecy, resists offline cracking |

| Auth Method | Use Case | Mechanism |
|---|---|---|
| PSK (Personal) | SOHO / small office | Single shared passphrase |
| 802.1X (Enterprise) | Corporate | Per-user creds via RADIUS/EAP |

### Exam Gotchas
- Standard ACL near source = blocks traffic to unintended destinations too.
- Confusing wildcard mask with subnet mask on wildcard-calculation questions.
- Assuming 'restrict' err-disables the port — only 'shutdown' does.
- Believing DAI alone stops rogue DHCP servers — that's DHCP snooping's job.
- Treating WPA3-Personal as multi-user auth — it's still a single shared PSK, just SAE-protected.
