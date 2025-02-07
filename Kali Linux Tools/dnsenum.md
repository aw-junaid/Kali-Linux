![DNSenum](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/Images/dnsneum.png)

`DNSenum` is a powerful DNS enumeration tool used to gather information about a domain. It is commonly used in penetration testing and reconnaissance to discover DNS information, such as subdomains, MX records, nameservers, and more.

---

### **Installation**
`DNSenum` is pre-installed on many penetration testing distributions like Kali Linux. If it's not installed, you can install it using the following steps:

1. **On Debian-based systems (e.g., Kali Linux)**:
   ```bash
   sudo apt update
   sudo apt install dnsenum
   ```

2. **On other Linux distributions**:
   - Download the script from its [GitHub repository](https://github.com/fwaeytens/dnsenum).
   - Make it executable:
     ```bash
     chmod +x dnsenum.pl
     ```

---

### **Basic Usage**
The general syntax for `DNSenum` is:
```bash
dnsenum [options] <domain>
```

#### Example:
```bash
dnsenum example.com
```

---

### **General Usage**
The basic syntax for `DNSenum` is:
```bash
dnsenum [Options] <domain>
```
- Replace `<domain>` with the target domain you want to enumerate (e.g., `example.com`).

---

### **General Options**
These options control the overall behavior of `DNSenum`.

| Option                  | Description                                                                 |
|-------------------------|-----------------------------------------------------------------------------|
| `--dnsserver <server>`  | Use a specific DNS server for A, NS, and MX queries.                        |
| `--enum`                | Shortcut for `--threads 5 -s 15 -w` (performs a full enumeration).          |
| `-h, --help`            | Display this help menu.                                                     |
| `--noreverse`           | Skip reverse DNS lookups.                                                   |
| `--nocolor`             | Disable colored output in the terminal.                                     |
| `--private`             | Show and save private IP addresses in a file named `domain_ips.txt`.        |
| `--subfile <file>`      | Save all valid subdomains to the specified file.                            |
| `-t, --timeout <value>` | Set the TCP/UDP timeout in seconds (default: 10 seconds).                   |
| `--threads <value>`     | Set the number of threads for parallel queries (default: 5).                |
| `-v, --verbose`         | Enable verbose mode to show progress and error messages.                    |

---

### **Google Scraping Options**
These options control how `DNSenum` scrapes subdomains from Google search results.

| Option                  | Description                                                                 |
|-------------------------|-----------------------------------------------------------------------------|
| `-p, --pages <value>`   | Number of Google search pages to process (default: 5).                      |
| `-s, --scrap <value>`   | Maximum number of subdomains to scrape from Google (default: 15).           |

---

### **Brute Force Options**
These options control the brute-forcing of subdomains.

| Option                  | Description                                                                 |
|-------------------------|-----------------------------------------------------------------------------|
| `-f, --file <file>`     | Use a custom wordlist file for brute-forcing subdomains.                    |
| `-u, --update <a|g|r|z>`| Update the wordlist file (`-f`) with valid subdomains:                      |
|                         | `a` (all): Update using all results.                                        |
|                         | `g`: Update using only Google scraping results.                             |
|                         | `r`: Update using only reverse lookup results.                              |
|                         | `z`: Update using only zone transfer results.                               |
| `-r, --recursion`       | Perform recursive brute-forcing on discovered subdomains with NS records.   |

---

### **WHOIS Netrange Options**
These options control WHOIS queries for network ranges.

| Option                  | Description                                                                 |
|-------------------------|-----------------------------------------------------------------------------|
| `-d, --delay <value>`   | Maximum delay (in seconds) between WHOIS queries (default: 3 seconds).      |
| `-w, --whois`           | Perform WHOIS queries on C-class network ranges.                            |
|                         | **Warning**: This can generate large netranges and take a long time.        |

---

### **Reverse Lookup Options**
These options control reverse DNS lookups.

| Option                  | Description                                                                 |
|-------------------------|-----------------------------------------------------------------------------|
| `-e, --exclude <regexp>`| Exclude PTR records matching the regexp from reverse lookup results.        |

---

### **Output Options**
These options control the output format and file.

| Option                  | Description                                                                 |
|-------------------------|-----------------------------------------------------------------------------|
| `-o, --output <file>`   | Save the results in XML format (can be imported into MagicTree).            |

---


### **Step-by-Step Guide**

#### 1. **Basic Enumeration**
To perform a basic DNS enumeration:
```bash
dnsenum example.com
```
This will:
- Perform a zone transfer (if possible).
- Enumerate subdomains using Google scraping.
- Perform reverse DNS lookups.

---

#### 2. **Brute-Force Subdomains**
To brute-force subdomains using a custom wordlist:
```bash
dnsenum -f wordlist.txt example.com
```
- Replace `wordlist.txt` with the path to your wordlist file.
- This will attempt to find subdomains by appending words from the wordlist to the domain.

---

#### 3. **Save Output to a File**
To save the results to an XML file:
```bash
dnsenum -o output.xml example.com
```
- The output will be saved in `output.xml`.

---

#### 4. **Use a Specific DNS Server**
To use a specific DNS server for queries:
```bash
dnsenum --dnsserver 8.8.8.8 example.com
```
```bash
┌──(komugi㉿komugi)-[~]
└─$ dnsenum --dnsserver 8.8.8.8 example.com
dnsenum VERSION:1.3.1

-----   example.com   -----                                                                                                                         
                                                                                                                                                    
                                                                                                                                                    
Host's addresses:                                                                                                                                   
__________________                                                                                                                                  
                                                                                                                                                    
example.com.                             75       IN    A        23.192.228.80                                                                      
example.com.                             75       IN    A        96.7.128.175
example.com.                             75       IN    A        23.215.0.138
example.com.                             75       IN    A        96.7.128.198
example.com.                             75       IN    A        23.215.0.136
example.com.                             75       IN    A        23.192.228.84

                                                                                                                                                    
Name Servers:                                                                                                                                       
______________                                                                                                                                      
                                                                                                                                                    
b.iana-servers.net.                      819      IN    A        199.43.133.53                                                                      
a.iana-servers.net.                      720      IN    A        199.43.135.53

                                                                                                                                                    
Mail (MX) Servers:                                                                                                                                  
___________________                                                                                                                                 
                                                                                                                                                    
                                                                                                                                                    
                                                                                                                                                    
Trying Zone Transfers and getting Bind Versions:                                                                                                    
_________________________________________________                                                                                                   
                                                                                                                                                    
                                                                                                                                                    
Trying Zone Transfer for example.com on b.iana-servers.net ... 
AXFR record query failed: REFUSED

Trying Zone Transfer for example.com on a.iana-servers.net ... 
AXFR record query failed: NOTAUTH

                                                                                                                                                    
Brute forcing with /usr/share/dnsenum/dns.txt:                                                                                                      
_______________________________________________                                                                                                     
```
- Replace `8.8.8.8` with the IP address of the DNS server you want to use.

---

#### 5. **Increase Threads for Faster Enumeration**
To increase the number of threads for faster enumeration:
```bash
dnsenum --threads 10 example.com
```
- This will use 10 threads instead of the default 5.

---

#### 6. **Skip Reverse DNS Lookups**
To skip reverse DNS lookups:
```bash
dnsenum --noreverse example.com
```

---

#### 7. **Full Enumeration**
To perform a full enumeration (default behavior):
```bash
dnsenum --enum example.com
```

---

### **Advanced Usage**

#### 1. **Brute-Force with Recursion**
To enable recursive brute-forcing of subdomains:
```bash
dnsenum -r example.com
```
- This will attempt to brute-force subdomains of subdomains.

---

#### 2. **Show Private IP Addresses**
To include private IP addresses in the results:
```bash
dnsenum --private example.com
```

---

#### 3. **Only Enumerate Subdomains**
To only enumerate subdomains:
```bash
dnsenum --subdomains example.com
```

---

### **Example Commands**

1. **Basic enumeration with output saved to a file**:
   ```bash
   dnsenum -o results.xml example.com
   ```

2. **Brute-force subdomains with a custom wordlist**:
   ```bash
   dnsenum -f wordlist.txt example.com
   ```

3. **Full enumeration with 10 threads**:
   ```bash
   dnsenum --threads 10 --enum example.com
   ```

---

### **Output Explanation**
The output of `DNSenum` includes:
- **Hostnames**: Discovered subdomains.
- **IP Addresses**: Resolved IP addresses for the subdomains.
- **Nameservers**: Authoritative nameservers for the domain.
- **MX Records**: Mail exchange records.
- **Zone Transfers**: Results of zone transfer attempts.
- **Reverse DNS**: Reverse DNS lookup results.

---

### **Tips**
- Use a **custom wordlist** for better results in brute-forcing subdomains.
- Combine `DNSenum` with other tools like `Sublist3r` or `Amass` for comprehensive reconnaissance.
- Always ensure you have **proper authorization** before performing DNS enumeration on a domain.

---
