![dnsrecon](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/Images/dnsrecon.png)

### **What is DNSRecon?**

**DNSRecon** is a powerful DNS enumeration tool used for gathering information about a target domain's DNS infrastructure. It is commonly used in penetration testing, security assessments, and reconnaissance phases to identify DNS records, subdomains, and potential vulnerabilities. DNSRecon provides a wide range of features, including zone transfers, brute-forcing subdomains, reverse DNS lookups, and more.

---

### **Key Features of DNSRecon**
1. **DNS Record Enumeration**:
   - Retrieves various DNS records (A, AAAA, MX, TXT, SOA, NS, etc.).
2. **Zone Transfers**:
   - Attempts to perform AXFR (zone transfer) requests to gather DNS data.
3. **Subdomain Brute-Forcing**:
   - Uses wordlists to discover subdomains.
4. **Reverse DNS Lookups**:
   - Maps IP addresses to domain names.
5. **Cache Snooping**:
   - Checks for cached DNS records.
6. **Output Options**:
   - Supports multiple output formats (CSV, XML, JSON).

---

### **How to Use DNSRecon**

#### Installation:
DNSRecon is pre-installed on many penetration testing distributions like Kali Linux. If not, you can install it manually:

- On Debian-based systems (e.g., Kali Linux, Ubuntu):
  ```bash
  sudo apt update
  sudo apt install dnsrecon
  ```

- Alternatively, you can install it via Python's `pip`:
  ```bash
  pip install dnsrecon
  ```

---

#### Basic Usage:

1. **Enumerate DNS Records**:
   To retrieve all DNS records for a domain:
   ```bash
   dnsrecon -d hackthissite.org
   ```

2. **Perform a Zone Transfer**:
   To attempt a DNS zone transfer (AXFR):
```bash
dnsrecon -d hackthissite.org -t axfr

┌──(komugi㉿komugi)-[~]
└─$ dnsrecon -d hackthissite.org
[*] std: Performing General Enumeration against: hackthissite.org...
[-] A timeout error occurred please make sure you can reach the target DNS Servers
[-] directly and requests are not being filtered. Increase the timeout from 3.0 second
[-] to a higher number with --lifetime <time> option.
                                                                                                                                     
┌──(komugi㉿komugi)-[~]
└─$ dnsrecon -d hackthissite.org -t axfr
[*] Checking for Zone Transfer for hackthissite.org name servers
[*] Resolving SOA Record
[+]      SOA c.ns.buddyns.com 116.203.6.3
[+]      SOA c.ns.buddyns.com 2a01:4f8:1c0c:8115::3
[*] Resolving NS Records
[*] NS Servers found:
[+]      NS f.ns.buddyns.com 23.27.101.128
[+]      NS f.ns.buddyns.com 2606:fc40:4003:26::a
[+]      NS g.ns.buddyns.com 192.184.93.99
[+]      NS g.ns.buddyns.com 2604:180:1:92a::3
[+]      NS c.ns.buddyns.com 116.203.6.3
[+]      NS c.ns.buddyns.com 2a01:4f8:1c0c:8115::3
[+]      NS h.ns.buddyns.com 103.25.56.55
[+]      NS h.ns.buddyns.com 2406:d500:2::de4f:f105
[+]      NS j.ns.buddyns.com 37.143.61.179
[+]      NS j.ns.buddyns.com 2a01:a500:2766::5c3f:d10b
[*] Removing any duplicate NS server IP Addresses...
[*]  
[*] Trying NS server 192.184.93.99
[+] 192.184.93.99 Has port 53 TCP Open
[-] Zone Transfer Failed (Zone transfer error: NOTAUTH)
[*]  
[*] Trying NS server 23.27.101.128
[+] 23.27.101.128 Has port 53 TCP Open
[-] Zone Transfer Failed (Zone transfer error: NOTAUTH)
[*]  
[*] Trying NS server 116.203.6.3
[+] 116.203.6.3 Has port 53 TCP Open
[-] Zone Transfer Failed (Zone transfer error: NOTAUTH)
[*]  
[*] Trying NS server 2604:180:1:92a::3
[-] Zone Transfer Failed for 2604:180:1:92a::3!
[-] Port 53 TCP is being filtered
[*]  
[*] Trying NS server 103.25.56.55
[+] 103.25.56.55 Has port 53 TCP Open
[-] Zone Transfer Failed (Zone transfer error: NOTAUTH)
[*]  
[*] Trying NS server 2a01:a500:2766::5c3f:d10b
[-] Zone Transfer Failed for 2a01:a500:2766::5c3f:d10b!
[-] Port 53 TCP is being filtered
[*]  
[*] Trying NS server 2606:fc40:4003:26::a
[-] Zone Transfer Failed for 2606:fc40:4003:26::a!
[-] Port 53 TCP is being filtered
[*]  
[*] Trying NS server 2a01:4f8:1c0c:8115::3
[-] Zone Transfer Failed for 2a01:4f8:1c0c:8115::3!
[-] Port 53 TCP is being filtered
[*]  
[*] Trying NS server 37.143.61.179
[+] 37.143.61.179 Has port 53 TCP Open
[-] Zone Transfer Failed (Zone transfer error: NOTAUTH)
[*]  
[*] Trying NS server 2406:d500:2::de4f:f105
[-] Zone Transfer Failed for 2406:d500:2::de4f:f105!
[-] Port 53 TCP is being filtered

```

3. **Brute-Force Subdomains**:
   To brute-force subdomains using a wordlist:
   ```bash
   dnsrecon -d hackthissite.org -D /path/to/wordlist.txt -t brt
   ```

4. **Reverse DNS Lookup**:
   To perform a reverse DNS lookup on an IP range:
   ```bash
   dnsrecon -r 192.168.1.0/24
   ```

5. **Save Results to a File**:
   To save the output in a specific format (CSV, XML, or JSON):
   ```bash
   dnsrecon -d hackthissite.org -c output.csv
   ```

6. **Check for Cache Snooping**:
   To check for cached DNS records:
   ```bash
   dnsrecon -d hackthissite.org -t snoop
   ```

---

**Key Options and Their Explanations:**

* **Target Specification:**
    * `-d DOMAIN`:  **Required.** Specifies the target domain name (e.g., `-d hackthissite.org`).  This is the domain you want to perform DNS reconnaissance on.
* **Name Server Options:**
    * `-n NS_SERVER`: Specifies a specific name server to query (e.g., `-n 8.8.8.8`). If not provided, `dnsrecon` will try to find authoritative name servers for the target domain.
* **Range Options (for reverse lookups):**
    * `-r RANGE`: Specifies an IP address range for reverse DNS lookups (e.g., `-r 192.168.1.0/24`). This is used to find hostnames associated with IP addresses in the given range.
* **Dictionary Options (for brute-forcing subdomains):**
    * `-D DICTIONARY`: Specifies a dictionary file containing subdomain names to try (e.g., `-D subdomains.txt`).  This is used for subdomain brute-forcing.  A common use case is to try many common subdomain names (like `www`, `mail`, `ftp`, `blog`, etc.) to see if they exist.
* **Flags (Boolean Options):**
    * `-f`: Performs a full zone transfer.  This attempts to retrieve the entire DNS zone information from a name server.  This is often blocked by servers for security reasons.
    * `-a`: Performs an AXFR (Authoritative Transfer) request.  Similar to `-f`.
    * `-s`: Performs a standard DNS lookup for common record types (A, AAAA, MX, NS, SOA, TXT).
    * `-b`: Performs a reverse lookup (PTR record query).
    * `-y`: Performs a DNSSEC (DNS Security Extensions) validation.
    * `-k`: Performs a banner grab on the DNS server.
    * `-w`: Performs a whois lookup for the target domain.
    * `-z`: Performs a zone walking (iterating through subdomains).
* **Other Options:**
    * `--threads THREADS`: Specifies the number of threads to use (for faster scanning).
    * `--lifetime LIFETIME`: Specifies the DNS query timeout (in seconds).
    * `--tcp`: Use TCP instead of UDP for DNS queries.
    * `--db DB`: Specifies a database file to use for storing results.
    * `-x XML`: Saves the results in XML format.
    * `-c CSV`: Saves the results in CSV format.
    * `-j JSON`: Saves the results in JSON format.
    * `--iw`: Ignores wildcards in DNS responses.
    * `--disable_check_recursion`: Disables checking for recursive DNS.
    * `--disable_check_bindversion`: Disables checking the BIND version of the DNS server.
    * `-V`: Displays the version of `dnsrecon`.
    * `-v`: Increases verbosity (more output).
    * `-t TYPE`: Specifies the record type to query (e.g., `-t A`, `-t MX`, `-t CNAME`).

#### Example Commands:

- **Basic DNS Enumeration**:
  ```bash
  dnsrecon -d example.com
  ```

- **Brute-Force Subdomains with a Custom Wordlist**:
  ```bash
  dnsrecon -d example.com -D /path/to/wordlist.txt -t brt
  ```

- **Zone Transfer Attempt**:
  ```bash
  dnsrecon -d example.com -t axfr
  ```

- **Reverse DNS Lookup on an IP Range**:
  ```bash
  dnsrecon -r 192.168.1.0/24
  ```

- **Save Results in CSV Format**:
  ```bash
  dnsrecon -d example.com -c output.csv
  ```

---

### **Advanced Options**:
- **Specify a DNS Server**:
  Use the `-n` option to specify a DNS server:
```bash
dnsrecon -d hackthissite.org -n 8.8.8.8
┌──(komugi㉿komugi)-[~]
└─$ dnsrecon -d hackthissite.org -n 8.8.8.8
[*] std: Performing General Enumeration against: hackthissite.org...
[-] DNSSEC is not configured for hackthissite.org
[*]      SOA c.ns.buddyns.com 116.203.6.3
[*]      SOA c.ns.buddyns.com 2a01:4f8:1c0c:8115::3
[*]      NS g.ns.buddyns.com 192.184.93.99
[*]      NS g.ns.buddyns.com 2604:180:1:92a::3
[*]      NS c.ns.buddyns.com 116.203.6.3
[*]      NS c.ns.buddyns.com 2a01:4f8:1c0c:8115::3
[*]      NS f.ns.buddyns.com 23.27.101.128
[*]      NS f.ns.buddyns.com 2606:fc40:4003:26::a
[*]      NS j.ns.buddyns.com 37.143.61.179
[*]      NS j.ns.buddyns.com 2a01:a500:2766::5c3f:d10b
[*]      NS h.ns.buddyns.com 103.25.56.55
[*]      NS h.ns.buddyns.com 2406:d500:2::de4f:f105
[*]      MX aspmx.l.google.com 142.251.173.27
[*]      MX aspmx3.googlemail.com 142.251.9.26
[*]      MX alt1.aspmx.l.google.com 142.250.153.27
[*]      MX aspmx4.googlemail.com 142.250.150.26
[*]      MX aspmx5.googlemail.com 74.125.200.26
[*]      MX aspmx2.googlemail.com 142.250.153.26
[*]      MX alt2.aspmx.l.google.com 142.251.9.27
[*]      MX aspmx.l.google.com 2a00:1450:400c:c0b::1a
[*]      MX aspmx3.googlemail.com 2a00:1450:4025:c03::1a
[*]      MX alt1.aspmx.l.google.com 2a00:1450:4013:c16::1a
[*]      MX aspmx4.googlemail.com 2a00:1450:4010:c1c::1a
[*]      MX aspmx5.googlemail.com 2404:6800:4003:c00::1b
[*]      MX aspmx2.googlemail.com 2a00:1450:4013:c16::1b
[*]      MX alt2.aspmx.l.google.com 2a00:1450:4025:c03::1b
[*]      A hackthissite.org 137.74.187.104
[*]      A hackthissite.org 137.74.187.103
[*]      A hackthissite.org 137.74.187.102
[*]      A hackthissite.org 137.74.187.101
[*]      A hackthissite.org 137.74.187.100
[*]      SPF v=spf1 a mx ip4:137.74.187.96 ip4:137.74.187.97 ip4:137.74.187.98 a:mail.hackthissite.org include:aspmx.googlemail.com include:spf.hackmail.org -all
[*]      TXT hackthissite.org t-verify=e3f12c9c23e2e475563590326df31a12
[*]      TXT hackthissite.org v=spf1 a mx ip4:137.74.187.96 ip4:137.74.187.97 ip4:137.74.187.98 a:mail.hackthissite.org include:aspmx.googlemail.com include:spf.hackmail.org -all
[*]      TXT hackthissite.org HARICA-aaaDeHpueWSi2N4aEvO
[*]      TXT _dmarc.hackthissite.org v=DMARC1;p=quarantine;sp=quarantine;fo=0:1:d:s;aspf=r;adkim=r;ri=86400;pct=25;rua=mailto:8rbjyycl@ag.dmarcian.eu;ruf=mailto:8rbjyycl@fr.dmarcian.eu;
[*] Enumerating SRV Records
[-] No SRV Records Found for hackthissite.org

```

- **Threading**:
  Use the `-t` option with a number to specify the number of threads for brute-forcing:
  ```bash
  dnsrecon -d example.com -t brt -T 10
  ```

- **Verbose Output**:
  Use the `-v` option for verbose output:
  ```bash
  dnsrecon -d example.com -v
  ```

---

### **Tips for Effective Use**:
- **Custom Wordlists**: Use tailored wordlists for better subdomain discovery.
- **Combine with Other Tools**: Use DNSRecon alongside tools like `Sublist3r`, `Amass`, or `DNSMap` for comprehensive DNS enumeration.
- **Legal Considerations**: Always ensure you have permission to scan the target domain. Unauthorized scanning can be illegal.

---

### **Output Interpretation**:
DNSRecon provides detailed output, including:
- **A Records**: IP addresses associated with the domain.
- **MX Records**: Mail servers for the domain.
- **NS Records**: Name servers for the domain.
- **SOA Records**: Start of Authority information.
- **Subdomains**: Discovered subdomains (if brute-forcing is used).

---

DNSRecon is a versatile and powerful tool for DNS enumeration, making it an essential part of any security professional's toolkit.
