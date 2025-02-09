![netdiscover.png](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/Images/netdiscover.png)

`netdiscover` is a passive network reconnaissance tool, primarily used for discovering hosts on a local network. It operates by listening for ARP (Address Resolution Protocol) requests and responses, which are used by devices to map IP addresses to MAC addresses. Because it's passive, it's generally harder to detect than active scanning tools.

**What `netdiscover` Does:**

`netdiscover` passively sniffs network traffic to identify active hosts on the same network segment. It doesn't send any packets itself (unless you use the `-r` option for sending ARP requests, which makes it semi-passive).  It simply listens for the ARP traffic that already exists on the network.  This makes it useful for:

* **Identifying Active Hosts:** Discovering which devices are currently connected to the network.
* **Network Mapping:** Getting a basic overview of the network's connected devices.
* **Troubleshooting:** Identifying devices that might be causing network issues.

**Key Features and Capabilities:**

* **Passive Scanning:**  Doesn't actively probe hosts (by default).
* **ARP Sniffing:**  Listens for ARP requests and responses.
* **Fast and Efficient:**  Quickly identifies active hosts.
* **Simple to Use:**  Has a straightforward command-line interface.

**How to Use `netdiscover`:**

**Basic Usage:**

```bash
netdiscover [-i device] [-r range | -l file | -p] [-m file] [-F filter] [-s time] [-c count] [-n node] [-dfPLNS]
```

**Options:**

* `-i device`:  Specifies the network interface to use (e.g., `-i eth0`, `-i wlan0`).  This is often required.
* `-r range`: Scan a specific IP address range instead of the automatic scan.  You can specify multiple ranges separated by commas (e.g., `-r 192.168.1.0/24,10.0.0.0/16`).
* `-l file`: Scan the IP address ranges listed in the given file.  Each range should be on a separate line in the file.
* `-p`: Passive mode.  `netdiscover` will only listen for ARP traffic; it won't send any ARP requests. This is the default if `-r` or `-l` are not used.
* `-m file`: Scan a list of known MAC addresses and hostnames from the given file. This allows you to associate known names with discovered MAC addresses.
* `-F filter`: Customize the pcap filter expression. The default filter is `"arp"`.  This allows for more complex filtering of network traffic.
* `-s time`: Set the sleep time (in milliseconds) between each ARP request (used with active scanning).
* `-c count`: Set the number of times to send each ARP request.  This can be useful on networks with packet loss.
* `-n node`: Set the last source IP octet used for scanning (from 2 to 253).  This can be useful for avoiding conflicts or specific IP ranges.
* `-d`: Ignore home configuration files for autoscan and fast mode.
* `-f`: Enable fast mode scan. This saves time and is recommended for automatic scans.
* `-P`: Print results in a format suitable for parsing by another program and stop after the active scan.
* `-L`: Similar to `-P`, but continues listening after the active scan is completed.
* `-N`: Do not print the header.  Only valid when `-P` or `-L` is enabled.
* `-S`: Enable sleep time suppression between each request (hardcore mode).  Use this with extreme caution as it can flood the network.

**Key Points:**

* **Passive vs. Active:**  By default, `netdiscover` operates in passive mode, only listening for ARP traffic. The `-r` option enables active scanning by sending ARP requests.
* **Target Specification:** You can specify target IP ranges using `-r` or `-l`. If you don't specify a range, `netdiscover` will scan common LAN addresses.
* **Output Options (`-P`, `-L`, `-N`):** These options control how the results are displayed, especially for scripting or integration with other tools.
* **Fast Mode (`-f`):** This is a useful option for speeding up scans, especially automatic scans.
* **Hardcore Mode (`-S`):** Use this with caution, as it can be very aggressive and potentially disrupt network traffic.

**Example Usage:**

   * Listening on a specific interface:
     ```bash
     netdiscover -i wlan0
     ```

   * Sending ARP requests (semi-passive):
     ```bash
     netdiscover -r
     ```

   * Specifying the network mask:
     ```bash
     netdiscover -n 192.168.1.0/24
     ```

   * Sending a specific number of ARP requests:
     ```bash
     netdiscover -r -c 10
     ```

**Interpreting the Results:**

`netdiscover` displays a table showing the discovered hosts, their IP addresses, MAC addresses, and hardware vendor information (if available).

**Important Considerations:**

* **Passive vs. Active:** By default, `netdiscover` is passive.  It only listens for existing ARP traffic.  Using the `-r` option makes it semi-passive, as it will send out ARP requests.
* **Root Privileges:** `netdiscover` requires root privileges to capture network traffic. You'll usually need to run it with `sudo`.
* **Local Network:** `netdiscover` only works on the local network segment.  It cannot discover hosts on other networks.
* **ARP Spoofing Detection:**  `netdiscover`'s output can sometimes be an indicator of potential ARP spoofing attacks if you see unexpected MAC addresses associated with IP addresses.

`netdiscover` is a simple but useful tool for quickly identifying active hosts on a local network. Its passive nature makes it a good choice when you want to avoid generating much traffic or alerting potential adversaries.  However, for more comprehensive network scanning and host discovery, tools like Nmap are often preferred.
