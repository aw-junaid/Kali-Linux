![wafw00f](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/Images/wafw00f.png)

`wafw00f` (Web Application Firewall Fingerprinting) is a tool used to identify and fingerprint web application firewalls (WAFs).  WAFs are security devices that sit in front of web applications and protect them from various attacks, such as cross-site scripting (XSS), SQL injection, and cross-site request forgery (CSRF).  `wafw00f` helps security professionals and researchers understand what kind of WAF is being used, which can be valuable information for penetration testing and vulnerability assessment.

**What `wafw00f` Does:**

`wafw00f` works by sending various crafted HTTP requests to the target web application and analyzing the responses.  It looks for specific patterns and characteristics in the responses that are indicative of different WAFs.  These characteristics can include:

* **HTTP Headers:** WAFs often add or modify HTTP headers (e.g., `Server`, `X-Cache`, custom headers) that can reveal their presence and sometimes even their specific product.
* **Response Codes:**  Different WAFs might use different HTTP response codes for blocked requests.
* **Error Messages:**  The wording and format of error messages when a WAF blocks a request can be a fingerprint.
* **HTML Content:**  WAFs might inject specific HTML code (e.g., error pages, blocking messages) into the responses.
* **Timing Analysis:**  Some WAFs introduce latency or delays in the responses, which can be detected.

**How to Use `wafw00f`:**

 **Installation:** `wafw00f` is typically installed using `pip`:

   ```bash
   pip install wafw00f
   ```
**Basic Usage:**

```bash
wafw00f <target_url>
```

* `wafw00f`: The command to run the tool.
* `<target_url>`: The URL of the web application you want to analyze (e.g., `https://example.com`). This is the **required** argument.

**Options:**

* `-h, --help`: Displays this help message and exits.

* `-v, --verbose`: Enables verbose output. Multiple `-v` options increase the verbosity level (e.g., `-v`, `-vv`, `-vvv`).  More `v`'s provide more detailed information.

* `-a, --findall`: Finds *all* matching WAFs. By default, `wafw00f` stops testing after it identifies the first WAF. This option forces it to continue and identify all potential WAFs present.

* `-r, --noredirect`: Prevents `wafw00f` from following HTTP redirects (3xx responses).  Sometimes, WAFs or load balancers redirect requests, and this option allows you to analyze the initial response without following the redirect.

* `-t TEST, --test=TEST`: Tests for a specific WAF.  You provide the name of the WAF (as listed by `wafw00f -l`).  This is useful for targeted testing if you suspect a particular WAF.

* `-o OUTPUT, --output=OUTPUT`: Writes the output to a file. The format (CSV, JSON, or text) is determined by the file extension. Use `-` as the filename for stdout (standard output).  Examples:
    * `-o results.csv`
    * `-o results.json`
    * `-o results.txt`
    * `-o -` (for printing to the console)

* `-f FORMAT, --format=FORMAT`: Forces the output format to CSV, JSON, or text, regardless of the output filename's extension.

* `-i INPUT, --input-file=INPUT`: Reads target URLs from a file.  The file can be in CSV, JSON, or text format.  For CSV and JSON, a `url` column or element is required.  This option is useful for batch scanning multiple websites.

* `-l, --list`: Lists all the WAFs that `wafw00f` can detect. This is very useful to see the available WAF names to use with the `-t` option.

* `-p PROXY, --proxy=PROXY`: Uses an HTTP proxy for the requests.  You can specify the proxy URL in various formats:
    * `http://hostname:8080`
    * `socks5://hostname:1080`
    * `http://user:pass@hostname:8080`

* `-V, --version`: Prints the version number of `wafw00f` and exits.

* `-H HEADERS, --headers=HEADERS`:  Pass custom HTTP headers from a file to override the default headers.  This is useful for advanced testing or bypassing certain WAF detections.



## **Basic Usage of WAFW00F**  

### **1. Detect if a website is using a WAF**  
```bash
wafw00f hackthissite.org


                   ______
                  /      \                                                                                             
                 (  Woof! )                                                                                            
                  \  ____/                      )                                                                      
                  ,,                           ) (_                                                                    
             .-. -    _______                 ( |__|                                                                   
            ()``; |==|_______)                .)|__|                                                                   
            / ('        /|\                  (  |__|                                                                   
        (  /  )        / | \                  . |__|                                                                   
         \(_)_))      /  |  \                   |__|                                                                   

                    ~ WAFW00F : v2.2.0 ~
    The Web Application Firewall Fingerprinting Toolkit                                                                
                                                                                                                       
[*] Checking https://hackthissite.org
[+] Generic Detection results:
[-] No WAF detected by the generic detection
[~] Number of requests: 7

```
This checks whether `hackthissite.org` has a WAF and identifies it.  

### **2. Enable verbose mode for detailed output**  
```bash
wafw00f hackthissite.org -v
```
Provides more details about the detection process.  

### **3. Find all possible WAFs protecting a website**  
```bash
wafw00f hackthissite.org -a
```
Detects **all matching WAFs**, instead of stopping at the first one.  

### **4. Avoid following redirections (3xx responses)**  
```bash
wafw00f hackthissite.org -r
```
Prevents the tool from following HTTP redirects, which may reveal extra details.  

### **5. Test for a specific WAF**  
```bash
wafw00f hackthissite.org -t Cloudflare
```
Checks whether `hackthissite.org` is using **Cloudflare** WAF.  

### **6. Save the output to a file**  
```bash
wafw00f hackthissite.org -o results.json
```
Saves the output in **JSON** format. You can also use `.csv` or `.txt`.  

### **7. Force output format**  
```bash
wafw00f hackthissite.org -o results.txt -f json
```
Forces the output format to **JSON**, even if saving to `.txt`.  

### **8. Scan multiple websites from a file**  
```bash
wafw00f -i targets.txt
```
Scans all domains listed in `targets.txt` (one URL per line).  

### **9. List all WAFs WAFW00F can detect**  
```bash
wafw00f -l
```
Displays a **list of all known WAFs** that WAFW00F can identify.  

### **10. Use an HTTP/SOCKS proxy for scanning**  
```bash
wafw00f hackthissite.org -p http://127.0.0.1:8080
```
Routes requests through a **proxy**, useful for anonymity or bypassing restrictions.  

### **11. Use custom headers (useful for WAF evasion)**  
```bash
wafw00f hackthissite.org -H headers.txt
```
Loads **custom HTTP headers** from a file to modify request signatures.  


**Important Considerations:**

* **Accuracy:** `wafw00f` is a fingerprinting tool, and its results are not always definitive.  WAFs can be configured to make detection more difficult.  Consider using multiple tools and techniques for WAF identification.
* **Evasion:**  Some WAFs can detect and block `wafw00f` scans.  Using techniques like rotating IP addresses, user agents, and adding delays can sometimes improve the chances of detection.
* **Ethical Use:**  Only use `wafw00f` on web applications that you own or have explicit permission to test.  Unauthorized scanning is illegal and unethical.  Be mindful of the target's resources and avoid overloading their servers with excessive requests.

`wafw00f` is a valuable tool for security assessments, but it should be used responsibly and ethically.  Always prioritize obtaining proper authorization before scanning any web application.
