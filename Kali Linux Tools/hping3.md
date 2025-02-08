![hping3.png](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/Images/hping3.png)

`hping3` is a powerful and versatile command-line packet crafting tool.  It's used for network security testing, auditing, and exploration. Unlike `ping`, which primarily focuses on ICMP echo requests, `hping3` allows you to create and send custom packets with a wide range of options, giving you fine-grained control over the packets you transmit.

**What `hping3` Does:**

`hping3` can be used for various network tasks, including:

* **Firewall Testing:**  Testing firewall rules by sending various types of packets to see how the firewall responds.
* **Port Scanning:**  Scanning for open ports on a target host.
* **Network Probing:**  Exploring network devices and their responses to different packet types.
* **Denial-of-Service (DoS) Attacks (for educational/testing purposes only):**  Generating a high volume of traffic to simulate a DoS attack (use with extreme caution and only on networks you own or have explicit permission to test).
* **Network Performance Testing:**  Measuring network latency and bandwidth.
* **Spoofing:**  Creating packets with spoofed source IP addresses.
* **TCP/IP Stack Testing:**  Analyzing how a target system's TCP/IP stack handles different packet flags and options.

**How to Use `hping3`:**

**Basic Usage:**

```bash
hping3 host [options]
```

* `hping3`: The command to execute the tool.
* `host`: The target hostname or IP address.
* `[options]`: Flags and parameters to customize the behavior.

**General Options:**

* `-h, --help`: Show this help message.
* `-v, --version`: Show version information.
* `-c, --count`: Packet count.
* `-i, --interval`: Wait interval (e.g., `-i u1000` for 1000 microseconds).
* `--fast`: Alias for `-i u10000` (10 packets per second).
* `--faster`: Alias for `-i u1000` (100 packets per second).
* `--flood`: Send packets as fast as possible (flood mode). Don't show replies.  **Use with extreme caution!**
* `-n, --numeric`: Numeric output (don't resolve hostnames).
* `-q, --quiet`: Quiet output.
* `-I, --interface`: Interface name (otherwise, default routing interface).
* `-V, --verbose`: Verbose mode.
* `-D, --debug`: Debugging information.
* `-z, --bind`: Bind Ctrl+Z to TTL (default to destination port).
* `-Z, --unbind`: Unbind Ctrl+Z.
* `--beep`: Beep for every matching packet received.

**Mode Options (Packet Type):**

* `default mode`: TCP
* `-0, --rawip`: RAW IP mode.
* `-1, --icmp`: ICMP mode.
* `-2, --udp`: UDP mode.
* `-8, --scan`: SCAN mode (port scanning). Example: `hping3 --scan 1-30,70-90 -S www.target.host`
* `-9, --listen`: Listen mode.

**IP Options:**

* `-a, --spoof`: Spoof source address.
* `--rand-dest`: Random destination address mode.
* `--rand-source`: Random source address mode.
* `-t, --ttl`: TTL (Time To Live, default 64).
* `-N, --id`: IP ID (default random).
* `-W, --winid`: Use Windows-style ID byte ordering.
* `-r, --rel`: Relativize ID field (to estimate host traffic).
* `-f, --frag`: Split packets into fragments (may bypass weak ACLs).
* `-x, --morefrag`: Set More Fragments flag.
* `-y, --dontfrag`: Set Don't Fragment flag.
* `-g, --fragoff`: Set fragment offset.
* `-m, --mtu`: Set virtual MTU (implies `--frag` if packet size > MTU).
* `-o, --tos`: Type of Service (default 0x00). Use `--tos help` for options.
* `-G, --rroute`: Include RECORD_ROUTE option and display the route buffer.
* `--lsrr`: Loose source routing and record route.
* `--ssrr`: Strict source routing and record route.
* `-H, --ipproto`: Set IP protocol field (only in RAW IP mode).

**ICMP Options:**

* `-C, --icmptype`: ICMP type (default echo request).
* `-K, --icmpcode`: ICMP code (default 0).
* `--force-icmp`: Send all ICMP types (default sends only supported types).
* `--icmp-gw`: Set gateway address for ICMP redirect (default 0.0.0.0).
* `--icmp-ts`: Alias for `--icmp --icmptype 13` (ICMP timestamp).
* `--icmp-addr`: Alias for `--icmp --icmptype 17` (ICMP address subnet mask).
* `--icmp-help`: Display help for other ICMP options.

**UDP/TCP Options:**

* `-s, --baseport`: Base source port (default random).
* `-p, --destport`: Destination port (default 0). Use Ctrl+Z to increment/decrement.
* `-k, --keep`: Keep source port constant.
* `-w, --win`: Window size (default 64).
* `-O, --tcpoff`: Set fake TCP data offset.
* `-Q, --seqnum`: Show only TCP sequence number.
* `-b, --badcksum`: Send packets with a bad IP checksum (many systems will fix it).
* `-M, --setseq`: Set TCP sequence number.
* `-L, --setack`: Set TCP ACK number.
* `-F, --fin`: Set FIN flag.
* `-S, --syn`: Set SYN flag.
* `-R, --rst`: Set RST flag.
* `-P, --push`: Set PUSH flag.
* `-A, --ack`: Set ACK flag.
* `-U, --urg`: Set URG flag.
* `-X, --xmas`: Set X unused flag (0x40).
* `-Y, --ymas`: Set Y unused flag (0x80).
* `--tcpexitcode`: Use last `tcp->th_flags` as exit code.
* `--tcp-mss`: Enable TCP MSS option.
* `--tcp-timestamp`: Enable TCP timestamp option.

**Common Options (Data and Other):**

* `-d, --data`: Data size (default 0).
* `-E, --file`: Data from file.
* `-e, --sign`: Add 'signature'.
* `-j, --dump`: Dump packets in hex.
* `-J, --print`: Dump printable characters.
* `-B, --safe`: Enable 'safe' protocol.
* `-u, --end`: Tell you when `--file` reaches EOF and prevent rewind.
* `-T, --traceroute`: Traceroute mode (implies `--bind` and `--ttl 1`).
* `--tr-stop`: Exit when the first non-ICMP packet is received in traceroute mode.
* `--tr-keep-ttl`: Keep the source TTL fixed in traceroute mode.
* `--tr-no-rtt`: Don't calculate/show RTT in traceroute mode.

**ARS Packet Description (New, Unstable):**

* `--apd-send`: Send the packet described with APD (see `docs/APD.txt`).

### **hping3 Use Case Examples** 🚀

### **1. Basic Ping Test (ICMP Mode)**
Similar to `ping`, but with more control:  
```bash
hping3 -1 -c 4 hackthissite.org

HPING hackthissite.org (eth0 137.74.187.104): icmp mode set, 28 headers + 0 data bytes
len=46 ip=137.74.187.104 ttl=53 id=12949 icmp_seq=0 rtt=167.6 ms
len=46 ip=137.74.187.104 ttl=53 id=12950 icmp_seq=1 rtt=167.0 ms
len=46 ip=137.74.187.104 ttl=53 id=12951 icmp_seq=2 rtt=190.6 ms
len=46 ip=137.74.187.104 ttl=53 id=12952 icmp_seq=3 rtt=166.0 ms

--- hackthissite.org hping statistic ---
4 packets transmitted, 4 packets received, 0% packet loss
round-trip min/avg/max = 166.0/172.8/190.6 ms

```
🔹 `-1`: ICMP mode  
🔹 `-c 4`: Send 4 packets  

---

### **2. TCP SYN Scan (Detect Open Ports)**
Sends SYN packets to check if ports are open:  
```bash
hping3 -S -p 80 hackthissite.org

HPING hackthissite.org (eth0 137.74.187.102): S set, 40 headers + 0 data bytes
len=46 ip=137.74.187.102 ttl=64 id=13368 sport=80 flags=SA seq=0 win=65535 rtt=255.5 ms
len=46 ip=137.74.187.102 ttl=64 id=13369 sport=80 flags=SA seq=1 win=65535 rtt=170.8 ms
len=46 ip=137.74.187.102 ttl=64 id=13370 sport=80 flags=SA seq=2 win=65535 rtt=200.3 ms
len=46 ip=137.74.187.102 ttl=64 id=13371 sport=80 flags=SA seq=3 win=65535 rtt=171.8 ms
len=46 ip=137.74.187.102 ttl=64 id=13372 sport=80 flags=SA seq=4 win=65535 rtt=246.3 ms
len=46 ip=137.74.187.102 ttl=64 id=13373 sport=80 flags=SA seq=5 win=65535 rtt=176.9 ms
len=46 ip=137.74.187.102 ttl=64 id=13374 sport=80 flags=SA seq=6 win=65535 rtt=287.4 ms
len=46 ip=137.74.187.102 ttl=64 id=13375 sport=80 flags=SA seq=7 win=65535 rtt=166.6 ms
len=46 ip=137.74.187.102 ttl=64 id=13376 sport=80 flags=SA seq=8 win=65535 rtt=229.4 ms
len=46 ip=137.74.187.102 ttl=64 id=13377 sport=80 flags=SA seq=9 win=65535 rtt=176.4 ms
len=46 ip=137.74.187.102 ttl=64 id=13378 sport=80 flags=SA seq=10 win=65535 rtt=175.3 ms
len=46 ip=137.74.187.102 ttl=64 id=13379 sport=80 flags=SA seq=11 win=65535 rtt=170.3 ms
len=46 ip=137.74.187.102 ttl=64 id=13380 sport=80 flags=SA seq=12 win=65535 rtt=220.0 ms
len=46 ip=137.74.187.102 ttl=64 id=13381 sport=80 flags=SA seq=13 win=65535 rtt=251.9 ms
len=46 ip=137.74.187.102 ttl=64 id=13382 sport=80 flags=SA seq=14 win=65535 rtt=271.3 ms
len=46 ip=137.74.187.102 ttl=64 id=13383 sport=80 flags=SA seq=15 win=65535 rtt=164.5 ms
len=46 ip=137.74.187.102 ttl=64 id=13384 sport=80 flags=SA seq=16 win=65535 rtt=288.2 ms
len=46 ip=137.74.187.102 ttl=64 id=13385 sport=80 flags=SA seq=17 win=65535 rtt=164.0 ms
len=46 ip=137.74.187.102 ttl=64 id=13386 sport=80 flags=SA seq=18 win=65535 rtt=164.2 ms
len=46 ip=137.74.187.102 ttl=64 id=13387 sport=80 flags=SA seq=19 win=65535 rtt=171.5 ms
len=46 ip=137.74.187.102 ttl=64 id=13388 sport=80 flags=SA seq=20 win=65535 rtt=202.0 ms
len=46 ip=137.74.187.102 ttl=64 id=13389 sport=80 flags=SA seq=21 win=65535 rtt=225.9 ms
len=46 ip=137.74.187.102 ttl=64 id=13390 sport=80 flags=SA seq=22 win=65535 rtt=248.7 ms
len=46 ip=137.74.187.102 ttl=64 id=13391 sport=80 flags=SA seq=23 win=65535 rtt=167.8 ms
len=46 ip=137.74.187.102 ttl=64 id=13392 sport=80 flags=SA seq=24 win=65535 rtt=195.3 ms
len=46 ip=137.74.187.102 ttl=64 id=13393 sport=80 flags=SA seq=25 win=65535 rtt=218.6 ms

--- hackthissite.org hping statistic ---
26 packets transmitted, 26 packets received, 0% packet loss
round-trip min/avg/max = 164.0/207.0/288.2 ms

```
🔹 `-S`: SYN flag  
🔹 `-p 80`: Target port 80 (HTTP)  

🔥 **Full Port Scan (1-1000):**  
```bash
hping3 -S -p 1-1000 hackthissite.org --faster
```
**⚠️ Warning:** Ensure you have permission before scanning a target.

---

### **3. Firewall Evasion (Spoofed IP)**
Bypassing firewall rules by spoofing the source IP:  
```bash
hping3 -S -p 443 -a 192.168.1.100 hackthissite.org
```
🔹 `-a 192.168.1.100`: Spoof source IP  

---

### **4. Traceroute Alternative**
Traceroute using TCP instead of ICMP:  
```bash
hping3 -S -p 80 --traceroute hackthissite.org
```
🔹 `--traceroute`: Enables traceroute mode  

---

### **5. Flooding Attack (Stress Testing)**
Sends packets as fast as possible to test a system's limits:  
```bash
hping3 --flood -S -p 80 hackthissite.org
```
🔹 `--flood`: Sends packets rapidly  
🔹 `-S`: SYN flood  

🚨 **Use Responsibly! Flooding can be considered an attack if done without permission.**

---

### **6. Detecting Firewalls and IDS**
By sending packets with invalid TCP flags, some firewalls may leak responses:  
```bash
hping3 -F -P -U -p 80 hackthissite.org
```
🔹 `-F -P -U`: FIN, PUSH, and URG flags  

---

### **7. Advanced TCP Testing (Custom Window Size)**
Checking for TCP-based filtering by modifying the TCP window size:  
```bash
hping3 -S -p 443 -w 64 hackthissite.org
```
🔹 `-w 64`: TCP window size 64  

---


**Interpreting the Results:**

`hping3` displays information about the packets sent and received.  The output can include details like IP addresses, port numbers, flags, TTL, RTT (round-trip time), and more.  The specific output depends on the options used.

**Important Considerations:**

* **Ethical Use:**  Use `hping3` responsibly and ethically.  Only use it on networks you own or have explicit permission to test.  Unauthorized use can be illegal and harmful.
* **Flood Attacks:**  The `--flood` option can be used to simulate DoS attacks.  Use this option with extreme caution and *only* on networks you own or have permission to test.  Misuse can cause significant disruption.
* **Root Privileges:**  `hping3` often requires root privileges to send raw packets.  You might need to use `sudo`.

`hping3` is a powerful tool for network exploration and security testing.  Its flexibility and wide range of options make it a valuable asset for network professionals. However, it's essential to use it responsibly and ethically.  Always prioritize obtaining explicit permission before using `hping3` on any network that you do not own.

