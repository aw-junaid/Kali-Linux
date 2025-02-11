![dmitry.png](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/Images/dmitry.png)

`dmitry` (Deep Magic Information Gathering Tool) is a classic, though somewhat dated, open-source tool used for gathering information about a target host or domain. It can perform various tasks, including WHOIS lookups, port scans, subdomain searches, email address harvesting, and more. While some of its features overlap with newer tools like `amass` or `theHarvester`, it still has some use cases, particularly for quick, basic reconnaissance.

**What `dmitry` Does:**

`dmitry` automates the process of collecting information about a target, including:

* **WHOIS Lookups:** Retrieves WHOIS records to get information about domain registration.
* **Port Scanning:** Scans for open ports on the target host.
* **Subdomain Search:** Tries to find subdomains using various techniques.
* **Email Address Harvesting:** Attempts to find email addresses associated with the target domain.
* **Banner Grabbing:** Retrieves banners from services running on open ports.
* **TCP/IP Stack Fingerprinting:** Attempts to identify the operating system of the target host.

**Key Features and Capabilities:**

* **Information Gathering:** Collects various types of information about a target.
* **Multiple Techniques:** Uses different methods for information gathering.
* **Command-Line Interface:** Easy to use and scriptable.

**How to Use `dmitry`:**

 **Installation:** `dmitry` is often available in package repositories for various Linux distributions (e.g., `apt-get install dmitry` on Debian/Ubuntu).  However, it's an older tool, so you might need to compile it from source if your distribution doesn't have it readily available.

**Basic Usage:**

```bash
dmitry [-winsepfb] [-t 0-9] [-o %host.txt] host
```

**Options:**

* `-o`: Save output to `%host.txt` (or to the file specified by `-o file`).  If you just use `-o`, the output will be saved to a file named after the target host.  If you want to specify a different filename, use `-o <filename>`.
* `-i`: Perform a WHOIS lookup on the IP address of a host.
* `-w`: Perform a WHOIS lookup on the domain name of a host.
* `-n`: Retrieve Netcraft.com information on a host (Note: Netcraft has changed a lot since this tool was written; this feature might not work as expected anymore).
* `-s`: Perform a search for possible subdomains.
* `-e`: Perform a search for possible email addresses.
* `-p`: Perform a TCP port scan on a host.
* `-f`: Perform a TCP port scan and report filtered ports.  This is a more detailed port scan than `-p`.  It shows ports that are closed *and* ports that are filtered by a firewall.
* `-b`: Read in the banner received from the scanned port.  This retrieves the banner (a short identifying message) from services running on open ports.
* `-t 0-9`: Set the TTL (Time To Live) in seconds when scanning a TCP port (default is 2).  This controls how many hops the port scan packets can take.  A higher TTL might be needed to reach hosts behind routers or firewalls, but it also makes the scan slower.

**Argument:**

* `host`: The target host (IP address or hostname).  This is *required*.

## **🛠️Examples**

### **1️⃣ WHOIS Lookups**
#### **Get WHOIS for Domain**
```bash
dmitry -w example.com

Deepmagic Information Gathering Tool
"There be some deep magic going on"

HostIP:23.192.228.80
HostName:example.com

Gathered Inic-whois information for example.com
---------------------------------
   Domain Name: EXAMPLE.COM
   Registry Domain ID: 2336799_DOMAIN_COM-VRSN
   Registrar WHOIS Server: whois.iana.org
   Registrar URL: http://res-dom.iana.org
   Updated Date: 2024-08-14T07:01:34Z
   Creation Date: 1995-08-14T04:00:00Z
   Registry Expiry Date: 2025-08-13T04:00:00Z
   Registrar: RESERVED-Internet Assigned Numbers Authority
   Registrar IANA ID: 376
   Registrar Abuse Contact Email:
   Registrar Abuse Contact Phone:
   Domain Status: clientDeleteProhibited https://icann.org/epp#clientDeleteProhibited
   Domain Status: clientTransferProhibited https://icann.org/epp#clientTransferProhibited
   Domain Status: clientUpdateProhibited https://icann.org/epp#clientUpdateProhibited
   Name Server: A.IANA-SERVERS.NET
   Name Server: B.IANA-SERVERS.NET
   DNSSEC: signedDelegation
   DNSSEC DS Data: 370 13 2 BE74359954660069D5C63D200C39F5603827D7DD02B56F120EE9F3A86764247C
   URL of the ICANN Whois Inaccuracy Complaint Form: https://www.icann.org/wicf/
>>> Last update of whois database: 2025-02-11T11:12:41Z <<<

For more information on Whois status codes, please visit https://icann.org/epp

NOTICE: The expiration date displayed in this record is the date the
registrar's sponsorship of the domain name registration in the registry is
currently set to expire. This date does not necessarily reflect the expiration
date of the domain name registrant's agreement with the sponsoring
registrar.  Users may consult the sponsoring registrar's Whois database to
view the registrar's reported date of expiration for this registration.

TERMS OF USE: You are not authorized to access or query our Whois
database through the use of electronic processes that are high-volume and
automated except as reasonably necessary to register domain names or
modify existing registrations; the Data in VeriSign Global Registry
Services' ("VeriSign") Whois database is provided by VeriSign for
information purposes only, and to assist persons in obtaining information
about or related to a domain name registration record. VeriSign does not
guarantee its accuracy. By submitting a Whois query, you agree to abide
by the following terms of use: You agree that you may use this Data only
for lawful purposes and that under no circumstances will you use this Data
to: (1) allow, enable, or otherwise support the transmission of mass
unsolicited, commercial advertising or solicitations via e-mail, telephone,
or facsimile; or (2) enable high volume, automated, electronic processes
that apply to VeriSign (or its computer systems). The compilation,
repackaging, dissemination or other use of this Data is expressly
prohibited without the prior written consent of VeriSign. You agree not to
use electronic processes that are automated and high-volume to access or
query the Whois database except as reasonably necessary to register
domain names or modify existing registrations. VeriSign reserves the right
to restrict your access to the Whois database in its sole discretion to ensure
operational stability.  VeriSign may restrict or terminate your access to the
Whois database for failure to abide by these terms of use. VeriSign
reserves the right to modify these terms at any time.

The Registry database contains ONLY .COM, .NET, .EDU domains and
Registrars.

All scans completed, exiting

```
✔️ Retrieves **WHOIS records** of `example.com`.

#### **Get WHOIS for IP Address**
```bash
dmitry -i example.com
```
✔️ Resolves the **IP address** and performs **WHOIS** on it.

---

### **2️⃣ Netcraft Information**
```bash
dmitry -n example.com
```
✔️ Fetches **Netcraft.com information** on `example.com`.

---

### **3️⃣ Subdomain Enumeration**
```bash
dmitry -s example.com
```
✔️ Searches for **subdomains**.

---

### **4️⃣ Email Address Search**
```bash
dmitry -e example.com
```
✔️ Extracts **email addresses** from the domain.

---

### **5️⃣ TCP Port Scanning**
#### **Basic Port Scan**
```bash
dmitry -p example.com
```
✔️ Performs a **TCP port scan** to detect open ports.

#### **Show Filtered Ports in Scan**
```bash
dmitry -pf example.com
```
✔️ Displays **filtered ports** in the scan.

#### **Banner Grabbing**
```bash
dmitry -pb example.com
```
✔️ **Identifies services** running on open ports.

#### **Set Port Scan TTL (Timeout)**
```bash
dmitry -p -t 5 example.com
```
✔️ Sets **TTL (time-to-live)** for TCP scans (default: 2 seconds).

---

### **6️⃣ Save Output to File**
```bash
dmitry -o results.txt example.com
```
✔️ Saves scan results to `results.txt`.

---

## **🚀 Full Scan Example**
```bash
dmitry -winsep -o full_scan.txt example.com
```

**Interpreting the Results:**

`dmitry` outputs the collected information, including WHOIS details, website information, open ports, subdomains, email addresses, and banners.

**Key Considerations:**

* **Dated Tool:** `dmitry` is an older tool, and some of its features might be less effective compared to newer tools.
* **Limited Features:**  It lacks some advanced features found in modern tools.
* **Accuracy:**  The accuracy of some of the information gathered (e.g., email addresses) might be limited.
* **Ethical Use:** Only use `dmitry` on targets that you have explicit permission to test. Unauthorized scanning is illegal and unethical.

**When to Use `dmitry`:**

* For quick, basic reconnaissance.
* In situations where newer tools are not available.
* As part of a larger information-gathering process, combined with other tools.

While `dmitry` might not be the most advanced tool available, it can still be useful for basic information gathering.  However, it's generally recommended to use newer and more feature-rich tools like `amass`, `theHarvester`, or others for more comprehensive reconnaissance.  Always use these tools responsibly and ethically, and only on systems you have permission to test.
