![masscan.png](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/Images/masscan.png)

`masscan` is a very fast port scanner. It's designed to scan the entire Internet (or large portions of it) much more quickly than traditional port scanners like Nmap.  While Nmap is excellent for in-depth scans of individual hosts or small networks, `masscan` excels at large-scale scans where speed is paramount.

**What `masscan` Does:**

`masscan` sends SYN packets (the first part of the TCP three-way handshake) to a large number of IP addresses and ports. It listens for SYN-ACK responses, which indicate that the port is open.  Because it's optimized for speed, it doesn't perform the full TCP handshake by default (unless you specifically configure it to).  This makes it faster but also means it's less thorough than a full TCP connect scan.

**Key Features and Capabilities:**

* **Speed:**  `masscan` is designed for extremely fast scanning of massive address spaces. It can scan the entire Internet in a matter of hours (depending on network conditions and available bandwidth).
* **Flexibility:**  While it's known for speed, `masscan` also offers options to control the scan rate, target specific ports, and even perform full TCP handshakes.
* **Output:**  `masscan` can output results in various formats, making it easy to integrate with other tools.

**How to Use `masscan`:**

 **Basic Usage:**

   ```bash
   masscan <target_range> -p <port_range>
   ```

   * `<target_range>`: Specifies the IP address range to scan. You can use CIDR notation (e.g., `192.168.0.0/16`) or a range of IP addresses (e.g., `192.168.0.1-192.168.255.255`).
   * `-p <port_range>`: Specifies the port range to scan (e.g., `-p 80,443,8080` or `-p 1-1024`).
This shows example usages of the `masscan` command and clarifies some of its features. Let's break down each example:

**1. `masscan -p80,8000-8100 10.0.0.0/8 --rate=10000`**

* `masscan`: The command to run the tool.
* `-p80,8000-8100`:  Specifies the port range to scan. This example scans port 80 and ports 8000 through 8100.
* `10.0.0.0/8`: Specifies the target IP address range using CIDR notation. This scans all IP addresses in the 10.0.0.0/8 network (a very large private IP address range).
* `--rate=10000`: Sets the sending rate to 10,000 packets per second. This is a relatively high rate and should be used with caution.

This command scans a large private IP range for common web ports (80 and 8000-8100) at a rate of 10,000 packets per second.  It's a fast way to discover web servers within that network.

**2. `masscan --nmap`**

* `masscan`: The command to run the tool.
* `--nmap`: This option lists all the `masscan` options that are compatible with Nmap. This is helpful if you're familiar with Nmap and want to use similar options in `masscan`.  It helps bridge the gap between the two tools.

This command doesn't actually perform a scan. It just displays a list of options that `masscan` and Nmap have in common.

**3. `masscan -p80 10.0.0.0/8 --banners -oB <filename>`**

* `masscan`: The command to run the tool.
* `-p80`: Scans port 80.
* `10.0.0.0/8`: Specifies the target IP address range.
* `--banners`: This option tells `masscan` to retrieve banners from open ports.  This means it will perform a full TCP handshake to establish a connection and receive any data sent by the service running on port 80.  This is slower than a SYN scan but provides more information.
* `-oB <filename>`: Saves the results in a binary format to the specified `<filename>`. This binary format is efficient for storing large scan results.

This command scans the specified IP range for web servers (port 80), retrieves banners from open ports, and saves the results in a binary file.

**4. `masscan --open --banners --readscan <filename> -oX <savefile>`**

* `masscan`: The command to run the tool.
* `--open`: This option filters the results to only show open ports.
* `--banners`: Retrieves banners (required because the original scan used `--banners`).
* `--readscan <filename>`: Reads the scan results from the binary file specified by `<filename>`. This is how you process the results saved with the `-oB` option.
* `-oX <savefile>`: Saves the processed results in XML format to `<savefile>`.  This makes the results more readable and easier to parse with other tools.

This command reads the binary scan results from the file created in the previous example, filters for open ports, retrieves banners (if they weren't already captured), and then saves the results in XML format.  This allows you to analyze the scan data in a more user-friendly format.

### **Masscan Usage Examples & Options** 🚀  

## **📌 Basic Scanning Examples**  

### **1️⃣ Scan Web Ports on a Large Network (10,000 packets per second)**
```bash
sudo masscan -p80,8000-8100 10.0.0.0/8 --rate=10000
```
🔹 Scans **ports 80, 8000-8100** on all `10.x.x.x` IPs  
🔹 `--rate=10000`: **Adjust** to avoid network congestion  

---

### **2️⃣ List Options Compatible with Nmap**
```bash
masscan --nmap
```
🔹 Shows **compatible** Nmap-style options  

---

### **3️⃣ Save Scan Results in Binary Format**
```bash
sudo masscan -p80 10.0.0.0/8 --banners -oB scan_results.bin
```
🔹 `-oB scan_results.bin`: Saves results in **binary** format  
🔹 `--banners`: Captures **server banners** (e.g., HTTP headers)  

---

### **4️⃣ Convert Binary Scan Results to XML**
```bash
sudo masscan --open --banners --readscan scan_results.bin -oX results.xml
```
🔹 Reads the **binary scan results** and converts them to **XML format**  
🔹 `--open`: Only saves **open** ports  
🔹 `-oX results.xml`: Saves output as **XML**  

---

## **📡 Advanced Scanning Techniques**  

### **5️⃣ Scan with a Spoofed Source IP (Evasion)**
```bash
sudo masscan -p22 192.168.1.0/24 --source-ip 192.168.1.100
```
🔹 Uses **192.168.1.100** as the **spoofed** source IP  
⚠️ **Requires root and may trigger firewall rules**  

---

### **6️⃣ Scan Using a Specific Network Interface**
```bash
sudo masscan -p80 192.168.1.0/24 --interface eth0
```
🔹 Ensures **masscan** uses `eth0` for sending packets  

---

### **7️⃣ Scan Only Live Hosts (Avoid Wasting Time on Inactive Devices)**
```bash
sudo masscan -p80 192.168.1.0/24 --ping
```
🔹 Sends **ICMP ping** before scanning  

---

### **8️⃣ Exclude Specific IPs**
```bash
sudo masscan -p22,80,443 10.0.0.0/8 --exclude 10.0.0.1,10.0.0.2
```
🔹 Skips **specific IPs** from scanning  

---

## **📊 Saving & Processing Results**
| Format  | Command |
|---------|---------|
| Binary  | `-oB results.bin` |
| XML     | `-oX results.xml` |
| JSON    | `-oJ results.json` |
| Grepable | `-oG results.txt` |

---

**Important Considerations:**

* **Ethical Use:**  Only use `masscan` on networks that you own or have explicit permission to scan.  Unauthorized scanning is illegal and unethical.  Scanning the entire Internet without permission is especially problematic.
* **Rate Limiting:**  Be very careful with the `--rate` option.  Setting it too high can overwhelm the target network and cause a denial-of-service condition.  Start with a low rate and gradually increase it if necessary.
* **Legal Issues:**  Scanning large portions of the Internet without permission can lead to legal consequences.  Be aware of the laws and regulations in your jurisdiction.
* **Accuracy:**  `masscan`'s default SYN scan is very fast but might not be as accurate as a full TCP connect scan.  If you need more accurate results, use the `--banners` option (which will be much slower) or combine `masscan` with Nmap for in-depth scanning of identified hosts.
* **Root Privileges:** `masscan` typically requires root privileges to send raw packets.  You'll often need to use `sudo`.

`masscan` is a powerful tool for large-scale network scanning, but it should be used responsibly and ethically.  Always prioritize obtaining proper authorization before scanning any network.  Be mindful of the potential impact on target networks and use the `--rate` option carefully.
