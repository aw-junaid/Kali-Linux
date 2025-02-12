![skipfish.png](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/Images/Vulnerability%20Analysis%20Tools/skipfish.png)

Skipfish is a powerful and versatile web application security reconnaissance tool. It performs an active scan of a target web application to identify a wide range of security vulnerabilities, including cross-site scripting (XSS), SQL injection, command injection, path traversal, and many others.  It's designed to be fast, thorough, and easy to use.

**What Skipfish Does:**

Skipfish crawls the target website, analyzing its structure and behavior.  It sends various HTTP requests with specially crafted payloads to test for vulnerabilities. It then reports its findings in an organized and user-friendly HTML report.

**Key Features and Capabilities:**

*   **Fast and Efficient:** Written in C, Skipfish is designed for high performance.
*   **Comprehensive Coverage:** Detects a wide range of web application vulnerabilities.
*   **Intelligent Crawling:**  Crawls the target website efficiently, avoiding redundant requests.
*   **Plugin Support:**  Extensible with plugins to add custom checks.
*   **HTML Reporting:** Generates detailed and easy-to-understand reports.
*   **Command-Line Interface:**  Flexible and scriptable.

**How to Use Skipfish:**

**Installation:** Skipfish is often available in penetration testing distributions like Kali Linux. You can also usually install it using your distribution's package manager (e.g., `apt-get install skipfish` on Debian/Ubuntu).

**Basic Usage:**

```bash
skipfish [ options ... ] -W wordlist -o output_dir start_url [ start_url2 ... ]
```

*   `-W wordlist`: *Required*. Path to the wordlist file.
*   `-o output_dir`: *Required*. Directory where the report will be saved.
*   `start_url`: *Required*. The URL(s) to start the scan from. You can provide multiple URLs.

**Authentication and Access Options:**

*   `-A user:pass`: HTTP authentication credentials.
*   `-F host=IP`: Force a specific hostname to resolve to a given IP address. Useful for testing virtual hosts.
*   `-C name=val`: Add a custom cookie.
*   `-H name=val`: Add a custom HTTP header.
*   `-b (i|f|p)`: Use headers consistent with MSIE, Firefox, or iPhone.  Helps to emulate different browsers.
*   `-N`: Do not accept any new cookies.
*   `--auth-form url`: URL of the form-based authentication page.
*   `--auth-user user`: Username for form-based authentication.
*   `--auth-pass pass`: Password for form-based authentication.
*   `--auth-verify-url`: URL to check for successful login (in-session detection).

**Crawl Scope Options:**

*   `-d max_depth`: Maximum crawl depth.
*   `-c max_child`: Maximum number of children to index per node.
*   `-x max_desc`: Maximum number of descendants to index per branch.
*   `-r r_limit`: Maximum total number of requests to send.
*   `-p crawl%`: Node and link crawl probability.
*   `-q hex`: Repeat probabilistic scan with a given seed (for reproducible results).
*   `-I string`: Only follow URLs matching the regular expression.
*   `-X string`: Exclude URLs matching the regular expression.
*   `-K string`: Do not fuzz parameters named 'string'.
*   `-D domain`: Crawl cross-site links to another domain.
*   `-B domain`: Trust, but do not crawl, links to another domain.
*   `-Z`: Do not descend into 5xx (server error) locations.
*   `-O`: Do not submit any forms.
*   `-P`: Do not parse HTML to find new links (faster, but less thorough crawling).

**Reporting Options:**

*   `-o dir`: *Required*. Output directory for the report.
*   `-M`: Log warnings about mixed content and non-SSL passwords.
*   `-E`: Log HTTP caching intent mismatches.
*   `-U`: Log all external URLs and email addresses seen.
*   `-Q`: Suppress duplicate nodes in reports.
*   `-u`: Quiet mode (disable progress stats).
*   `-v`: Verbose output (runtime logging to stderr).

**Dictionary Management Options:**

*   `-W wordlist`: *Required*. Path to the read-write wordlist.
*   `-S wordlist`: Path to a supplemental read-only wordlist.
*   `-L`: Do not auto-learn new keywords.
*   `-Y`: Do not fuzz extensions in directory brute-force.
*   `-R age`: Purge words hit more than 'age' scans ago.
*   `-T name=val`: Add a new form auto-fill rule.
*   `-G max_guess`: Maximum number of keyword guesses to keep.
*   `-z sigfile`: Load signatures from a file.

**Performance Settings:**

*   `-g max_conn`: Maximum simultaneous TCP connections (global).
*   `-m host_conn`: Maximum simultaneous connections per target IP.
*   `-f max_fail`: Maximum consecutive HTTP errors before stopping.
*   `-t req_tmout`: Total request response timeout.
*   `-w rw_tmout`: Individual network I/O timeout.
*   `-i idle_tmout`: Timeout on idle HTTP connections.
*   `-s s_limit`: Response size limit.
*   `-e`: Do not keep binary responses for reporting.
*   `-l max_req`: Max requests per second.
*   `-k duration`: Stop scanning after the given duration (e.g., `1:30:00` for 1 hour, 30 minutes).

**Other Settings:**

*   `--config file`: Load the specified configuration file.


## Examples:  

### 1️⃣ **Basic Scan**  
Scans a website with default settings and saves the report in a directory:  
```bash
skipfish -o report_dir -W wordlist.txt http://example.com/
```
- `-o report_dir` → Specifies the output directory for the scan report  
- `-W wordlist.txt` → Specifies the wordlist for dictionary-based brute forcing  
- `http://example.com/` → The target website  

---

### 2️⃣ **Scan with Authentication (Basic Auth)**  
If the website requires authentication:  
```bash
skipfish -o report_dir -W wordlist.txt -A admin:password http://example.com/
```
- `-A admin:password` → Uses HTTP Basic Authentication credentials  

---

### 3️⃣ **Custom Headers (Bypass WAF or Filters)**  
Add custom headers to bypass security restrictions:  
```bash
skipfish -o report_dir -W wordlist.txt -H "User-Agent: Googlebot" http://example.com/
```
- `-H "User-Agent: Googlebot"` → Sets a fake user-agent  

---

### 4️⃣ **Limit the Scan Depth**  
Restrict how deep Skipfish crawls to avoid unnecessary requests:  
```bash
skipfish -o report_dir -W wordlist.txt -d 3 http://example.com/
```
- `-d 3` → Limits the scan depth to 3  

---

### 5️⃣ **Exclude Specific URLs**  
Ignore URLs that match a specific pattern:  
```bash
skipfish -o report_dir -W wordlist.txt -X logout http://example.com/
```
- `-X logout` → Excludes any URL containing "logout"  

---

### 6️⃣ **Perform a Targeted Directory Brute Force Attack**  
```bash
skipfish -o report_dir -W wordlist.txt -I /admin -I /uploads http://example.com/
```
- `-I /admin` → Only test URLs matching "/admin"  
- `-I /uploads` → Only test URLs matching "/uploads"  

---

### 7️⃣ **Crawl but Don't Submit Forms**  
If you want to scan a website but avoid sending form data:  
```bash
skipfish -o report_dir -W wordlist.txt -O http://example.com/
```
- `-O` → Disables form submissions  

---

### 8️⃣ **Scan with Custom Proxy (Burp Suite Interception)**  
If you want to route Skipfish traffic through Burp Suite:  
```bash
export http_proxy="http://127.0.0.1:8080"
skipfish -o report_dir -W wordlist.txt http://example.com/
```
- Routes requests through **Burp Suite** or another HTTP proxy  

---

### 9️⃣ **Fast Scan with Increased Threads**  
Boosts scanning speed (use with caution to avoid crashing the server):  
```bash
skipfish -o report_dir -W wordlist.txt -g 100 -m 50 http://example.com/
```
- `-g 100` → Increases global simultaneous connections  
- `-m 50` → Increases simultaneous connections per target  

---

### 🔟 **Scan for a Limited Time**  
If you want to stop scanning after a set time:  
```bash
skipfish -o report_dir -W wordlist.txt -k 1:30:00 http://example.com/
```
- `-k 1:30:00` → Stops after **1 hour 30 minutes**  

---





