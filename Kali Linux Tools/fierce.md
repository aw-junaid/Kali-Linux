![fierce](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/Images/fierce.png)

`fierce` is a powerful, open-source reconnaissance tool used for DNS enumeration and subdomain discovery.  It's designed to help security professionals and researchers identify potential vulnerabilities and gather information about a target domain.  While it's a valuable tool, it's essential to use it ethically and legally, only targeting domains you have explicit permission to scan.

**What `fierce` Does:**

`fierce` primarily focuses on:

* **DNS Enumeration:**  It retrieves various DNS records (A, AAAA, MX, NS, CNAME, SOA, TXT) to gain insights into the target domain's infrastructure.
* **Subdomain Discovery:** It uses a combination of techniques, including dictionary-based brute-forcing, zone transfers (if allowed), and querying search engines, to discover subdomains that might not be immediately obvious.
* **Reverse Lookups:** It can perform reverse DNS lookups to identify hostnames associated with specific IP addresses.
* **Banner Grabbing:** It attempts to retrieve banner information from services running on discovered subdomains, which can reveal software versions and potential vulnerabilities.

**Key Features and Capabilities:**

* **Subdomain Brute-forcing:** Uses wordlists to guess potential subdomains.
* **DNS Zone Transfer:** Attempts to perform a zone transfer to retrieve the entire DNS zone information (often blocked by servers).
* **Reverse DNS Lookups:** Identifies hostnames associated with IP addresses.
* **Banner Grabbing:** Retrieves banner information from services.
* **Output to various formats:** Can save results in different formats for further analysis.


### **Basic Usage:**
```bash
fierce -dns example.com
```
This command runs a basic DNS enumeration against `example.com`.

* `fierce`: The command to execute the tool.
* `[options]`: The flags and parameters you can use to customize the scan.

**Options:**

* `-h, --help`: Displays this help message and exits.

* `--domain DOMAIN`:  **Required.** Specifies the target domain (e.g., `--domain example.com`).  This is the domain you want to perform reconnaissance on.

* `--connect`: Attempts an HTTP connection to discovered IP addresses that are *not* within RFC 1918 private address space (like 192.168.x.x, 10.x.x.x, 172.16.x.x).  This can help identify web servers running on those IPs.

* `--wide`: Scans the entire Class C network (e.g., 192.168.1.0/24) of discovered records.  If `fierce` finds a record like `mail.example.com` resolving to 192.168.1.10, it will then scan the entire 192.168.1.0/24 range.

* `--traverse TRAVERSE`: Scans IP addresses near discovered records.  The difference between `--wide` and `--traverse` is that `--traverse` will *not* scan adjacent Class C networks.  It stays within the same Class C.

* `--search SEARCH [SEARCH ...]`: Filters the domains used for expansion.  This allows you to specify keywords.  For example, if you're only interested in mail servers, you could use `--search mail`.

* `--range RANGE`: Scans a specific internal IP address range using CIDR notation (e.g., `--range 192.168.1.0/24`).  This is useful for internal network scanning.

* `--delay DELAY`: Sets the time to wait between DNS lookups (in seconds).  This helps to be polite and avoid overwhelming the target's DNS servers.

* `--subdomains SUBDOMAINS [SUBDOMAINS ...]`: Specifies a list of subdomains to use for brute-forcing (e.g., `--subdomains www mail ftp`).

* `--subdomain-file SUBDOMAIN_FILE`: Specifies a file containing a list of subdomains (one per line) to use for brute-forcing.  This is a more practical way to use a large wordlist.

* `--dns-servers DNS_SERVERS [DNS_SERVERS ...]`: Specifies a list of DNS servers to use for reverse lookups (e.g., `--dns-servers 8.8.8.8 8.8.4.4`).

* `--dns-file DNS_FILE`: Specifies a file containing a list of DNS servers (one per line) to use for reverse lookups.

* `--tcp`: Uses TCP instead of UDP for DNS queries.  TCP is generally used for larger DNS responses, like zone transfers.



### **Example Commands:**

 **Basic domain scan:**
   ```bash
   fierce -dns example.com
   ```

 **Use a custom wordlist for subdomain brute-forcing:**
   ```bash
   fierce -dns example.com -wordlist subdomains.txt
   ```

 **Scan an IP range for hosts:**
   ```bash
   fierce -range 192.168.1.0-255
   ```

 **Save results to a file:**
   ```bash
   fierce -dns example.com -output results.txt
   ```

. **Increase threads for faster scanning:**
   ```bash
   fierce -dns example.com -threads 10
   ```
 **Scanning a Class C network:**
  ```bash
  fierce --domain example.com --wide
  ```

 **Using a subdomain file:**
  ```bash
  fierce --domain example.com --subdomain-file subdomains.txt
  ```

 **Specifying DNS servers:**
  ```bash
  fierce --domain example.com --dns-servers 8.8.8.8 1.1.1.1
  ```

 **Using TCP:**
  ```bash
  fierce --domain example.com --tcp
  ```
---

### **When to Use Fierce?**
- **During reconnaissance** in a penetration test.
- **To find hidden subdomains** that may reveal admin portals or APIs.
- **To locate IP ranges** associated with a target.
- **As a passive recon tool** before launching active attacks.

