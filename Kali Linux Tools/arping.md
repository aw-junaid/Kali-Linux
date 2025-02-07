![arping](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/Images/arping.png)

`arping` is a command-line utility used to probe network devices by sending ARP (Address Resolution Protocol) requests. Unlike the standard `ping` command, which uses ICMP (Internet Control Message Protocol), `arping` operates at Layer 2 (Data Link Layer) of the OSI model, making it useful for discovering hosts on the same local network segment, even if they are blocking ICMP traffic.

* **Host Discovery:** Identifying active devices on the local network.
* **Checking Network Connectivity:** Verifying if a device is reachable on the local network.
* **MAC Address Resolution:** Discovering the MAC address associated with a given IP address.
* **Duplicate IP Detection:** Identifying if multiple devices are using the same IP address. (If you receive replies from multiple MAC addresses for the same IP, it indicates a duplicate IP conflict).

**How to Use `arping`:**

 **Basic Usage:**

   ```bash
   arping <target_ip_address>
   ```

   Replace `<target_ip_address>` with the IP address of the device you want to probe (e.g., `192.168.1.100`).

### **Common Options**

1. **General Options**:
   - `-0`: Use the null MAC address (00:00:00:00:00:00) as the source MAC address.
   - `-a`: Audible ping (beep when a reply is received).
   - `-A`: Send ARP replies instead of requests (used for testing ARP behavior).
   - `-b`: Send only Layer 2 broadcasts (default is to send unicast ARP requests).
   - `-d`: Detect duplicate IP addresses (exit with 1 if a duplicate is found).
   - `-D`: Display the MAC address of the sender.
   - `-e`: Show the MAC address of the sender in the output.
   - `-F`: Enable "fuzzy" mode (ignore some errors).
   - `-p`: Send ARP probes (used for duplicate address detection).
   - `-P`: Send ARP replies instead of requests.
   - `-q`: Quiet mode (minimal output).
   - `-r`: Raw output (only show the MAC address of the target).
   - `-R`: Reverse mode (send ARP requests to the broadcast address).
   - `-u`: Update the local ARP cache with the received reply.
   - `-U`: Send unsolicited ARP replies (used to update ARP caches on other devices).
   - `-v`: Verbose mode (more detailed output).
   - `-z`: Enable zero-verification mode (ignore some checks).

2. **Timing Options**:
   - `-w <sec>`: Set the timeout in seconds to wait for a reply.
   - `-W <sec>`: Set the delay between ARP requests in seconds.

3. **Source and Target Options**:
   - `-S <host/ip>`: Specify the source IP address to use in the ARP request.
   - `-T <host/ip>`: Specify the target IP address to use in the ARP request.
   - `-s <MAC>`: Specify the source MAC address to use in the ARP request.
   - `-t <MAC>`: Specify the target MAC address to use in the ARP request.

4. **Count Options**:
   - `-c <count>`: Stop after sending a specified number of ARP requests.
   - `-C <count>`: Stop after receiving a specified number of replies.

5. **Interface and Network Options**:
   - `-i <interface>`: Specify the network interface to use (e.g., `eth0`, `wlan0`).
   - `-m <type>`: Specify the ARP message type (e.g., `request`, `reply`).
   - `-g <group>`: Specify the multicast group to use.
   - `-V <vlan>`: Specify the VLAN ID to use.
   - `-Q <priority>`: Specify the 802.1p priority level.

6. **Miscellaneous**:
   - `<host/ip/MAC>`: The target host, IP address, or MAC address to send ARP requests to.
   - `-B`: Use the broadcast address as the target.

---

## **Basic Usage**  

### **1. Send ARP requests to a target IP**  
```bash
arping -c 5 -I eth0 192.168.1.1
```
- `-c 5` → Send **5 ARP packets** and stop.  
- `-I eth0` → Use the **interface eth0** (replace with `wlan0` for WiFi).  

### **2. Find a device’s MAC address**  
```bash
arping -I eth0 192.168.1.100
```
Returns the **MAC address** of `192.168.1.100`.  

### **3. Continuous ARP ping (until manually stopped)**  
```bash
arping -I eth0 192.168.1.1
```
Keeps sending ARP requests until **Ctrl+C** is pressed.  

### **4. Detect duplicate IP addresses**  
```bash
arping -D -I eth0 -c 5 192.168.1.50
```
- `-D` → Sends a **duplicate address detection probe**.  

---

## **Advanced Options**  

### **5. Send an ICMP Echo request instead of ARP**  
```bash
arping -0 192.168.1.1
```
- `-0` → Uses **ICMP Echo Request** instead of ARP (like `ping`).  

### **6. Avoid printing responses (quiet mode)**  
```bash
arping -q -I eth0 192.168.1.1
```
- `-q` → Only prints the final result (**silent mode**).  

### **7. Specify source IP (spoofed request)**  
```bash
arping -S 192.168.1.200 -I eth0 192.168.1.1
```
- `-S 192.168.1.200` → Pretend to be **192.168.1.200**.  

### **8. Specify target MAC address**  
```bash
arping -t 00:1A:2B:3C:4D:5E -I eth0 192.168.1.1
```
- `-t <MAC>` → Targets a **specific MAC address**.  

### **9. Flood ARP packets (for testing network load)**  
```bash
arping -f -I eth0 192.168.1.1
```
- `-f` → **Flood mode** (sends ARP packets as fast as possible).  

### **10. Set a timeout for waiting for replies**  
```bash
arping -w 3 -I eth0 192.168.1.1
```
- `-w 3` → Waits **3 seconds** for responses before stopping.  

### **11. Use VLAN tagging (802.1Q support)**  
```bash
arping -V 10 -I eth0 192.168.1.1
```
- `-V 10` → Uses **VLAN ID 10**.  

---

## **Example Output**  
```
ARPING 192.168.1.1 from 192.168.1.10 eth0
60 bytes from 00:1A:2B:3C:4D:5E (192.168.1.1): index=0 time=0.897 msec
60 bytes from 00:1A:2B:3C:4D:5E (192.168.1.1): index=1 time=0.932 msec
```
- **MAC Address:** `00:1A:2B:3C:4D:5E`  
- **Latency:** `0.897 ms`  

---

### **Getting Help**
- To see the full list of options and their descriptions, use:
  ```bash
  arping --help
  ```
- To access the manual page, use:
  ```bash
  man arping
  ```

### Installation
On most Linux distributions, `arping` is included by default. If not, you can install it using:
- **Debian/Ubuntu**:
  ```bash
  sudo apt install arping
  ```
- **Red Hat/CentOS**:
  ```bash
  sudo yum install arping
  ```
- **macOS** (via Homebrew):
  ```bash
  brew install arping
  ```

### Key Differences Between `ping` and `arping`:

* `ping` uses ICMP (Layer 3), while `arping` uses ARP (Layer 2).
* `ping` can be used to test connectivity across networks, while `arping` is limited to the local network segment.
* `ping` might be blocked by firewalls, while `arping` is more likely to succeed on local networks.

`arping` is a valuable tool for network troubleshooting and administration.  It's particularly useful when dealing with devices that are not responding to `ping` requests but are suspected to be on the same local network.
