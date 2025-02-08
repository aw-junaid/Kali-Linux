![spiderfoot](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/Images/spiderfoot.png)

### What is **SpiderFoot**?

**SpiderFoot** is an open-source reconnaissance tool designed for **OSINT (Open-Source Intelligence)** gathering. It automates the process of collecting information about a target (e.g., domain, IP address, email, or username) from hundreds of public data sources. SpiderFoot is widely used by security professionals, penetration testers, and threat intelligence analysts to gather data for footprinting, reconnaissance, and threat analysis.

---

### **Key Features of SpiderFoot**
1. **Automated OSINT Collection**:
   - Gathers data from over 200 data sources, including search engines, social media, DNS records, WHOIS, and more.
2. **Modular Design**:
   - Supports modules for specific types of data collection (e.g., DNS lookups, IP geolocation, email harvesting).
3. **Customizable Scans**:
   - Allows users to configure which modules to run and how deep the scan should go.
4. **Data Visualization**:
   - Provides graphical representations of relationships between entities (e.g., domains, IPs, emails).
5. **Integration**:
   - Can integrate with tools like Maltego and databases like SQLite.
6. **Cross-Platform**:
   - Runs on Linux, macOS, and Windows.

---

**Basic Usage:**

```bash
sf.py [-h] [-d] [-l IP:port] [-m mod1,mod2,...] [-M] [-C scanID] [-s TARGET] [-t type1,type2,...] [-u {all,footprint,investigate,passive}] [-T] [-o {tab,csv,json}] [-H] [-n] [-r] [-S LENGTH] [-D DELIMITER] [-f] [-F type1,type2,...] [-x] [-q] [-V] [-max-threads MAX_THREADS]
```

**Options:**

* `-h, --help`: Show this help message and exit.
* `-d, --debug`: Enable debug output.
* `-l IP:port`: IP and port to listen on (for the web interface).
* `-m mod1,mod2,...`: Modules to enable (comma-separated list).
* `-M, --modules`: List available modules.
* `-C scanID, --correlate scanID`: Run correlation rules against a scan ID. This is for post-processing results from a previous scan.
* `-s TARGET`: Target for the scan (e.g., domain, IP address, email).  This is *required*.
* `-t type1,type2,...`: Event types to collect (comma-separated list). This automatically selects relevant modules.  Use `-T` to list available event types.
* `-u {all,footprint,investigate,passive}`: Select modules automatically by use case:
    * `all`: All modules.
    * `footprint`: Modules for basic footprinting.
    * `investigate`: Modules for in-depth investigation.
    * `passive`: Passive reconnaissance modules.
* `-T, --types`: List available event types.
* `-o {tab,csv,json}`: Output format (tab-separated, CSV, or JSON). Default is tab-separated.
* `-H`: Don't print field headers (only data).
* `-n`: Strip newlines from data.
* `-r`: Include the source data field in tab/CSV output.
* `-S LENGTH`: Maximum data length to display. By default, all data is shown.
* `-D DELIMITER`: Delimiter to use for CSV output (default is comma).
* `-f`: Filter out other event types that weren't requested with `-t`.
* `-F type1,type2,...`: Show only a set of event types (comma-separated).
* `-x`: Strict mode. Only enables modules that can directly consume your target. Overrides `-t` and `-m`.
* `-q`: Disable logging (hides errors as well!).
* `-V, --version`: Display the version of SpiderFoot and exit.
* `-max-threads MAX_THREADS`: Maximum number of modules to run concurrently.


### **SpiderFoot**

#### **Installation**
SpiderFoot can be installed in several ways:

1. **Using Docker** (recommended):
   ```bash
   docker run -p 5001:5001 spiderfoot
   ```
   Access the web interface at `http://localhost:5001`.

2. **From Source**:
   - Clone the repository:
     ```bash
     git clone https://github.com/smicallef/spiderfoot.git
     ```
   - Install dependencies:
     ```bash
     cd spiderfoot
     pip3 install -r requirements.txt
     ```
   - Run SpiderFoot:
     ```bash
     python3 sf.py -l 127.0.0.1:5001
     ```
   - Access the web interface at `http://127.0.0.1:5001`.

3. **Pre-Installed on Kali Linux**:
   - SpiderFoot is included in Kali Linux. Launch it from the terminal:
     ```bash
     spiderfoot
     ```

---

### **Using the Web Interface**
1. **Start a New Scan**:
   - Go to the "New Scan" tab.
   - Enter the target (e.g., domain, IP, email, or username).
   - Choose the scan type (e.g., "Footprint," "Investigate," or "Passive").
   - Select the modules to run (or use the default selection).
   - Click "Run Scan."

2. **Monitor the Scan**:
   - The scan progress is displayed in real-time.
   - Results are categorized by type (e.g., IP addresses, domains, emails).

3. **View Results**:
   - Results are displayed in a table format.
   - Use the "Graph" tab to visualize relationships between entities.
   - Export results in formats like CSV, JSON, or GEXF.

---

### **Command-Line Usage**
SpiderFoot can also be run from the command line for automation or scripting purposes.

#### Basic Syntax:
```bash
python3 sf.py -t <target> -m <modules> -s <scan_name>
```

#### Example:
```bash
python3 sf.py -t example.com -m all -s example_scan
```
- `-t`: Target (e.g., domain, IP, email).
- `-m`: Modules to run (e.g., `all` for all modules).
- `-s`: Name of the scan.

---

### **Common Modules**
- **DNS Lookup**: Resolves DNS records for the target.
- **WHOIS Lookup**: Retrieves domain registration details.
- **IP Geolocation**: Maps IP addresses to physical locations.
- **Email Harvesting**: Collects email addresses associated with the target.
- **Social Media Lookup**: Searches for social media profiles.
- **Port Scanning**: Scans for open ports on IP addresses.

---

### **Example Use Cases**
1. **Domain Reconnaissance**:
   - Gather information about a domain, including subdomains, DNS records, and associated IPs.
   ```bash
   python3 sf.py -t example.com -m dns,whois,ipgeo
   ```

2. **Email Investigation**:
   - Find information about an email address, such as associated accounts and data breaches.
   ```bash
   python3 sf.py -t user@example.com -m email,breach
   ```

3. **Threat Intelligence**:
   - Collect data about an IP address, including geolocation and open ports.
   ```bash
   python3 sf.py -t 192.168.1.100 -m ipgeo,portscan
   ```

4. **Social Media Profiling**:
   - Search for social media profiles associated with a username.
   ```bash
   python3 sf.py -t username -m socialmedia
   ```

---

### **Tips for Effective Use**
- **Start with Passive Modules**: Use passive modules (e.g., `whois`, `dns`) to avoid alerting the target.
- **Limit Scope**: Use specific modules to avoid overwhelming results.
- **Visualize Data**: Use the "Graph" tab to understand relationships between entities.
- **Export Results**: Export data for further analysis in tools like Maltego or Excel.

---

### **Limitations**
- **Rate Limits**: Some data sources may impose rate limits, slowing down scans.
- **False Positives**: Verify results, as some data may be outdated or incorrect.
- **Ethical Use**: Always ensure you have permission to scan the target.

---

### **Resources**
- [SpiderFoot GitHub Repository](https://github.com/smicallef/spiderfoot)
- [SpiderFoot Documentation](https://www.spiderfoot.net/documentation/)

---
