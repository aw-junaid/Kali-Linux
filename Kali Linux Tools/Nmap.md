![nmap.png](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/Images/nmap.png)

Nmap (Network Mapper) is a powerful and versatile open-source tool for network discovery and security auditing. It's used to scan networks and hosts to gather information about their structure, services, and vulnerabilities. Nmap is a fundamental tool for network administrators, security professionals, and anyone interested in network exploration.

**What Nmap Does:**

Nmap can be used for a wide range of tasks, including:

* **Host Discovery:** Identifying which hosts are active on a network.
* **Port Scanning:** Determining which ports are open on a target host.
* **Service Version Detection:** Identifying the version of services running on open ports.
* **Operating System Fingerprinting:** Attempting to determine the operating system of the target host.
* **Vulnerability Scanning:** Identifying known vulnerabilities in services.
* **Network Mapping:** Creating a map of the network topology.
* **Firewall Testing:** Testing firewall rules.
* **Security Auditing:** Assessing the security posture of networks and hosts.

**Key Features and Capabilities:**

* **Versatile Scanning Techniques:** Supports various scan types (e.g., TCP SYN scan, TCP connect scan, UDP scan, ICMP ping scan).
* **Port Scanning:** Can scan a wide range of ports.
* **Service Version Detection:** Identifies the version of running services.
* **OS Fingerprinting:** Attempts to determine the target operating system.
* **Scripting:** Supports Nmap Scripting Engine (NSE) for advanced tasks and automation.
* **Output Formats:** Can output results in various formats (e.g., interactive, XML, grepable).
* **Cross-Platform:** Runs on various operating systems (Linux, Windows, macOS).

**How to Use Nmap:**

1. **Basic Usage (TCP SYN scan):**

   ```bash
   nmap <target_host>
   ```

   Replace `<target_host>` with the hostname or IP address of the target. This command performs a basic TCP SYN scan, which is the default scan type.

## The available options and provides examples of usage.

**TARGET SPECIFICATION:**

* Defines how to specify the target(s) for the scan.
* Can use hostnames, IP addresses, networks (CIDR notation), or ranges.
* `-iL <inputfilename>`: Read targets from a file.
* `-iR <num hosts>`: Generate random targets.
* `--exclude <host1[,host2][,host3],...>`: Exclude specific hosts or networks.
* `--excludefile <exclude_file>`: Exclude targets listed in a file.

**HOST DISCOVERY:**

* Options for determining which hosts are online before scanning ports.
* `-sL`: List Scan (only lists targets, doesn't scan).
* `-sn`: Ping Scan (disables port scan, only checks for host availability).
* `-Pn`: Treat all hosts as online (skips host discovery).
* `-PS/PA/PU/PY[portlist]`: TCP SYN/ACK, UDP, or SCTP discovery to specific ports.
* `-PE/PP/PM`: ICMP Echo, Timestamp, and Netmask Request discovery probes.
* `-PO[protocol list]`: IP Protocol Ping.
* `-n/-R`: Never/Always do DNS resolution.
* `--dns-servers <serv1[,serv2],...>`: Specify custom DNS servers.
* `--system-dns`: Use the operating system's DNS resolver.
* `--traceroute`: Trace the route to each host.

**SCAN TECHNIQUES:**

* Specifies the type of port scan to perform.
* `-sS/sT/sA/sW/sM`: TCP SYN/Connect()/ACK/Window/Maimon scans.
* `-sU`: UDP scan.
* `-sN/sF/sX`: TCP Null, FIN, and Xmas scans.
* `--scanflags <flags>`: Customize TCP scan flags.
* `-sI <zombie host[:probeport]>`: Idle scan.
* `-sY/sZ`: SCTP INIT/COOKIE-ECHO scans.
* `-sO`: IP protocol scan.
* `-b <FTP relay host>`: FTP bounce scan.

**PORT SPECIFICATION AND SCAN ORDER:**

* Defines which ports to scan and in what order.
* `-p <port ranges>`: Specify port ranges (e.g., `-p22`, `-p1-65535`, `-p U:53,111,137,T:21-25,80`).
* `--exclude-ports <port ranges>`: Exclude specific ports.
* `-F`: Fast mode (scans fewer ports).
* `-r`: Scan ports sequentially (don't randomize).
* `--top-ports <number>`: Scan the most common ports.
* `--port-ratio <ratio>`: Scan ports based on their commonality.

**SERVICE/VERSION DETECTION:**

* Attempts to determine the version of services running on open ports.
* `-sV`: Enable version detection.
* `--version-intensity <level>`: Set the level of probing (0-9).
* `--version-light`: Limit to the most likely probes (intensity 2).
* `--version-all`: Try every probe (intensity 9).
* `--version-trace`: Show detailed version scan activity.

**SCRIPT SCAN:**

* Allows running Nmap scripts for advanced tasks.
* `-sC`: Equivalent to `--script=default` (runs common scripts).
* `--script=<Lua scripts>`: Specify scripts to run (comma-separated list).
* `--script-args=<n1=v1,[n2=v2,...]>`: Provide arguments to scripts.
* `--script-args-file=filename`: Provide script arguments from a file.
* `--script-trace`: Show all data sent and received by scripts.
* `--script-updatedb`: Update the script database.
* `--script-help=<Lua scripts>`: Show help for specific scripts.

**OS DETECTION:**

* Attempts to identify the operating system of the target.
* `-O`: Enable OS detection.
* `--osscan-limit`: Limit OS detection to promising targets.
* `--osscan-guess`: Guess the OS more aggressively.

**TIMING AND PERFORMANCE:**

* Options to control the speed and timing of the scan.
* `-T<0-5>`: Set timing template (higher number is faster, but less accurate).
* `--min-hostgroup/max-hostgroup <size>`: Parallel host scan group sizes.
* `--min-parallelism/max-parallelism <numprobes>`: Probe parallelization.
* `--min-rtt-timeout/max-rtt-timeout/initial-rtt-timeout <time>`: Round trip time settings.
* `--max-retries <tries>`: Maximum retransmissions.
* `--host-timeout <time>`: Timeout for each host.
* `--scan-delay/--max-scan-delay <time>`: Delay between probes.
* `--min-rate/--max-rate <number>`: Minimum/Maximum sending rate (packets per second).

**FIREWALL/IDS EVASION AND SPOOFING:**

* Techniques to avoid detection or hide the source of the scan.
* `-f; --mtu <val>`: Fragment packets.
* `-D <decoy1,decoy2[,ME],...>`: Use decoys.
* `-S <IP_Address>`: Spoof source address.
* `-e <iface>`: Use specified interface.
* `-g/--source-port <portnum>`: Use given source port.
* `--proxies <url1,[url2],...>`: Use HTTP/SOCKS4 proxies.
* `--data <hex string>`/`--data-string <string>`/`--data-length <num>`: Custom payload options.
* `--ip-options <options>`: Specify IP options.
* `--ttl <val>`: Set IP time-to-live.
* `--spoof-mac <mac address/prefix/vendor name>`: Spoof MAC address.
* `--badsum`: Send packets with a bogus checksum.

**OUTPUT:**

* Options for saving scan results in various formats.
* `-oN/-oX/-oS/-oG <file>`: Normal, XML, s|<rIpt kIddi3, and Grepable output.
* `-oA <basename>`: Output in all three major formats.
* `-v`: Increase verbosity.
* `-d`: Increase debugging level.
* `--reason`: Display the reason for a port's state.
* `--open`: Only show open ports.
* `--packet-trace`: Show all packets.
* `--iflist`: Print interfaces and routes.
* `--append-output`: Append to output files.
* `--resume <filename>`: Resume a scan.
* `--noninteractive`: Disable runtime interactions.
* `--stylesheet <path/URL>`/`--webxml`/`--no-stylesheet`: Stylesheet options for XML output.

**MISC:**

* Other miscellaneous options.
* `-6`: Enable IPv6 scanning.
* `-A`: Enable OS detection, version detection, script scanning, and traceroute.
* `--datadir <dirname>`: Custom Nmap data directory.
* `--send-eth/--send-ip`: Use raw ethernet frames or IP packets.
* `--privileged/--unprivileged`: Assume privileged/unprivileged user.
* `-V`: Print version number.
* `-h`: Print this help message.

## **📌 Basic Nmap Commands**
### **1️⃣ Scan a Single Host**
```bash
nmap 192.168.1.1
```
🔹 Performs a **basic scan** to find open ports.

### **2️⃣ Scan Multiple Hosts**
```bash
nmap 192.168.1.1 192.168.1.2 192.168.1.3
```
🔹 Scans multiple IPs.

### **3️⃣ Scan an Entire Network**
```bash
nmap 192.168.1.0/24
```
🔹 Scans all **256 hosts** in `192.168.1.x`.

### **4️⃣ Scan a Specific Port**
```bash
nmap -p 80 192.168.1.1
```
🔹 Checks if **port 80** (HTTP) is open.

### **5️⃣ Scan a Range of Ports**
```bash
nmap -p 1-1000 192.168.1.1
```
🔹 Scans ports **1 to 1000**.

### **6️⃣ Scan All 65,535 Ports**
```bash
nmap -p- 192.168.1.1
```
🔹 **Comprehensive scan** of all TCP ports.

---

## **🔬 Advanced Scanning Techniques**
### **7️⃣ TCP SYN Scan (Stealth Scan)**
```bash
nmap -sS 192.168.1.1
```
🔹 Uses **half-open** TCP connections to avoid detection.

### **8️⃣ UDP Scan**
```bash
nmap -sU 192.168.1.1
```
🔹 Checks for open **UDP** ports.

### **9️⃣ Detect OS and Services**
```bash
nmap -A 192.168.1.1
```
🔹 `-A` enables:
✅ OS detection  
✅ Service version detection  
✅ Traceroute  
✅ Script scanning  

### **🔟 Aggressive Scan**
```bash
nmap -A -T4 192.168.1.1
```
🔹 `-T4` makes scanning **faster**, but more **detectable**.

---

## **📂 Output and Saving Results**
### **11️⃣ Save Scan Results (Text)**
```bash
nmap -oN scan_results.txt 192.168.1.1
```
🔹 Saves output to `scan_results.txt`.

### **12️⃣ Save Scan Results (XML)**
```bash
nmap -oX scan_results.xml 192.168.1.1
```
🔹 Saves output in **XML format** for further processing.

---

## **🛠️ Special Scans**
### **13️⃣ Scan for Specific Services**
```bash
nmap -p 22,80,443 --open 192.168.1.1
```
🔹 Finds **only open** SSH (22), HTTP (80), and HTTPS (443).

### **14️⃣ Firewall Evasion**
```bash
nmap -f -D RND:10 192.168.1.1
```
🔹 `-f` → **Fragment packets** (bypass IDS/IPS).  
🔹 `-D RND:10` → **Decoy scan** using 10 fake IPs.

### **15️⃣ Scan for Vulnerabilities**
```bash
nmap --script vuln 192.168.1.1
```
🔹 Runs **vulnerability detection scripts**.

---

## **🎯 Nmap Cheat Sheet**
| **Command** | **Description** |
|------------|---------------|
| `nmap -sS` | TCP SYN scan (stealth) |
| `nmap -sU` | UDP scan |
| `nmap -A` | OS & service detection |
| `nmap -T4` | Faster scanning |
| `nmap -p-` | Scan all ports |
| `nmap --script vuln` | Run vulnerability scans |
| `nmap -oX output.xml` | Save results in XML |


**Interpreting the Results:**

Nmap's output shows information about open ports, services detected, operating systems, and other details. The specific information displayed depends on the options used.

**Important Considerations:**

* **Ethical Use:** Only use Nmap on networks that you own or have explicit permission to scan. Unauthorized scanning is illegal and unethical.
* **Rate Limiting:** Be careful with scan intensity and rate. Avoid overwhelming the target network.
* **Accuracy:** Nmap's results are not always 100% accurate. Consider using multiple tools and techniques.
* **Firewall Evasion:**  Nmap provides techniques to evade firewalls, but these should only be used for ethical testing.
* **Legal Issues:** Scanning networks without permission can lead to legal issues. Be aware of the laws in your jurisdiction.

Nmap is an essential tool for network administrators and security professionals.  It's powerful, flexible, and widely used for network discovery and security auditing.  However, it's crucial to use it responsibly and ethically.  Always prioritize obtaining proper authorization before scanning any network. Be mindful of the potential impact on target networks and use the tool carefully.
