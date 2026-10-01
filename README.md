# cybersecurity-Task1
# Cybersecurity Task 1 - Port Scanning & Risk Analysis

## Nmap Scan Overview
Target IP: `192.168.1.1` (Local Gateway / Router)

## Discovered Ports and Services

| Port | Protocol | State | Service | Service Version / Details |
| :--- | :--- | :--- | :--- | :--- |
| 53 | TCP | Open | DNS | `dnsmasq` |
| 80 | TCP | Open | HTTP | `mini_httpd x.x` |
| 443 | TCP | Open | HTTPS | SSL/TLS (`Airtel-CPE-0001`) |
| 554 | TCP | Open | RTSP | Real-Time Streaming Protocol |
| 8000 | TCP | Open | HTTP-Alt | Secondary Web Service |
| 8443 | TCP | Open | HTTPS-Alt | Secondary SSL Web Service |
| 9010 | TCP | Open | Proprietary | Media/Device Control |
| 10000 | TCP | Open | Webmin/HTTP | Remote Management Interface |
| 49152 | TCP | Open | UPnP | Dynamic Local Service Port |
| 62078 | TCP | Open | UPnP | Dynamic Local Service Port |

---

## Potential Security Risks

1. **Unencrypted HTTP Traffic (Port 80):** Administrative traffic sent over plain HTTP can be intercepted via network sniffing or ARP spoofing.
2. **Exposed Web Management Panels (Ports 80, 443, 8443, 10000):** Multiple management interfaces increase the attack surface if default credentials or outdated software binaries are used.
3. **Unverified TLS Certificates (Port 443):** Self-signed certificates allow traffic encryption but do not prevent Man-in-the-Middle (MitM) impersonation.
4. **RTSP Stream Exposure (Port 554):** Unauthenticated media streaming protocols may allow unauthorized access to local feeds or device status.
5. **Dynamic UPnP Service Ports (Ports 49152, 62078):** UPnP features can bypass strict firewall rules, exposing local services externally without explicit approval.

---

## Defensive Mitigation Recommendations

* Disable unencrypted administrative interfaces (HTTP on Port 80) in favor of strictly enforced HTTPS.
* Change all default system/router administrative passwords to strong, unique passphrases.
* Restrict access to management panels (Ports 443, 8443, 10000) so they are only accessible from trusted IP addresses or dedicated management VLANs.
* Disable UPnP if automatic port forwarding is not strictly required.
