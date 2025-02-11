![recon-ng](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/Images/recon-ng.png)

**Recon-ng** is a powerful open-source **web reconnaissance framework** written in Python. It is designed for conducting **information gathering** and **open-source intelligence (OSINT)** during penetration testing or security assessments. Recon-ng provides a modular approach, allowing users to leverage a wide range of modules for tasks like domain enumeration, subdomain discovery, port scanning, data harvesting, and more.

Recon-ng is highly customizable and is often compared to **Metasploit** due to its similar interface and workflow. However, Recon-ng is focused solely on reconnaissance and does not include exploitation capabilities.

---

### **Key Features of Recon-ng**
1. **Modular Design**: Over 300+ modules for various reconnaissance tasks.
2. **Database Integration**: Stores results in a database for easy querying and analysis.
3. **API Integration**: Supports integration with third-party APIs (e.g., Shodan, Hunter.io, etc.).
4. **Automation**: Allows scripting and automation of reconnaissance workflows.
5. **Cross-Platform**: Works on Linux, macOS, and Windows (with Python installed).

---

### **Installation**
Recon-ng is pre-installed in Kali Linux. For other systems, follow these steps:

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/lanmaster53/recon-ng.git
   ```
2. **Install Dependencies**:
   ```bash
   cd recon-ng
   pip install -r REQUIREMENTS
   ```
3. **Run Recon-ng**:
   ```bash
   ./recon-ng
   ```

---

##### ✅ Install Modules
```bash
marketplace refresh  # Refresh the marketplace
marketplace install all  # Install all available modules
```
Now, check if the modules are installed:
```bash
modules search
```
If you’re looking for specific modules:
```bash
marketplace search hosts
marketplace search domains
```

#### **2. Module Names**
When loading a module, you need to **use the correct module name**. If you previously installed them, you can check with:
```bash
show modules
```
Then, load a module:
```bash
modules load recon/domains-hosts/hackertarget
```

#### **3. correct `set SOURCE` Usage**
After loading a module, set the required options correctly:
```bash
set SOURCE example.com
```
If `set` isn’t working, first check available options:
```bash
options
```

#### **4. Database Not Initialized**
Make sure the database is set up before running any queries:
```bash
db init
```


### **Basic Usage**
1. **Start Recon-ng**:
   ```bash
   recon-ng
   ```
   You will enter the Recon-ng interactive shell.

2. **View Modules**:
   ```bash
   show modules
   ```
   This lists all available modules.

4. **Search for Modules**:
   ```bash
   search <keyword>
   ```
   Example:
   ```bash
   search shodan
   ```

5. **Load a Module**:
   ```bash
   use <module_path>
   ```
   Example:
   ```bash
   use recon/domains-hosts/hackertarget
   ```

6. **Show Module Info**:
   ```bash
   info
   ```
   Displays details about the loaded module, including options and descriptions.

7. **Set Module Options**:
   ```bash
   options set <option_name> <value>
   ```
   Example:
   ```bash
   options set SOURCE example.com
   ```

8. **Run the Module**:
   ```bash
   run
   ```
   Executes the module with the configured options.

9. **View Results**:
   ```bash
   show hosts
   ```
   Displays the results stored in the database.

---

### **Core Commands in Recon-ng**

#### **1. `back`**
- **Description**: Exits the current context (e.g., exits a module and returns to the main menu).
- **Usage**:
  ```bash
  back
  ```

#### **2. `dashboard`**
- **Description**: Displays a summary of activity, including the number of hosts, contacts, and vulnerabilities discovered.
- **Usage**:
  ```bash
  dashboard
  ```

#### **3. `db`**
- **Description**: Interfaces with the workspace's database. Allows you to query, insert, update, or delete records.
- **Usage**:
  ```bash
  db query "SELECT * FROM hosts"
  ```
  Example:
  ```bash
  db insert hosts (host, ip) VALUES ('example.com', '192.168.1.1')
  ```

#### **4. `exit`**
- **Description**: Exits the Recon-ng framework.
- **Usage**:
  ```bash
  exit
  ```

#### **5. `help`**
- **Description**: Displays the help menu or provides information about a specific command or topic.
- **Usage**:
  ```bash
  help
  ```
  Example:
  ```bash
  help db
  ```

#### **6. `index`**
- **Description**: Creates a module index (used by developers only).
- **Usage**:
  ```bash
  index
  ```

#### **7. `keys`**
- **Description**: Manages third-party API keys required by certain modules (e.g., Shodan, Hunter.io).
- **Usage**:
  ```bash
  keys add <service> <api_key>
  ```
  Example:
  ```bash
  keys add shodan_api YOUR_SHODAN_API_KEY
  ```

#### **8. `marketplace`**
- **Description**: Interfaces with the module marketplace. Allows you to search, install, or update modules.
- **Usage**:
  ```bash
  marketplace search <keyword>
  ```
  Example:
  ```bash
  marketplace install recon/domains-hosts/hackertarget
  ```

#### **9. `modules`**
- **Description**: Interfaces with installed modules. Allows you to load, reload, or search for modules.
- **Usage**:
  ```bash
  modules search <keyword>
  ```
  Example:
  ```bash
  modules load recon/domains-hosts/hackertarget
  ```

#### **10. `options`**
- **Description**: Manages the current context options (e.g., sets options for a loaded module).
- **Usage**:
  ```bash
  options set <option_name> <value>
  ```
  Example:
  ```bash
  options set SOURCE example.com
  ```

#### **11. `pdb`**
- **Description**: Starts a Python Debugger session (used by developers only).
- **Usage**:
  ```bash
  pdb
  ```

#### **12. `script`**
- **Description**: Records and executes command scripts. Useful for automating workflows.
- **Usage**:
  ```bash
  script record <filename>
  ```
  Example:
  ```bash
  script execute /path/to/script.rc
  ```

#### **13. `shell`**
- **Description**: Executes shell commands directly from the Recon-ng interface.
- **Usage**:
  ```bash
  shell <command>
  ```
  Example:
  ```bash
  shell ls -la
  ```

#### **14. `show`**
- **Description**: Shows various framework items, such as modules, options, or database tables.
- **Usage**:
  ```bash
  show <item>
  ```
  Examples:
  ```bash
  show modules
  show options
  show hosts
  ```

#### **15. `snapshots`**
- **Description**: Manages workspace snapshots. Allows you to save or restore the state of a workspace.
- **Usage**:
  ```bash
  snapshots save <name>
  ```
  Example:
  ```bash
  snapshots restore example_snapshot
  ```

#### **16. `spool`**
- **Description**: Spools (saves) output to a file.
- **Usage**:
  ```bash
  spool start <filename>
  spool stop
  ```

#### **17. `workspaces`**
- **Description**: Manages workspaces. Allows you to create, delete, or switch between workspaces.
- **Usage**:
  ```bash
  workspaces create <name>
  ```
  Example:
  ```bash
  workspaces load example_workspace
  ```

---

### **Example Workflow Using Commands**
1. **Create a Workspace**:
   ```bash
   workspaces create example_workspace
   ```

2. **Load a Module**:
   ```bash
   use recon/domains-hosts/hackertarget
   ```

3. **Set Module Options**:
   ```bash
   options set SOURCE example.com
   ```

4. **Run the Module**:
   ```bash
   run
   ```

5. **View Results**:
   ```bash
   show hosts
   ```

6. **Export Results**:
   ```bash
   use reporting/html
   options set CREATOR "Your Name"
   options set CUSTOMER "Example Corp"
   run
   ```

7. **Exit Recon-ng**:
   ```bash
   exit
   ```
---

By mastering these commands, you can efficiently use Recon-ng to conduct thorough reconnaissance and gather valuable intelligence for your security assessments.

### **Common Modules**
1. **Domain Enumeration**:
   - `recon/domains-hosts/hackertarget`: Enumerates subdomains using HackerTarget API.
   - `recon/domains-hosts/certificate_transparency`: Finds subdomains via SSL certificates.

2. **Port Scanning**:
   - `recon/hosts-ports/shodan`: Uses Shodan to discover open ports.

3. **Data Harvesting**:
   - `recon/contacts-profiles/linkedin`: Harvests LinkedIn profiles.
   - `recon/contacts-profiles/twitter`: Harvests Twitter profiles.

4. **Vulnerability Discovery**:
   - `recon/vulnerabilities/xssed`: Searches for XSS vulnerabilities.

5. **Reporting**:
   - `reporting/html`: Generates an HTML report of the findings.

---


### **Advanced Features**

## **🔧 Add Required API Keys**
Many modules in **Recon-ng** require API keys to function. You need to **register for API keys** from different services and add them manually.

### **1️⃣ Get API Keys from Required Services**
You need to sign up for API keys from these platforms:
- **Google API** → [Google Cloud Console](https://console.cloud.google.com/)
- **Shodan API** → [Shodan](https://www.shodan.io/)
- **VirusTotal API** → [VirusTotal](https://www.virustotal.com/)
- **Censys API** → [Censys](https://censys.io/)
- **Hunter.io API** → [Hunter.io](https://hunter.io/)
- **GitHub API** → [GitHub Developer](https://github.com/settings/tokens)
- **Twitter API** → [Twitter Developer](https://developer.twitter.com/)
- **Bing API** → [Bing Search API](https://www.microsoft.com/en-us/bing/apis/bing-search-api-v7)
- **BinaryEdge API** → [BinaryEdge](https://binaryedge.io/)
- **IPStack API** → [IPStack](https://ipstack.com/)
- **HIBP (Have I Been Pwned)** → [HIBP API](https://haveibeenpwned.com/)

---

### **2️⃣ Add API Keys in Recon-ng**
Once you have the API keys, add them to Recon-ng using:
```bash
keys add google_api YOUR_GOOGLE_API_KEY
keys add shodan_api YOUR_SHODAN_API_KEY
keys add virustotal_api YOUR_VIRUSTOTAL_API_KEY
keys add censysio_id YOUR_CENSYS_ID
keys add censysio_secret YOUR_CENSYS_SECRET
keys add hunter_io YOUR_HUNTER_IO_API_KEY
keys add github_api YOUR_GITHUB_API_KEY
keys add twitter_api YOUR_TWITTER_API_KEY
keys add twitter_secret YOUR_TWITTER_SECRET
keys add bing_api YOUR_BING_API_KEY
keys add binaryedge_api YOUR_BINARYEDGE_API_KEY
keys add ipstack_api YOUR_IPSTACK_API_KEY
keys add hibp_api YOUR_HIBP_API_KEY
```
**To verify the keys were added correctly:**
```bash
keys list
```

---

## **🔍 Fix Module Dependency Errors**
You have **missing dependencies** (`PyPDF3`, `CensysCertificates`, etc.), so you need to install them manually.

### ✅ **Fix Dependencies (Python Packages)**
Run:
```bash
pip install PyPDF3 censys
```
If using Kali Linux:
```bash
apt install python3-pypdf3 python3-censys -y
```

---

## **🔄 Reload Recon-ng**
Once you've added the API keys and fixed dependencies, restart **Recon-ng**:
```bash
exit
recon-ng
```
Then, reload modules:
```bash
modules reload
```

---

## **Final Check**
To confirm everything is working:
```bash
marketplace search
modules search hosts
show modules
```
Then try running a module:
```bash
modules load recon/domains-hosts/hackertarget
options
set SOURCE example.com
run
```

---

 **Database Management**:
   - View tables:
     ```bash
     show <table_name>
     ```
     Example:
     ```bash
     show hosts
     ```
   - Delete records:
     ```bash
     query DELETE FROM hosts WHERE host='example.com'
     ```

 **Scripting**:
   - Automate workflows using scripts:
     ```bash
     recon-ng -r /path/to/script.rc
     ```

---

### **Use Cases**
1. **Penetration Testing**:
   - Gather information about a target before launching an attack.
2. **Bug Bounty Hunting**:
   - Discover subdomains, open ports, and vulnerabilities.
3. **Threat Intelligence**:
   - Collect OSINT data for threat analysis.
4. **Security Audits**:
   - Identify exposed services and potential attack vectors.

---

### **Limitations**
- **No Exploitation**: Recon-ng is purely a reconnaissance tool and does not include exploitation capabilities.
- **API Dependencies**: Many modules rely on third-party APIs, which may have usage limits or require payment.
- **Learning Curve**: Requires familiarity with the command-line interface and OSINT techniques.

---

### **Summary**
Recon-ng is a versatile and powerful reconnaissance framework for penetration testers, security researchers, and bug bounty hunters. Its modular design, database integration, and automation capabilities make it an essential tool for information gathering and OSINT. By mastering Recon-ng, you can efficiently collect and analyze data to identify potential vulnerabilities and attack vectors.
