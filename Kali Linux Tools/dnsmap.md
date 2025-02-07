![dnsmap](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/Images/dnsmap.png)

### What is DNSMap?

DNSMap is an open-source network reconnaissance tool designed to discover subdomains of a target domain. It is commonly used in penetration testing and security assessments to identify potential entry points or vulnerabilities within a domain's infrastructure. DNSMap works by brute-forcing subdomains using a predefined wordlist or by performing dictionary-based attacks.

### Key Features of DNSMap:
1. **Subdomain Discovery**: It helps identify subdomains associated with a target domain.
2. **Wordlist-Based Brute-Forcing**: Uses a built-in or custom wordlist to guess subdomains.
3. **Output Options**: Results can be saved in human-readable or machine-readable formats.
4. **Lightweight and Fast**: Designed to be efficient and easy to use.

---

### How to Use DNSMap

#### Installation:
DNSMap is typically pre-installed on penetration testing distributions like Kali Linux. If not, you can install it manually:

- On Debian-based systems (e.g., Kali Linux, Ubuntu):
  ```bash
  sudo apt update
  sudo apt install dnsmap
  ```

- On other systems, you can download and compile it from the source:
  ```bash
  git clone https://github.com/makefu/dnsmap.git
  cd dnsmap
  make
  sudo make install
  ```


#### Options:
1. **`-w <wordlist-file>`**:
   - Specifies a custom wordlist file for subdomain brute-forcing.
   - If not provided, DNSMap uses its built-in wordlist.

2. **`-r <regular-results-file>`**:
   - Saves the results in a human-readable format to the specified file.

3. **`-c <csv-results-file>`**:
   - Saves the results in CSV format to the specified file.

4. **`-d <delay-millisecs>`**:
   - Adds a delay (in milliseconds) between DNS queries to avoid detection or rate-limiting.

5. **`-i <ips-to-ignore>`**:
   - Ignores specific IP addresses in the results (useful to avoid false positives).

---

### **Examples**

1. **Basic Scan**:
   - Scan `example.com` using the default wordlist:
```bash
     dnsmap example.com
     ┌──(komugi㉿komugi)-[~]
└─$ dnsmap github.com 
dnsmap 0.36 - DNS Network Mapper

[+] searching (sub)domains for github.com using built-in wordlist
[+] using maximum random delay of 10 millisecond(s) between requests

admin.github.com
IP address #1: 140.82.112.23

blog.github.com
IPv6 address #1: 2606:50c0:8000::153
IPv6 address #2: 2606:50c0:8002::153
IPv6 address #3: 2606:50c0:8003::153
IPv6 address #4: 2606:50c0:8001::153

blog.github.com
IP address #1: 185.199.109.153
IP address #2: 185.199.108.153
IP address #3: 185.199.111.153
IP address #4: 185.199.110.153

classroom.github.com
IP address #1: 140.82.113.21

cs.github.com
IP address #1: 140.82.112.18

de.github.com
IP address #1: 140.82.112.18

```

2. **Custom Wordlist**:
   - Scan `example.com` using a custom wordlist (`yourwordlist.txt`) and save results to `/tmp/domainbf_results.txt`:
     ```bash
     dnsmap example.com -w yourwordlist.txt -r /tmp/domainbf_results.txt
     ```

3. **Add Delay Between Queries**:
   - Scan `example.com` with a 3-second delay between queries and save results to `/tmp/`:
     ```bash
     dnsmap example.com -r /tmp/ -d 3000
     ```

4. **Save Results in Current Directory**:
   - Scan `example.com` and save results to `./domainbf_results.txt`:
     ```bash
     dnsmap example.com -r ./domainbf_results.txt
     ```

5. **Ignore Specific IPs**:
   - Scan `example.com` and ignore specific IP addresses (e.g., `192.168.1.1` and `10.0.0.1`):
     ```bash
     dnsmap example.com -i 192.168.1.1,10.0.0.1
     ```

---

### **Tips for Using DNSMap Effectively**
- **Custom Wordlists**: Use tailored wordlists for better results, especially for specific industries or technologies.
- **Delay Option**: Use the `-d` option to avoid triggering rate limits or detection mechanisms.
- **Output Formats**: Use `-r` for human-readable results and `-c` for machine-readable CSV output.
- **False Positives**: Use the `-i` option to ignore IPs that may cause false positives.

---

### **Important Notes**
- **Legal Use**: Always ensure you have explicit permission to scan the target domain. Unauthorized scanning is illegal and unethical.
- **Combine with Other Tools**: Use DNSMap alongside tools like `Sublist3r`, `Amass`, or `Assetfinder` for comprehensive subdomain enumeration.

---

DNSMap is a lightweight and efficient tool for subdomain discovery, making it a valuable asset for penetration testers and security professionals.

