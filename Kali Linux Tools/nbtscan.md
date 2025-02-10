![nbtscan.png](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/Images/nbtscan.png)

**nbtscan** is a command-line tool used to scan IP networks for **NetBIOS** information. NetBIOS (Network Basic Input/Output System) is a protocol that allows applications on separate computers to communicate over a local area network (LAN). It is commonly used in Windows networks for file and printer sharing, as well as for name resolution.

`nbtscan` retrieves NetBIOS information from devices on a network, such as:
- **NetBIOS Name**: The name of the computer.
- **NetBIOS Service**: The services running on the device (e.g., file sharing, domain controller).
- **MAC Address**: The physical address of the network interface.
- **IP Address**: The IP address of the device.

This tool is particularly useful for network administrators to discover and troubleshoot devices on a Windows-based network.

---

### **Key Features of nbtscan**
1. **Fast Scanning**: Quickly scans IP ranges for NetBIOS information.
2. **Cross-Platform**: Works on Linux, Windows, and macOS.
3. **No Authentication Required**: Does not require credentials to scan devices.
4. **Output Formats**: Provides human-readable and machine-readable output.

---

### **Installation**
#### On Linux:
- Install via package manager:
  ```bash
  sudo apt install nbtscan  # Debian/Ubuntu
  sudo yum install nbtscan  # CentOS/RHEL
  ```

#### On Windows:
- Download the precompiled binary from the official website or GitHub.

#### On macOS:
- Install via Homebrew:
  ```bash
  brew install nbtscan
  ```

---

### **Basic Usage**
The general syntax is:
```bash
nbtscan [options] target
```
- `target` can be a single IP address, a range of IP addresses, or a subnet.

**Options:**

* `-v`: Verbose output. Prints all NetBIOS names received from each host.
* `-d`: Dump packets. Prints the contents of the entire packet.  Useful for debugging.
* `-e`: Format output in `/etc/hosts` format.
* `-l`: Format output in `lmhosts` format.  Cannot be used with `-v`, `-s`, or `-h`.
* `-t timeout`: Set the timeout (in milliseconds) for responses. Default is 1000 (1 second).
* `-b bandwidth`: Output throttling. Slows down output to use no more than the specified bandwidth (in bps). Useful for slow links.
* `-r`: Use local port 137 for scans. Some older Windows systems (Win95) only respond to queries on this port. Requires root privileges on Unix-like systems.
* `-q`: Suppress banners and error messages (quiet mode).
* `-s separator`: Script-friendly output.  Doesn't print headers; separates fields with the specified `separator`.
* `-h`: Print human-readable names for services. Can only be used with the `-v` option.
* `-m retransmits`: Number of retransmits. Default is 0.
* `-f filename`: Take IP addresses to scan from the specified `filename`.  `-f -` reads IP addresses from standard input (stdin).
* `<scan_range>`: Specifies the IP address range to scan. Can be a single IP address (e.g., `192.168.1.1`) or a range in one of two formats:
    * `xxx.xxx.xxx.xxx/xx` (CIDR notation, e.g., `192.168.1.0/24`)
    * `xxx.xxx.xxx.xxx-xxx` (IP range, e.g., `192.168.1.25-137`)


### **Examples**

1. **Scan a Single IP Address**:
   ```bash
   nbtscan 192.168.1.10
   ```
   Output:
   ```
   Doing NBT name scan for addresses from 192.168.1.10

   IP address       NetBIOS Name     Server    User             MAC address      
   ------------------------------------------------------------------------------
   192.168.1.10     MY-PC           <server>  <unknown>        00:1A:2B:3C:4D:5E
   ```

2. **Scan a Range of IP Addresses**:
   ```bash
   nbtscan 192.168.1.1-192.168.1.254
   ```
   Output:
   ```
   Doing NBT name scan for addresses from 192.168.1.1-192.168.1.254

   IP address       NetBIOS Name     Server    User             MAC address      
   ------------------------------------------------------------------------------
   192.168.1.1      ROUTER           <server>  <unknown>        00:11:22:33:44:55
   192.168.1.10     MY-PC            <server>  <unknown>        00:1A:2B:3C:4D:5E
   ```

3. **Scan a Subnet**:
   ```bash
   nbtscan 192.168.1.0/24
   ```
   Output:
   ```
   Doing NBT name scan for addresses from 192.168.1.0/24

   IP address       NetBIOS Name     Server    User             MAC address      
   ------------------------------------------------------------------------------
   192.168.1.1      ROUTER           <server>  <unknown>        00:11:22:33:44:55
   192.168.1.10     MY-PC            <server>  <unknown>        00:1A:2B:3C:4D:5E
   ```

4. **Verbose Output**:
   ```bash
   nbtscan -v 192.168.1.10
   ```
   Output:
   ```
   Doing NBT name scan for addresses from 192.168.1.10

   Sending query to 192.168.1.10
   Received answer from 192.168.1.10

   IP address       NetBIOS Name     Server    User             MAC address      
   ------------------------------------------------------------------------------
   192.168.1.10     MY-PC            <server>  <unknown>        00:1A:2B:3C:4D:5E
   ```

5. **Read Targets from a File**:
   ```bash
   nbtscan -f targets.txt
   ```
   (Scans IP addresses listed in `targets.txt`.)

6. **Use a Custom Separator**:
   ```bash
   nbtscan -s ";" 192.168.1.10
   ```
   Output:
   ```
   192.168.1.10;MY-PC;<server>;<unknown>;00:1A:2B:3C:4D:5E
   ```

---

### **Output Fields**
- **IP Address**: The IP address of the device.
- **NetBIOS Name**: The name of the device.
- **Server**: Indicates if the device is a server.
- **User**: The logged-in user (if available).
- **MAC Address**: The physical address of the device.

---

### **Use Cases**
1. **Network Discovery**:
   - Identify devices on a network and their NetBIOS names.
2. **Troubleshooting**:
   - Diagnose connectivity issues in Windows networks.
3. **Security Audits**:
   - Detect unauthorized devices or services on the network.
4. **Inventory Management**:
   - Maintain a list of devices and their NetBIOS information.

---

### **Limitations**
- **Windows Firewall**: Devices with firewalls may block NetBIOS requests.
- **IPv6**: `nbtscan` only works with IPv4 addresses.
- **NetBIOS Dependency**: Devices must have NetBIOS enabled to respond to scans.

---

### **Summary**
`nbtscan` is a simple yet powerful tool for scanning and retrieving NetBIOS information from devices on a network. It is particularly useful in Windows environments for network discovery, troubleshooting, and security audits. By understanding its usage and options, you can effectively manage and monitor devices on your network.
