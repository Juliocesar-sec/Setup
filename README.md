# Setup

<h1 align="center">🏠 Secure Home Office Network Lab 🔒</h1>

<p align="center">
This repository details the architecture and implementation of my network and cybersecurity infrastructure for a <strong>home office</strong> environment. My goal is to demonstrate the practical application of security principles to secure a home network, optimize connectivity, and create a robust environment for remote work, as well as serve as a test lab for security. </p>

---

<h2 align="center">🛠️ Architecture and Component Overview</h2>

<p align="center">My setup was designed to provide visibility, control, and resilience using a strategic combination of hardware and software.</p>

### Base Hardware

<ul>
<li><strong>Host Computer:</strong> Lenovo ThinkCentre M93 Tiny</li>
<ul>
<li><em>Function:</em> Compact and efficient server for hosting virtual machines.</li>
</ul>
<li><strong>Internet Access (WAN):</strong> Aquário 4G Rural Internet Modem</li>
<ul>
<li><em>Function:</em> Providing primary connectivity via 4G network.</li>
</ul>
<li><strong>Main Router:</strong> GL.iNet SFT1200 (Slate AX)</li> <ul>
<li><em>Function:</em> Internal network management, routing and advanced features.</li>
</ul>
</ul>

### Software and Virtualization

<ul>
<li><strong>Host Operating System:</strong> Debian 12</li>
<ul>
<li><em>Function:</em> Stable and secure base for virtualization.</li>
<li><em>Virtualization Tool:</em> KVM/libvirt for efficient management of VMs.</li>
</ul>
<li><strong>Firewall and Edge Security (VM):</strong> OPNsense</li>
<ul>
<li><em>Function:</em> Acts as the main firewall and network gateway, controlling all incoming and outgoing traffic.</li>
</ul>
<li><strong>DNS Filtering and Threat Blocking (VM):</strong> Pi-hole</li>
<ul>
<li><em>Function:</em> Network-wide DNS server responsible for filtering ads, trackers, and malicious domains.</li>
</ul>
</ul>

---

<h2 align="center">🔒 Security Implementation Details</h2>

<p align="center">This section describes how each component contributes to the network security posture.</p>

### 1. Firewall and Segmentation with OPNsense

<ul>
<li><strong>Implementation:</strong> OPNsense runs as a dedicated virtual machine on the ThinkCentre M93 Tiny, strategically positioned as the ingress and egress point of the local network.</li>
<li><strong>Demonstrated Capabilities:</strong>
<ul>
<li><strong>Stateful Filtering:</strong> Configure granular firewall rules to allow or block traffic based on IP addresses, ports, protocols, and state. connection.</li>
<li><strong>Network Segmentation:</strong> Creation of VLANs (Virtual Local Area Networks) or virtual interfaces to isolate different types of devices (e.g., work network, IoT device network, guest network), minimizing the impact of a potential breach.</li>
<li><strong>Intrusion Detection/Prevention System (IDS/IPS):</strong> Use of the integrated <strong>Suricata</strong> to monitor traffic in real time, identify known attack patterns, and block suspicious activity.</li>
<li><strong>VPN Server:</strong> Configuration of VPN servers (OpenVPN or WireGuard) to allow secure remote access to the internal network or to tunnel outbound network traffic through an external VPN service, ensuring privacy and security in transit.</li>
<li><strong>Log Management and Auditing:</strong> Monitoring and analyzing logs to identify security events and audit network traffic.</li>
</ul>
</li>
</ul>

### 2. DNS Filtering and Content Control with Pi-hole

<ul>
<li><strong>Implementation:</strong> Pi-hole operates as a separate virtual machine on the ThinkCentre M93 Tiny, configured to be the primary DNS server for all devices on the network.</li>
<li><strong>Demonstrated Capabilities:</strong>
<ul>
<li><strong>Malware and Phishing Blocking:</strong> Using up-to-date blocklists to prevent devices from accessing domains known to host malware, phishing, and other malicious content.</li>
<li><strong>Enhanced Privacy:</strong> Blocking trackers and device telemetry, reducing the digital footprint and protecting the privacy of network users.</li>
<li><strong>DNS Traffic Visibility:</strong> The Pi-hole dashboard provides detailed statistics on DNS queries, allowing you to identify usage patterns, suspicious activities and attempts to access blocked domains.</li>
<li><strong>Performance Optimization:</strong> Reduces processing load and bandwidth by blocking requests for ads and other unwanted content.</li>
</ul>
</li>
</ul>

### 3. Optimized Connectivity and Routing

<ul>
<li><strong>Aquario 4G Rural Internet Modem:</strong> Provides the primary WAN connection, demonstrating adaptability and resilience in environments where fixed broadband may be limited or unavailable.</li>
<li><strong>GL.iNet SFT1200 Router (Slate AX):</strong>
<ul>
<li><strong>Efficient Routing:</strong> Manages traffic between the local network and OPNsense.</li>
<li><strong>Flexibility:</strong> GL.iNet OS, based on OpenWrt, allows advanced network and security configurations.</li>
<li><strong>VPN Client:</strong> Can be configured to function as a VPN client, routing all network traffic through a secure tunnel to a VPN provider, ensuring anonymity and data protection for all connected devices.</li>
</ul>
</li>
</ul>

---

<h2 align="center">🎯 Relevance for Cybersecurity in Home Office</h2>

<p align="center">This setup is particularly relevant for cybersecurity professionals and anyone looking for a secure and efficient remote work environment, as it offers:</p>

<ul>
<li><strong>Defense in Depth:</strong> Multiple layers of security (firewall, DNS filtering) to protect the network.</li>
<li><strong>Control and Transparency:</strong> Ability to proactively monitor, audit, and manage network traffic.</li>
<li><strong>Privacy and Anonymity:</strong> Tools to mitigate trackers and potential integration with VPNs.</li>
<li><strong>Practical Skills:</strong> Demonstrates proficiency in virtualization, open-source firewall configuration, DNS management, and advanced routing – skills highly valued in the cybersecurity market.</li>
<li><strong>Lab Environment:</strong> The setup serves as a platform to test new tools, simulate attacks, and continually improve security capabilities without impacting production networks.</li>
</ul>

---

<h2 align="center">➡️ Next Steps and Future Improvements</h2>

<p align="center">I plan to expand and refine this infrastructure with the following projects:</p>

<ul>
<li><strong>SIEM (Security Information and Event Management) Implementation:</strong> Setting up a solution such as ELK Stack (Elasticsearch, Logstash, Kibana) or Splunk Free to centralize and analyze logs from all security devices.</li>
<li><strong>Honeypot Configuration:</strong> Deploying honeypots to attract and analyze attack attempts, gaining threat intelligence.</li>
<li><strong>Security Task Automation:</strong> Developing scripts (Python/Bash) to automate log collection, alerts, and other tasks. security routines.</li>
<li><strong>Vulnerability Testing:</strong> Periodic vulnerability scans and intrusion tests are performed on the network itself to identify and correct potential flaws.</li>
<li><strong>Detailed Documentation:</strong> Create more in-depth documentation for each service, including more complex network diagrams and step-by-step configuration guides.</li>
</ul>

---

<h2 align="center">📞 Contact</h2>

<p align="center">Feel free to contact me to discuss this project, collaborate, or explore opportunities in the cybersecurity field.</p>

<p align="center">
  <a href="https://www.linkedin.com/in/julio-melgaco-a80aa7277" target="_blank">
  <img src="https://img.shields.io/badge/LinkedIn-Connect-blue?style=for-the-badge&logo=linkedin" alt="LinkedIn">
</p>

---

