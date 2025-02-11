![ike-scan.png](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/Images/ike-scan.png)

`ike-scan` is a command-line tool used to discover and fingerprint IKE (Internet Key Exchange) daemons. IKE is a protocol used to establish and manage Security Associations (SAs) for IPsec (IP Security).  `ike-scan` is primarily used for security auditing and identifying potential vulnerabilities in IKE implementations.

**What `ike-scan` Does:**

`ike-scan` sends IKE requests to target hosts to:

* **Discover IKE Daemons:** Identify devices that are running IKE.
* **Fingerprint IKE Implementations:** Determine the specific IKE implementation (e.g., strongSwan, OpenIKEv2, Cisco).
* **Enumerate Supported Proposals:** Discover the supported IKE proposals (combinations of encryption algorithms, authentication methods, etc.).
* **Identify Aggressive Mode Support:** Check if the IKE daemon supports Aggressive Mode, which is considered less secure than Main Mode.
* **Detect Vendor IDs:** Identify vendor IDs, which can sometimes reveal information about the device or its operating system.

**Key Features and Capabilities:**

* **IKE Discovery:**  Identifies IKE-enabled devices.
* **Fingerprinting:**  Determines the specific IKE implementation.
* **Proposal Enumeration:**  Lists supported IKE proposals.
* **Aggressive Mode Detection:**  Checks for Aggressive Mode support.
* **Vendor ID Detection:**  Identifies vendor IDs.
* **Command-Line Interface:**  Easy to use and scriptable.

**How to Use `ike-scan`:**

 **Installation:** `ike-scan` is usually available in the package repositories of most Linux distributions (e.g., `apt-get install ike-scan` on Debian/Ubuntu, `yum install ike-scan` on CentOS/RHEL).
 
**Basic Usage:**

```
ike-scan [options] [hosts...]
```

* **Target Hosts:** Hosts can be specified as IP addresses, hostnames, IPnetwork/bits (e.g., 192.168.1.0/24), IPstart-IPend (e.g., 192.168.1.3-192.168.1.27), or IPnetwork:NetMask (e.g., 192.168.1.0:255.255.255.0).  These formats can be used both on the command line and in a file specified with `--file`.

**General Options:**

* `--help or -h`: Display this help message.
* `--file=<fn> or -f <fn>`: Read hostnames/IPs from a file. Use "-" for stdin.
* `--version or -V`: Display program version.

**Networking Options:**

* `--sport=<p> or -s <p>`: Set UDP source port (default: 500, 0=random). Requires superuser privileges for ports below 1024.  `--nat-t` changes the default to 4500.
* `--dport=<p> or -d <p>`: Set UDP destination port (default: 500). `--nat-t` changes the default to 4500.
* `--retry=<n> or -r <n>`: Set total attempts per host (default: 3).
* `--timeout=<n> or -t <n>`: Set initial per-host timeout in milliseconds (default: 500). Subsequent timeouts are multiplied by the backoff factor.
* `--bandwidth=<n> or -B <n>`: Set desired outbound bandwidth (default: 56000 bps). Use "K" for kilobits/sec, "M" for megabits/sec (decimal multiples).
* `--interval=<n> or -i <n>`: Set minimum packet interval in milliseconds (default: varies).  Use "u" for microseconds, "s" for seconds. Cannot be used with `--bandwidth`.
* `--backoff=<b> or -b <b>`: Set timeout backoff factor (default: 1.50).
* `--tcp[=<n>] or -T[<n>]`: Use TCP transport instead of UDP.  `<n>` can be 1 (RAW IKE over TCP - Checkpoint) or 2 (Encapsulated IKE over TCP - Cisco).  Only a single target host is allowed.
* `--tcptimeout=<n> or -O <n>`: Set TCP connect timeout in seconds (default: 10).
* `--nat-t`: Use RFC 3947 NAT-Traversal encapsulation. Changes default ports to 4500.
* `--sourceip=<s>`: Set source IP address for outgoing packets. Use "random" for a different random source address per packet. Requires raw socket support and superuser privileges. Doesn't work on all OSs.
* `--bindip=<s>`: Set the IP address to bind to for outgoing packets and receiving responses.
* `--nodns or -N`: Do not use DNS to resolve names. All hosts must be specified as IP addresses.

**Output Options:**

* `--verbose or -v`: Display verbose progress messages (use multiple times for more detail).
* `--quiet or -q`: Don't decode the returned packet (shorter output lines).
* `--multiline or -M`: Split the payload decode across multiple lines for readability.
* `--showbackoff[=<n>] or -o[<n>]`: Display the backoff fingerprint table.  `<n>` is the time to wait after the last packet (default: 60 seconds).
* `--shownum`: Display the host number for received packets.
* `--timestamp`: Display timestamps for received packets.

**IKE Options:**

* `--aggressive or -A`: Use IKE Aggressive Mode (default is Main Mode). Requires `--dhgroup`, `--id`, and `--idtype`.
* `--id=<id> or -n <id>`: Use `<id>` as the identification value (Aggressive Mode only). Can be a string or a hex value (e.g., `--id=0xdeadbeef`).
* `--idtype=<n> or -y <n>`: Use identification type `<n>` (Aggressive Mode only, default: 3 - ID_USER_FQDN). See RFC 2407 4.6.2.
* `--dhgroup=<n> or -g <n>`: Use Diffie-Hellman Group `<n>` (Aggressive Mode and IKEv2 only, default: 2). Values: 1, 2, 5, 14, 15, 16, 17, 18, 19, 20, 21.
* `--gssid=<n> or -G <n>`: Use GSS ID `<n>` (hex string). Uses attribute type 16384 (or 32001 for Windows 2000). Use `--auth=65001` for Kerberos.
* `--lifetime=<s> or -l <s>`: Set IKE lifetime in seconds (default: 28800). Can be a decimal integer (4-byte value), hex number (appropriate size value), or "none". Used with `--trans` for multiple transform payloads with different lifetimes.
* `--lifesize=<s> or -z <s>`: Set IKE lifesize in Kilobytes (default: 0). Similar to `--lifetime` in terms of value specification and usage with `--trans`.
* `--auth=<n> or -m <n>`: Set authentication method (default: 1 - PSK). RFC values 1-5. Checkpoint hybrid mode is 64221. GSS is 65001. XAUTH uses 65001-65010. Not applicable to IKEv2.
* `--vendor=<v> or -e <v>`: Set vendor ID string (hex value). Can be used multiple times.
* `--trans=<t> or -a <t>`: Use custom transform. Can be used multiple times.  Two ways to specify: new (attribute/value pairs) and old (fixed attribute list). See the help message for details. Not yet supported for IKEv2.
* `--certreq=<c> or -C <c>`: Add CertificateRequest payload (hex value). First byte is certificate type, the rest is the CA. See RFC 2408 3.9 and 3.10.
* `--doi=<d> or -D <d>`: Set SA DOI (default: 1 - IPsec).
* `--situation=<s> or -S <s>`: Set SA Situation (default: 1 - SIT_IDENTITY_ONLY for IPsec).
* `--protocol=<p> or -j <p>`: Set Proposal protocol ID (default: 1 - PROTO_ISAKMP for IPsec).
* `--transid=<t> or -k <t>`: Set Transform ID (default: 1 - KEY_IKE for IPsec).
* `--spisize=<n>`: Set proposal SPI size (default: 0).
* `--hdrflags=<n>`: Set ISAKMP header flags (default: 0). See RFC 2408 3.1.
* `--hdrmsgid=<n>`: Set ISAKMP header message ID (default: 0, should be 0 for IKE Phase-1).
* `--cookie=<n>`: Set ISAKMP initiator cookie (hex value). Requires a single target.
* `--exchange=<n>`: Set exchange type. Only Main (2) and Aggressive (4) modes are supported.
* `--nextpayload=<n>`: Set next payload in ISAKMP header.
* `--randomseed=<n>`: Use `<n>` to seed the PRNG.
* `--rcookie=<n>`: Set ISAKMP responder cookie (hex value, default: 0).
* `--noncelen=<n> or -c <n>`: Set nonce length in bytes (default: 20, Aggressive Mode only).
* `--headerlen=<n> or -L <n>`: Set ISAKMP header length. Can be "+n", "-n", or "n".
* `--mbz=<n> or -Z <n>`: Set reserved (MBZ) fields (0-255).
* `--headerver=<n> or -E <n>`: Specify ISAKMP header version (default: 0x10).
* `--pskcrack[=<f>] or -P[<f>]`: Crack aggressive mode PSKs. Outputs parameters for `psk-crack`. `<f>` is the optional filename. Requires a single target and Aggressive Mode.
* `--ikev2 or -2`: Use IKE version 2 (experimental, default proposal only).

### **Example 1: Scan a Single IP for IKE Services**
```bash
ike-scan 192.168.1.1
```
- Sends IKE requests to **192.168.1.1** on UDP port 500.
- If the target responds, it likely has an IKE service running.

---

### **Example 2: Scan a Network for IKE Services**
```bash
ike-scan 192.168.1.0/24
```
- Scans all devices in the **192.168.1.0/24** subnet.
- Useful for identifying VPN gateways on a network.

---

### **Example 3: Use Aggressive Mode Scan**
```bash
ike-scan --aggressive 192.168.1.1
```
- Sends IKE Aggressive Mode requests.
- Some VPNs disclose more information in Aggressive Mode, which can be useful for fingerprinting.

---

### **Example 4: Identify VPN Vendor**
```bash
ike-scan --aggressive --id=myvpn 192.168.1.1
```
- Tests the target for a VPN service that responds to **"myvpn"** as an ID.
- Useful when trying to identify VPN configurations.

---

### **Example 5: Scan with NAT-Traversal**
```bash
ike-scan --nat-t 192.168.1.1
```
- Uses **NAT-Traversal (NAT-T)** to check if the VPN server supports NAT traversal.

---

### **Example 6: Capture Raw Responses**
```bash
ike-scan --log=output.txt 192.168.1.1
```
- Saves scan results to **output.txt** for further analysis.

---

### **Example 7: Fingerprint a VPN**
```bash
ike-scan --trans=5,2,1,2 --aggressive 192.168.1.1
```
- Attempts to match specific **IKE transforms** (encryption settings).
- Helps in identifying **VPN vendor and configuration**.

---

**Use Cases:**

* **Security Auditing:** Assessing the security of IKE implementations.
* **Vulnerability Scanning:** Identifying potential vulnerabilities in IKE configurations.
* **VPN Testing:** Testing the security of VPN gateways.

**Important Considerations:**

* **Firewall Considerations:** Firewalls can block IKE traffic.
* **Aggressive Mode:** While Aggressive Mode can be useful for discovery, it's generally considered less secure than Main Mode.
* **Ethical Use:** Only use `ike-scan` on networks and devices that you have explicit permission to test. Unauthorized scanning is illegal and unethical.

`ike-scan` is a valuable tool for anyone responsible for the security of IPsec VPNs or other IKE-dependent systems. It helps identify potential weaknesses in IKE configurations, ensuring the confidentiality and integrity of secure communications.  However, it's crucial to use it responsibly and ethically. Always obtain proper authorization before testing any network.  Be aware of the limitations of the tool and the potential for detection.
