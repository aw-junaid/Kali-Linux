![wapiti.png](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/Images/Vulnerability%20Analysis%20Tools/wapiti.png)

Wapiti is a web application vulnerability scanner. It's designed to identify a range of security flaws in web applications, including cross-site scripting (XSS), SQL injection, command injection, path traversal, and more. Wapiti works by crawling the target website and injecting payloads to test for vulnerabilities. It's known for its ease of use and ability to generate detailed reports.

**What Wapiti Does:**

Wapiti crawls the target web application, analyzing its structure and identifying entry points. It then uses various attack vectors (payloads) to test these entry points for vulnerabilities. The results are reported in a clear and concise format.

**Key Features and Capabilities:**

*   **Comprehensive Scanning:** Detects a wide range of web application vulnerabilities.
*   **Crawling:** Explores the web application to identify potential attack surfaces.
*   **Attack Modules:** Uses various attack modules to test for different types of vulnerabilities.
*   **Reporting:** Generates reports in various formats (HTML, XML, etc.).
*   **Command-Line Interface:** Easy to use and scriptable.
*   **Fast Scanning:** Designed to be relatively quick.

**How to Use Wapiti:**

1.  **Installation:** Wapiti is often included in penetration testing distributions like Kali Linux.  You can also usually install it using your distribution's package manager (e.g., `apt-get install wapiti` on Debian/Ubuntu, `brew install wapiti` on macOS).

2.  **Basic Usage:**

    ```bash
    wapiti -u <target_url> -o <report_file>
    ```

    *   `-u <target_url>`: *Required*. The URL of the web application to scan (e.g., `http://example.com` or `https://example.com`).
    *   `-o <report_file>`: *Required*. The path and filename for the output report (e.g., `report.html`).

**Target and Scope:**

*   `-u URL` or `--url URL`: *Required (unless `--list-modules` or `--update` is used)*. The URL of the web application.
*   `--scope {page,folder,domain,url,punk}`: Defines the scope of the scan.
    *   `page`: Scan only the specified page.
    *   `folder`: Scan the specified folder and its subfolders.
    *   `domain`: Scan the entire domain.
    *   `url`: Same as `page`.
    *   `punk`:  A special mode that performs more aggressive and less predictable crawling.
*   `-d DEPTH`: Maximum crawling depth.

**Modules and Attacks:**

*   `-m MODULES_LIST`: Comma-separated list of modules to use.  Use `--list-modules` to see the available modules.
*   `--list-modules`: List available attack modules.
*   `-x ATTACKS_LIST`: Comma-separated list of specific attacks to perform.  Use `wapiti -h` to see the list of available attacks.
*   `--flush-attacks`: Force re-sending attacks even if they have already been tested.

**Crawling Options:**

*   `--skip-crawl`: Do not crawl the website, only use provided URLs.
*   `--resume-crawl`: Resume a previously interrupted crawl.
*   `--max-links-per-page MAX`: Maximum number of links to follow per page.
*   `--max-files-per-dir MAX`: Maximum number of files to index per directory.

**Timeouts and Limits:**

*   `--max-scan-time SECONDS`: Maximum scan time in seconds.
*   `--max-attack-time SECONDS`: Maximum time to spend on attacks.
*   `--max-parameters MAX`: Maximum number of parameters to test per request.
*   `-t SECONDS`: Timeout for requests.

**Authentication:**

*   `-a CREDENTIALS`: Authentication credentials (e.g., `user:password`).
*   `--auth-type {basic,digest,kerberos,ntlm,post}`: Authentication type.
*   `-c COOKIE_FILE`: Load cookies from a file.

**Proxy and Network:**

*   `-p PROXY_URL`: Use a proxy server.
*   `--tor`: Use Tor proxy.
*   `-H HEADER`: Add a custom HTTP header.
*   `-A AGENT`: Set a custom User-Agent.
*   `--verify-ssl {0,1}`: Verify SSL certificates (0 to disable, 1 to enable).

**Output and Reporting:**

*   `-f FORMAT`: Output format (e.g., `html`, `xml`, `txt`).
*   `-o OUPUT_PATH`: Path to the output report file.
*   `--color`: Colorize output.
*   `-v LEVEL`: Verbose output level (0-2).
*   `--no-bugreport`: Do not send bug reports.

**Other Options:**

*   `--update`: Update Wapiti.
*   `--flush-session`: Clear the current session.
*   `--store-session PATH`: Store the session to a file.
*   `--store-config PATH`: Store the configuration to a file.
*   `-s URL`: URL to start the scan from (alternative to `-u`).
*   `-x URL`: URL to exclude from the scan.
*   `-r PARAMETER`: Parameter to force the scan.
*   `--skip PARAMETER`: Parameter to skip during the scan.
*   `-S FORCE`: Force HTTP or HTTPS.
*   `--external-endpoint EXTERNAL_ENDPOINT_URL`: URL for external endpoints.
*   `--internal-endpoint INTERNAL_ENDPOINT_URL`: URL for internal endpoints.
*   `--endpoint ENDPOINT_URL`: URL for specific endpoints.
*   `--version`: Show Wapiti version.
*   `-h`: Display this help message.
``


## **🔹 Examples**
### **1️⃣ Simple Website Scan**
Scan a target website with **default settings**:
```bash
wapiti -u http://example.com/
```
- `-u` → Defines the **target URL**  
- The output will show the discovered vulnerabilities  

---

### **2️⃣ Scan with Authentication**
If the website requires authentication (Basic Auth, Digest, etc.), use:  
```bash
wapiti -u http://example.com/ -a username:password
```
- `-a username:password` → HTTP authentication credentials  

For **cookie-based authentication**, use:  
```bash
wapiti -u http://example.com/ -c "PHPSESSID=1234567890abcdef"
```
- `-c "cookie"` → Uses a **session cookie**  

---

### **3️⃣ Exclude Specific URLs**
Avoid scanning certain URLs:  
```bash
wapiti -u http://example.com/ --exclude "logout,admin"
```
- `--exclude "logout,admin"` → **Ignores URLs** containing "logout" or "admin"  

---

### **4️⃣ Set a Specific Scan Scope**
Limit how deep Wapiti crawls:  
```bash
wapiti -u http://example.com/ --max-depth 3
```
- `--max-depth 3` → Limits the scan depth to **3 levels**  

---

### **5️⃣ Only Test for Specific Vulnerabilities**
To test for **XSS and SQL Injection** only:  
```bash
wapiti -u http://example.com/ --module xss,sqli
```
- `--module` → Choose specific vulnerability tests  

📌 **Supported modules:**  
- `sqli` → **SQL Injection**  
- `xss` → **Cross-Site Scripting (XSS)**  
- `crlf` → **CRLF Injection**  
- `file` → **File Handling (LFI, RFI, Directory Traversal, etc.)**  
- `cmd` → **Command Execution**  
- `bck` → **Backup File Detection**  
- `htaccess` → **.htaccess misconfigurations**  

---

### **6️⃣ Enable Verbose Mode (More Details)**
To see more details while scanning:  
```bash
wapiti -u http://example.com/ -v 2
```
- `-v 2` → Sets verbosity level **2** (more output)  

---

### **7️⃣ Save Results in a Report**
Generate a vulnerability report in **HTML, JSON, XML, or TXT**:  
```bash
wapiti -u http://example.com/ -o report.html -f html
```
- `-o report.html` → Saves the report to **report.html**  
- `-f html` → Specifies the **HTML** format (Other options: `json`, `xml`, `txt`)  

---

### **8️⃣ Scan via a Proxy (Burp Suite, SOCKS, etc.)**
To route traffic through a proxy:  
```bash
wapiti -u http://example.com/ --proxy http://127.0.0.1:8080
```
- `--proxy http://127.0.0.1:8080` → Sends traffic through Burp Suite **(for manual analysis)**  

For **SOCKS proxy**:  
```bash
wapiti -u http://example.com/ --proxy socks5://127.0.0.1:9050
```
- Useful for **Tor routing**  

---

### **9️⃣ Scan Only a Specific Parameter**
If you want to **test only one parameter**:  
```bash
wapiti -u "http://example.com/search.php?query=FUZZ"
```
- Replaces `FUZZ` with test payloads  

---

### **🔹 Example: Full Scan with Reporting**
A full scan with **XSS, SQLi, and Directory Traversal**, plus an **HTML report**:
```bash
wapiti -u http://example.com/ --module xss,sqli,file -o full_report.html -f html
```






