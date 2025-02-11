![snmp-check.png](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/Images/snmp-check.png)

`snmp-check` is a powerful Perl script used for auditing and testing SNMP (Simple Network Management Protocol) devices. It goes beyond simple device discovery and allows you to check for a wide range of security vulnerabilities and misconfigurations in SNMP implementations.

**What `snmp-check` Does:**

`snmp-check` performs various checks on SNMP-enabled devices, including:

* **Default Community Strings:** Checks for the use of default community strings (like `public` or `private`), which are a major security risk.
* **Weak Community Strings:**  Tests against a list of known weak community strings.
* **Open Access:**  Verifies if read or write access is granted to the `public` community.
* **System Information:** Retrieves system information (OS, uptime, etc.).
* **Interface Information:**  Lists network interfaces and their status.
* **Process Information:**  Lists running processes (if accessible).
* **Software Information:**  Retrieves installed software details (if available).
* **Security Checks:**  Performs various security checks based on best practices and known vulnerabilities.
* **Brute-forcing Communities:** Can be used to try a list of community strings.

**Key Features and Capabilities:**

* **Comprehensive SNMP Auditing:**  Performs a wide range of checks.
* **Security Vulnerability Detection:**  Identifies potential security issues.
* **Information Gathering:**  Retrieves detailed system and network information.
* **Scriptable:**  Can be integrated into scripts for automated testing.
* **Extensible:**  New checks can be added to the script.

**How to Use `snmp-check`:**

 **Options:**

   `snmp-check` has many options to control its behavior. Here are some of the most important:

   * `-c <community_string>`: Specify the community string.
   * `-C <community_file>`: Specify a file containing a list of community strings to try (one per line).  Useful for brute-forcing.
   * `-t <timeout>`: Set the timeout for SNMP responses (in seconds).
   * `-p <port>`: Specify the SNMP port (default is 161).
   * `-v`: Verbose output.
   * `-d`: Debug output.
   * `-n`: Do not resolve IP addresses to hostnames.
   * `-h`: Display help message.
   * `-l <level>`: Set the log level (0-3, higher is more verbose).
   * `-f <file>`: Use a file containing a list of targets (one per line).

---

## **Installation**  
If `snmp-check` is not installed, you can install it on Kali Linux and other Debian-based systems using:  

```bash
sudo apt update && sudo apt install snmp-check
```

For other distributions, you may need to download it manually or use a package manager.

---

## **Basic Usage**  

### **1. Scan a Target Device (Default Options)**
```bash
snmp-check 192.168.1.1
```
- Uses the default **SNMP community string** (`public`) and **SNMPv1**.

### **2. Scan with a Custom SNMP Community String**
```bash
snmp-check -c private 192.168.1.1
```
- `-c private` → Uses the **community string** `private`.

### **3. Use SNMP Version 2c Instead of Version 1**
```bash
snmp-check -v 2c -c public 192.168.1.1
```
- `-v 2c` → Uses SNMP **version 2c**.
- `-c public` → Uses the **community string** `public`.

### **4. Specify a Different SNMP Port**
```bash
snmp-check -p 1610 -c public 192.168.1.1
```
- `-p 1610` → Uses **port 1610** instead of the default **161**.

### **5. Check for Write Access**
```bash
snmp-check -w -c public 192.168.1.1
```
- `-w` → Checks if **write access** is allowed (which could be a security risk).

### **6. Disable TCP Enumeration**
```bash
snmp-check -d -c public 192.168.1.1
```
- `-d` → Disables **TCP-based enumeration**, focusing only on **SNMP data**.

### **7. Increase Timeout and Retries**
```bash
snmp-check -t 10 -r 3 -c public 192.168.1.1
```
- `-t 10` → Sets a **timeout** of **10 seconds** (useful for slow networks).
- `-r 3` → Retries failed requests **3 times**.

---

## **Example Output**
```plaintext
============================================================
|  SNMP Enumeration Tool v1.9                              |
|  by Matteo Cantoni (www.nothink.org)                     |
============================================================

Target IP: 192.168.1.1
Community: public

System Information:
-------------------
  Hostname: router.local
  OS: Linux 5.4.0
  Uptime: 15 days, 4:32:15
  Contact: admin@company.com
  Location: Server Room 2

Network Interfaces:
-------------------
  Interface: eth0 - 192.168.1.1
  Interface: wlan0 - 10.0.0.1

Running Processes:
-------------------
  PID  USER   COMMAND
  1    root   init
  101  admin  sshd
  202  apache httpd

Installed Software:
-------------------
  - OpenSSH 8.0
  - Apache 2.4.41
  - MySQL 5.7.32
```

---

## **Why Use `snmp-check`?**
✅ **Easy to use** – Simple command-line tool for SNMP enumeration.  
✅ **Find Misconfigured SNMP** – Helps identify **open SNMP services** with weak community strings (`public`, `private`).  
✅ **Collect Valuable Information** – Extracts **system details, users, network interfaces, running processes, and installed software**.  
✅ **Supports SNMPv1 and SNMPv2c** – Works with different **SNMP versions**.  
✅ **Checks for Write Access** – Identifies **misconfigurations** that allow **unauthorized modifications**.  

---

## **Additional SNMP Enumeration Tools**
You can combine `snmp-check` with other SNMP tools for more detailed scanning:  

### **1. Find Valid SNMP Community Strings (`onesixtyone`)**
```bash
onesixtyone -c community_list.txt -i target_list.txt
```
- **Brute-forces SNMP community strings**.

### **2. Perform a Detailed SNMP Enumeration (`snmpwalk`)**
```bash
snmpwalk -v2c -c public 192.168.1.1
```
- Extracts **detailed SNMP information** using **SNMP OIDs**.

### **3. Enumerate SNMP Information with `snmpenum`**
```bash
snmpenum -t 192.168.1.1 -c public
```
- Extracts **OS details, running services, and network configuration**.

---

**Interpreting the Results:**

`snmp-check` outputs a detailed report of the checks performed, including any vulnerabilities or misconfigurations found. Pay close attention to warnings and errors.

**Important Considerations:**

* **Community Strings:** Default or weak SNMP community strings are a major security vulnerability. `snmp-check` helps identify these.
* **Firewall Considerations:** Firewalls can block SNMP traffic.
* **SNMP Versions:** `snmp-check` works best with SNMPv1 and SNMPv2c. SNMPv3 is more secure.
* **Ethical Use:** Only use `snmp-check` on networks and devices you own or have explicit permission to test. Unauthorized scanning is illegal and unethical.

`snmp-check` is an invaluable tool for network security auditing and identifying SNMP-related vulnerabilities.  It's crucial to use it responsibly and ethically. Always obtain proper authorization before testing any network.  Be aware of the limitations of the tool and the potential for detection.  Keep `snmp-check` (and its database of checks) updated for the latest vulnerabilities.
