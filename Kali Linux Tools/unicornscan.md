![unicornscan.png](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/Images/unicornscan.png)

`unicornscan` is a network reconnaissance and security testing tool. It's designed to be asynchronous, meaning it can handle a large number of concurrent connections and scans very efficiently.  It's often used for tasks like port scanning, service identification, and network mapping.

**What `unicornscan` Does:**

`unicornscan` is capable of performing various network scans, including:

* **TCP SYN scans:**  The most common type of port scan, used to determine if ports are open.
* **TCP connect scans:**  A more thorough scan that completes the three-way TCP handshake.
* **UDP scans:**  Used to discover open UDP ports.
* **Service version detection:**  Identifies the version of services running on open ports.
* **Operating system fingerprinting:**  Tries to determine the operating system of the target host.
* **Network mapping:**  Discovers hosts and network topology.
* **HTTP/HTTPS probing:**  Retrieves information from web servers.

**Key Features and Capabilities:**

* **Asynchronous operation:**  Handles many concurrent connections efficiently.
* **Modular design:**  Allows for customization and extension.
* **Scripting support:**  Can be extended with custom scripts.
* **Various scan types:**  Supports TCP, UDP, and other protocols.
* **Service identification:**  Detects service versions.
* **OS fingerprinting:**  Attempts to determine the target OS.

**How to Use `unicornscan`:**

**Basic Usage:**

```bash
unicornscan [options] X.X.X.X/YY:S-E
```

* `unicornscan`: The command to execute the tool.
* `[options]`: Flags and parameters to customize the scan.
* `X.X.X.X/YY:S-E`: The target specification.
    * `X.X.X.X/YY`:  The target IP address range in CIDR notation (e.g., `192.168.1.0/24`). If the CIDR mask is omitted, `/32` (a single host) is assumed.
    * `:S-E`: The port range to scan (e.g., `1-4096`, `53`, `a` for all 65k ports, `p` for 1-1024).

### **Unicornscan Options Breakdown**

#### **General Options**
- `-b, --broken-crc`: Set broken CRC sums on the Transport layer (`T`), Network layer (`N`), or both (`TN`).
- `-B, --source-port`: Set the source port for the scan.
- `-c, --proc-duplicates`: Process duplicate replies.
- `-d, --delay-type`: Set the delay type (numeric value: `1` for TSC, `2` for GTOD, `3` for sleep).
- `-D, --no-defpayload`: Disable the default payload; only probe known protocols.
- `-e, --enable-module`: Enable specific modules (e.g., output and report modules).
- `-E, --proc-errors`: Process non-open responses (e.g., ICMP errors, TCP RSTs).
- `-F, --try-frags`: Attempt to fragment packets.
- `-G, --payload-group`: Specify the payload group for TCP/UDP payload selection (default is all).
- `-h, --help`: Display help information.
- `-H, --do-dns`: Resolve hostnames during the reporting phase.
- `-i, --interface`: Specify the network interface to use (e.g., `eth0`).
- `-I, --immediate`: Enable immediate mode; display results as they are found.
- `-j, --ignore-seq`: Ignore sequence numbers for TCP header validation (`A` for all, `R` for reset).
- `-l, --logfile`: Write output to a specified log file instead of the terminal.
- `-L, --packet-timeout`: Set the timeout for waiting for packets (default is 7 seconds).
- `-m, --mode`: Specify the scan mode:
  - `T` for TCP SYN scan (default).
  - `U` for UDP scan.
  - `sf` for TCP connect scan.
  - `A` for ARP scan.
  - You can also specify TCP flags after `T` (e.g., `-mTsFpU` sends TCP SYN packets with specific flags).
- `-M, --module-dir`: Specify the directory where modules are located (default is `/usr/lib/unicornscan/modules`).
- `-o, --format`: Specify the output format for replies (see the man page for details).
- `-p, --ports`: Specify global ports to scan (if not specified in target options).
- `-P, --pcap-filter`: Add an extra PCAP filter string for the receiver.
- `-q, --covertness`: Set covertness value (0 to 255).
- `-Q, --quiet`: Disable output to the screen (useful for logging to a file or database).
- `-r, --pps`: Set the packets per second (PPS) rate (total, not per host).
- `-R, --repeats`: Repeat the packet scan N times.
- `-s, --source-addr`: Set the source address for packets (`r` for random).
- `-S, --no-shuffle`: Disable port shuffling.
- `-t, --ip-ttl`: Set the TTL (Time to Live) for sent packets (e.g., `62`, `6-16`, or `r64-128`).
- `-T, --ip-tos`: Set the TOS (Type of Service) for sent packets.
- `-u, --debug`: Set the debug mask.
- `-U, --no-openclosed`: Do not display "open" or "closed" status.
- `-w, --safefile`: Write a PCAP file of received packets.
- `-W, --fingerprint`: Perform OS fingerprinting:
  - `0` = Cisco (default).
  - `1` = OpenBSD.
  - `2` = Windows XP.
  - `3` = p0fsendsyn.
  - `4` = FreeBSD.
  - `5` = Nmap.
  - `6` = Linux.
  - `7` = StrangeTCP.
- `-v, --verbose`: Enable verbose output (use multiple `-v` for increased verbosity).
- `-V, --version`: Display the version of Unicornscan.
- `-z, --sniff`: Enable sniffing mode.
- `-Z, --drone-str`: Specify a drone string.

---

### **Address and Port Ranges**
- **Address Ranges**: Use CIDR notation (e.g., `192.168.1.0/24` for all IPs in the range `192.168.1.0` to `192.168.1.255`).
- **Port Ranges**: Use `1-4096` for a range or `53` for a single port. Special options:
  - `a` = All 65,535 ports.
  - `p` = Ports 1-1024.


---

## **🚀 Basic Unicornscan Commands**
### **1️⃣ TCP SYN Scan (Default Mode)**
```bash
unicornscan -mT 192.168.1.0/24
```
🔹 Scans all hosts in `192.168.1.0/24` using **TCP SYN scan**  

---

### **2️⃣ UDP Scan**
```bash
unicornscan -mU 192.168.1.1
```
🔹 Scans UDP ports on **192.168.1.1**  

---

### **3️⃣ Scan Specific Ports**
#### **Scan Port 80**
```bash
unicornscan -p80 192.168.1.1
```
#### **Scan Multiple Ports (22, 80, 443)**
```bash
unicornscan -p22,80,443 192.168.1.1
```
#### **Scan Port Range (1-1000)**
```bash
unicornscan -p1-1000 192.168.1.1
```

---

### **4️⃣ Scan at High Speed**
```bash
unicornscan -p1-10000 -r 10000 192.168.1.1
```
🔹 `-r 10000` → Sends **10,000 packets per second**  

---

### **5️⃣ Scan with Source Spoofing**
```bash
unicornscan -p80 -s 10.0.0.1 192.168.1.1
```
🔹 `-s 10.0.0.1` → **Spoof source IP** (use with caution!)  

---

### **6️⃣ OS Fingerprinting**
```bash
unicornscan -W 3 192.168.1.1
```
🔹 `-W 3` → Uses **Windows XP fingerprinting method**  

---

### **7️⃣ Save Scan Results**
#### **Save as Plain Text**
```bash
unicornscan -mT 192.168.1.1 > results.txt
```
#### **Save as PCAP (for Wireshark)**
```bash
unicornscan -w scan.pcap -mT 192.168.1.1
```

---

## **📌 Advanced Options**
| **Option** | **Description** |
|------------|---------------|
| `-mT` | TCP SYN scan |
| `-mU` | UDP scan |
| `-p` | Specify ports (single, range, or multiple) |
| `-r` | Packets per second (speed control) |
| `-s` | Spoof source IP |
| `-W` | OS fingerprinting |
| `-w` | Save packets to PCAP file |

---

## **⚠️ Ethical Usage Warning**
🚨 **Only scan networks you have permission to test!**  
🚔 Unauthorized scanning can get you **banned or arrested**.  

💡 **Best Practice:** Use Unicornscan in a **lab environment** or **pentesting engagement**.  

---

## **🔹 TL;DR - Quick Cheatsheet**
🔹 **Basic TCP scan:**  
```bash
unicornscan -mT 192.168.1.1
```
🔹 **Scan multiple ports:**  
```bash
unicornscan -p22,80,443 192.168.1.1
```
🔹 **High-speed scan:**  
```bash
unicornscan -p1-10000 -r 10000 192.168.1.1
```
🔹 **UDP scan:**  
```bash
unicornscan -mU -p53 192.168.1.1
```
🔹 **Save results:**  
```bash
unicornscan -mT 192.168.1.1 > scan.txt
```

**Interpreting the Results:**

`unicornscan` will display information about open ports, services detected, OS fingerprints, and other relevant details.  The output format can be customized using various options.

**Important Considerations:**

* **Ethical Use:** Only use `unicornscan` on networks that you own or have explicit permission to scan.  Unauthorized scanning is illegal and unethical.
* **Rate Limiting:** Be careful with the `-r` option.  Setting the rate too high can overwhelm the target network and cause a denial-of-service condition.  Start with a low rate and gradually increase it if necessary.
* **Accuracy:** While `unicornscan` is a powerful tool, its results are not always definitive.  Consider using other tools like Nmap for more in-depth scans.
* **Root Privileges:** `unicornscan` often requires root privileges to send raw packets.  You might need to use `sudo`.

`unicornscan` is a valuable tool for network reconnaissance and security testing.  Its asynchronous design makes it very efficient for scanning large networks.  However, it's essential to use it responsibly and ethically.  Always prioritize obtaining proper authorization before scanning any network.  Be mindful of the potential impact on target networks and use the tool carefully.
