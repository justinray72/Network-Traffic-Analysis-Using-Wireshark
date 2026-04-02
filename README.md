# Network Traffic Analysis Using Wireshark

A hands-on network monitoring project capturing and analyzing real DNS, TCP, and TLS traffic using Wireshark on a Windows environment. Built to develop foundational skills in packet analysis, traffic baselining, and security-focused network investigation.

---

## Tools & Environment

| Item | Details |
|---|---|
| Tool | Wireshark |
| OS | Windows 10/11 |
| Network | Home Wi-Fi (wireless interface) |
| Interface Mode | Monitor mode with administrative privileges |

---

## Objective

Capture live network traffic and analyze it through a security lens — identifying normal protocol behavior, documenting packet-level details, and establishing a baseline for future anomaly detection.

---

## Methodology

1. Launched Wireshark with admin privileges and selected the active Wi-Fi interface
2. Captured ~1 minute of baseline traffic during normal browsing activity (Google, Amazon)
3. Applied sequential display filters to isolate and analyze specific protocol traffic
4. Documented findings for each protocol layer with packet-level observations

---

## Analysis & Findings

### DNS Traffic
- Captured standard DNS queries from local system to external DNS servers 
- Packet sizes ranged from **70–206 bytes**, consistent with normal domain resolution
- All queried domains were legitimate — no anomalous or spoofed DNS behavior observed
- Established a clean DNS baseline for future comparison

**Example packet breakdown:**
```
Source IP:        172.16.x.x
Destination IP:   1.1.1.1
Protocol:         UDP
Source Port:      61762
Destination Port: 53
Query:            A record lookup for www.google.com
Packet Size:      70 bytes
TTL:              128
```

---

### TCP / HTTPS Traffic
- Observed standard SYN/ACK three-way handshakes on **port 443**
- **Zero traffic detected on port 80** — all web communication was encrypted
- Connection patterns were consistent with normal browser behavior

---

### TLS / SNI Analysis
- Analyzed TLS handshakes including Client Hello, Server Hello, and certificate exchanges
- Identified Server Name Indication (SNI) fields revealing destination domains (e.g., `unagi.amazon.com`)
- No unexpected domains, invalid certificates, or malformed handshakes detected

---

## Security Insights

This baseline analysis directly maps to real-world SOC workflows:

- **Baseline Establishment** — Documented normal traffic patterns to enable faster anomaly detection in future investigations
- **Alert Triage** — Packet-level inspection skills help validate SIEM alerts as true vs. false positives
- **Incident Response** — Understanding normal protocol behavior makes it easier to spot C2 communication or data exfiltration
- **Threat Hunting** — Proactive traffic analysis can surface threats that bypass automated detection tools

---

## Skills Demonstrated

- Configuring Wireshark for live capture on a wireless interface
- Applying display filters (`dns`, `tcp.port==443`, `tls`) to isolate traffic types
- Interpreting DNS resolution, TCP three-way handshakes, and TLS encryption at the packet level
- Reading packet headers: source/destination IPs, ports, TTL, packet size, protocol flags
- Establishing traffic baselines to differentiate normal from anomalous behavior

---

## Screenshots

Figure 1: Screenshot of Wireshark with the dns filter applied, highlighting a standard DNS query to Google.
<img width="975" height="337" alt="image" src="https://github.com/user-attachments/assets/f70993ea-b41f-40d1-bdc0-1f0fad7731f1" />
Figure 2: TCP filter in Wireshark showing HTTPS traffic on port 443, illustrating encrypted connections and normal TCP packet behavior.
<img width="975" height="335" alt="image" src="https://github.com/user-attachments/assets/58de3236-23e3-4daf-ab71-db9cee864469" />
Figure 3: TLS filter in Wireshark showing a Client Hello packet and the Server Name Indication (SNI) for unagi.amazon.com, illustrating a secure, encrypted connection to a legitimate domain.
<img width="1067" height="543" alt="image" src="https://github.com/user-attachments/assets/aa34423b-0796-419f-be9e-09867175337c" />







---

## Related Projects

- [Security Monitoring Dashboard Using Splunk](https://github.com/justinray72/Security-Monitoring-Dashboard-Using-Splunk)
- [IT Help Desk Lab Using osTicket](https://github.com/justinray72/IT-Help-Desk-Lab)
