# 🏠 Secure Home Office Network Lab 🔒

<p align="center">
  This repository details the architecture and implementation of my network and cybersecurity infrastructure for a <strong>home office</strong> environment. The goal is to demonstrate practical application of security principles to protect a home network, optimize connectivity, and create a robust remote work environment, while also serving as a cybersecurity testing lab.
</p>

---

# 🔒 Project: Security and Network Lab with pfSense + Suricata + Squid

## 📡 Network Setup

**Hypervisor:** VirtualBox  
**Firewall:** pfSense  

| Interface   | Type              | Purpose                          |
|-------------|-------------------|---------------------------------|
| Adapter 1   | NAT               | External access (WAN)            |
| Adapter 2   | Host-only         | Local administration (LAN)       |
| Adapter 3   | Internal Network  | Internal client network (OPT1)   |

---

## ⚙️ pfSense Configuration

### Interfaces
- **WAN:** DHCP via NAT  
- **LAN:** `192.168.56.1/24` (host-only)  
- **OPT1:** `192.168.50.1/24` (internal clients)

### DHCP (on OPT1)
- **Range:** `192.168.50.100 – 192.168.50.200`  
- **DNS Servers:**  
  - `192.168.50.1` (pfSense)  
  - `8.8.8.8`, `1.1.1.1` (external)

### Firewall Rules
- Allow: `OPT1 subnet -> any`  
- Logging: **enabled** for debugging

---

## 🛡️ Suricata IDS/IPS

### Installation
- Installed via **System > Package Manager**

### Monitored Interface
- `OPT1` (internal network)

### Configuration
- **Mode:** Inline IPS  
- **Block Offenders:** ✔️  
- **Auto-enable Flowbits:** ✔️  
- **Pass List created:** `trusted-network`

#### Pass List (Trusted IPs)
- `192.168.50.1` → pfSense gateway  
- `192.168.56.1` → physical host  
- `8.8.8.8`, `1.1.1.1` → external DNS

### Enabled Rule Categories (examples)
- `emerging-malware.rules`  
- `emerging-botcc.rules`  
- `emerging-exploit.rules`  
- `stream-events.rules`  
- `dns-events.rules`  
- `http-events.rules`  

---

## 🌐 Squid Proxy

### Mode: Transparent Proxy
- Interface: `OPT1`  
- Proxy automatically intercepts HTTP requests  
- HTTPS: **not intercepted** (SSL Bump disabled by default)

### ACLs
- Allowed subnet: `192.168.50.0/24`  
- Local cache enabled (100MB)

### Logs
- Local path: `/var/squid/logs/access.log`  
- GUI: `Status > System Logs > Proxy`

---

## ✅ Tests Performed

- Access to HTTP and HTTPS sites via proxy  
- Suricata test using `curl http://testmyids.com`  
- Blocking and unblocking based on Suricata rules  
- Log verification (proxy and IDS)  
- DHCP working with clients browsing without manual config  
- Pass List protecting internal IPs from IPS blocking

---

## 📌 Future Enhancements

- [ ] SquidGuard: category filtering  
- [ ] Lightsquid: graphical access reports  
- [ ] SSL Bump: HTTPS interception and inspection  
- [ ] pfBlockerNG: GeoIP, IP reputation, ASN filtering  
- [ ] User authentication on proxy

---

## 🗂 Repository Structure

/
├── README.md
├── pfsense_config/
│ ├── firewall_rules.txt
│ ├── passlist_conf.txt
│ ├── squid_conf_summary.txt
├── logs/
│ ├── squid_access_sample.log
│ ├── suricata_alerts.log
└── notes/
└── extensions_plan.md


---

## 👨‍💻 Author

> Personal lab for learning and practical implementation of network security using pfSense, Suricata, and Squid Proxy. Ideal for studying IDS/IPS, firewall, transparent proxy, and traffic control in isolated environments.

---

<h2 align="center">📞 Contact</h2>

<p align="center">Feel free to reach out to discuss this project, collaborate, or explore opportunities in cybersecurity.</p>

<p align="center">
  <a href="https://www.linkedin.com/in/julio-melgaco-a80aa7277" target="_blank" rel="noopener noreferrer">
    <img src="https://img.shields.io/badge/LinkedIn-Connect-blue?style=for-the-badge&logo=linkedin" alt="LinkedIn">
  </a>
</p>
