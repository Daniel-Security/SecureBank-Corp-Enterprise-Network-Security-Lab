---

## 🔒 Security Zones

| Zone | VLAN | Subnet | Purpose |
|------|------|--------|---------|
| Management | 10 | 172.16.10.0/24 | IT staff, SIEM, DNS |
| Teller | 20 | 172.16.20.0/24 | Bank teller workstations |
| Core Banking | 30 | 172.16.30.0/24 | Transaction processing servers |
| Customer Data | 40 | 172.16.40.0/24 | Customer account database |
| ATM Network | 50 | 172.16.50.0/24 | ATM machines |
| DMZ | 60 | 172.16.60.0/24 | Online banking web server |
| Guest WiFi | 70 | 172.16.70.0/24 | Customer lobby WiFi |
| Branch LAN | 100 | 172.16.100.0/24 | Branch office staff |

---

## 🛡️ Security Controls Implemented

### Network Device Hardening
- ✅ SSH version 2 with RSA 2048-bit keys — Telnet completely disabled
- ✅ Tiered privilege levels — helpdesk (5), netadmin (10), sysadmin (15)
- ✅ Login lockout — 3 failed attempts triggers 120 second block
- ✅ Full AAA accounting — every login logged with timestamp
- ✅ Legal warning banners on all devices
- ✅ Unused interfaces disabled and assigned to unused VLAN

### Network Segmentation
- ✅ 8 isolated security zones using 802.1Q VLANs
- ✅ Native VLAN changed from default VLAN 1 to VLAN 99 — prevents VLAN hopping
- ✅ Port security with sticky MAC learning on all access ports
- ✅ Violation mode restrict — alerts without disrupting operations

### Zero Trust ACL Architecture

| ACL | Policy |
|-----|--------|
| PROTECT-COREBANKING | Only Management, Tellers, ATMs, and Branch reach Core Banking on HTTPS only |
| PROTECT-CUSTOMERDATA | Only Management and Core Banking server reach Customer Data |
| TELLER-POLICY | Tellers restricted to Core Banking HTTPS and DNS only |
| ATM-POLICY | ATMs restricted to Core Banking HTTPS and DNS only |
| GUEST-ISOLATE | Guest WiFi blocked from all internal subnets |
| DMZ-POLICY | DMZ server cannot initiate connections to any internal zone |
| MGMT-ACCESS | Only Management subnet can SSH to network devices |

### Wireless Security
- ✅ WPA2 Personal with AES encryption for guest WiFi
- ✅ Guest SSID on isolated VLAN 70 with no internal access
- ✅ Separate DNS for guests pointing to 8.8.8.8 — guests cannot resolve internal hostnames

### Security Monitoring
- ✅ Centralized syslog on SRV-SIEM collecting from all network devices
- ✅ Timestamped log entries for every security event
- ✅ ACL hit counters providing real-time visibility into blocked traffic
- ✅ Internal DNS — internal hostnames never exposed publicly

### Routing and Availability
- ✅ OSPF dynamic routing between HQ and Branch
- ✅ /30 WAN subnet conserving addresses on point-to-point link
- ✅ DHCP with excluded ranges across all 8 zones
- ✅ Static IPs for all servers ensuring ACL rules never break

---

## 📜 Compliance Coverage

| Regulation | Requirements Met |
|------------|-----------------|
| PCI DSS | Network segmentation, access control, logging, encryption, least privilege |
| GLBA | Access restrictions on customer financial data |
| GDPR | Data isolation and access controls on customer personal data |
| SOX | Audit logging and change management controls |

---

## ✅ Verification Results — 18/18 Tests Passed

| Test | Result |
|------|--------|
| Teller cannot reach Customer Data | ✅ PASS |
| Teller cannot reach Management | ✅ PASS |
| Teller cannot reach Core Banking directly | ✅ PASS |
| IT Management has full network access | ✅ PASS |
| ATM cannot reach Teller network | ✅ PASS |
| ATM cannot reach Customer Data | ✅ PASS |
| Guest WiFi cannot reach Core Banking | ✅ PASS |
| Guest WiFi cannot reach Teller network | ✅ PASS |
| Guest WiFi cannot reach Management | ✅ PASS |
| Branch reaches HQ via OSPF | ✅ PASS |
| DMZ server cannot reach internal zones | ✅ PASS |
| All devices sending logs to SIEM | ✅ PASS |
| Port security active on all access ports | ✅ PASS |
| SSH working, Telnet blocked | ✅ PASS |
| DHCP serving all zones correctly | ✅ PASS |
| DNS resolving internal hostnames | ✅ PASS |
| Login lockout protecting all devices | ✅ PASS |
| VLAN hopping prevented via native VLAN | ✅ PASS |

---

## 🛠️ Technologies Used

- **Platform** — Cisco Packet Tracer 8.x
- **Devices** — Cisco 2911 routers, Cisco 2960-24TT switches
- **Protocols** — OSPF, 802.1Q, SSH v2, DHCP, DNS, Syslog, WPA2
- **Security** — Extended ACLs, VLAN segmentation, port security, AAA, Zero Trust

---

## 💡 Skills Demonstrated

- Network segmentation and VLAN design
- Zero Trust architecture implementation
- Cisco IOS CLI configuration
- Extended and standard ACL firewall rules
- SSH hardening and RSA key management
- Wireless security configuration
- Centralized security monitoring and SIEM
- Banking compliance — PCI DSS, GLBA, GDPR
- Incident detection through log analysis
- Defense in depth security architecture

---

## 📚 CompTIA Security+ SY0-701 Domains Covered

| Domain | Coverage |
|--------|----------|
| 1.0 General Security Concepts | CIA triad, cryptography, SSH, PKI |
| 2.0 Threats Vulnerabilities and Mitigations | Attack vectors, brute force defense, malware isolation |
| 3.0 Security Architecture | Zero Trust, DMZ, network segmentation, wireless |
| 4.0 Security Operations | AAA, IAM, SIEM, logging, incident detection |
| 5.0 Security Program Management | PCI DSS, GDPR, GLBA compliance controls |

---


## 👤 Author

**Daniel** | Cybersecurity Student 

Building toward a SOC Analyst role through hands-on practical labs.

- 🐙 GitHub: [Daniel-Security](https://github.com/Daniel-Security)
- 💼 LinkedIn: [www.linkedin.com/in/iourkov]

---

*Built as part of a CompTIA Security+ SY0-701 exam preparation program*
