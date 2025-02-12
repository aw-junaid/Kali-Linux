![**dirb.png**](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/Images/Vulnerability%20Analysis%20Tools/dirb.png)

Dirb is a command-line web directory brute-forcer.  It's used to discover hidden directories and files on a web server by trying common names and patterns.  It's a valuable tool for web application security testing and reconnaissance.

**What Dirb Does:**

Dirb works by sending HTTP requests to a web server for various directory and file names.  It checks the server's responses to determine if the directory or file exists.  It uses wordlists (lists of common directory and file names) to perform these checks.

**Key Features and Capabilities:**

*   **Wordlist-Based:** Uses wordlists to guess directory and file names.
*   **Recursive Scanning:** Can recursively scan subdirectories.
*   **Customizable:** Allows you to specify custom wordlists and extensions.
*   **Multiple Scan Modes:** Offers different scan modes to balance speed and thoroughness.
*   **Reporting:** Can generate reports of discovered directories and files.

**How to Use Dirb:**

1.  **Installation:** Dirb is often included in penetration testing distributions like Kali Linux.  You can also usually install it using your distribution's package manager (e.g., `apt-get install dirb` on Debian/Ubuntu).

**Basic Usage:**

```bash
dirb <url_base> [<wordlist_file(s)>] [options]
```

*   `<url_base>`: *Required*. The base URL to scan (e.g., `http://example.com/`).  Use `-resume` to resume a previous session.
*   `[<wordlist_file(s)>]`: *Optional*. A list of wordlist files to use.  You can specify multiple wordlists separated by commas (e.g., `wordlist1.txt,wordlist2.txt`). If no wordlist is provided, dirb uses its default wordlist.

**Hotkeys (During Scan):**

*   `n`: Go to the next directory (interactive mode).
*   `q`: Stop the scan and save the state for resuming later using `-resume`.
*   `r`: Display remaining scan statistics.

**Options:**

*   `-a <agent_string>`: Set a custom User-Agent string.  This can be useful to avoid detection or to test how the server responds to different user agents.
*   `-b`: Use the path as is.  Normally, dirb might try variations of the path (e.g., adding a trailing slash). This option disables that behavior.
*   `-c <cookie_string>`: Set a cookie for the HTTP request.  Useful for accessing authenticated areas of the website.
*   `-E <certificate>`: Path to the client certificate file for SSL/TLS authentication.
*   `-f`: Fine-tuning of NOT_FOUND (404) detection.  This can help dirb be more accurate in identifying valid directories, even if the server returns a 404 for them.
*   `-H <header_string>`: Add a custom header to the HTTP request.  Like `-a`, this can be repeated to add multiple headers.
*   `-i`: Use case-insensitive search.  Dirb will try both uppercase and lowercase versions of directory and file names.
*   `-l`: Print the "Location" header when found (for redirects).
*   `-N <nf_code>`: Ignore responses with this HTTP code.  For example, `-N 404,302` would ignore 404 and 302 responses.
*   `-o <output_file>`: Save the output to a file.
*   `-p <proxy[:port]>`: Use a proxy server.  The default port is 1080.
*   `-P <proxy_username:proxy_password>`: Proxy authentication.
*   `-r`: Don't search recursively.  Dirb will only check the specified base URL and not its subdirectories.
*   `-R`: Interactive recursion.  Dirb will ask you whether to recurse into each discovered directory.
*   `-S`: Silent mode.  Don't show tested words.  This is useful for dumb terminals or when you want to minimize output.
*   `-t`: Don't force an ending '/' on URLs.
*   `-u <username:password>`: HTTP authentication.  Use this if the target requires basic authentication.
*   `-v`: Show also NOT_FOUND pages.  This will show you all the requests dirb made, even if the directory or file wasn't found.
*   `-w`: Don't stop on WARNING messages.
*   `-X <extensions>` / `-x <exts_file>`: Append each word with these extensions.  For example, `-X .php,.html` will try `directory/file.php` and `directory/file.html`. `-x` loads extensions from a file.
*   `-z <millisecs>`: Add a delay (in milliseconds) between requests to avoid flooding the server.


# **🔹 DIRB Options Explained**
### 1️⃣ **Basic Scan (Default Wordlist)**
```sh
dirb http://example.com
```
🔹 Uses the **default wordlist** (`/usr/share/dirb/wordlists/common.txt`) to find **hidden directories and files**.

---

### 2️⃣ **Using a Custom Wordlist**
```sh
dirb http://example.com /usr/share/wordlists/dirb/big.txt
```
🔹 Uses a **bigger wordlist** to improve directory discovery.

📌 **Wordlist Location:**  
- `/usr/share/dirb/wordlists/`
- `/usr/share/wordlists/`
- **SecLists:** [GitHub SecLists](https://github.com/danielmiessler/SecLists)

---

### 3️⃣ **Custom User-Agent (Bypass Security)**
```sh
dirb http://example.com -a "Mozilla/5.0 (Windows NT 10.0; Win64; x64)"
```
🔹 Helps bypass security measures that block **default DIRB requests**.

---

### 4️⃣ **Brute-Forcing Specific File Extensions**
```sh
dirb http://example.com -X .php,.bak,.txt
```
🔹 Searches for **files** instead of just directories.  
✅ Useful for finding **backup files (`.bak`), logs (`.txt`), and source code (`.php`)**.

---

### 5️⃣ **Proxy Support (Use with BurpSuite)**
```sh
dirb http://example.com -p http://127.0.0.1:8080
```
🔹 Routes traffic through **BurpSuite/ZAP Proxy** for manual analysis.

✅ **Authentication via Proxy**
```sh
dirb http://example.com -p http://proxyserver:8080 -P user:pass
```

---

### 6️⃣ **Ignore Case Sensitivity (Useful for Windows/IIS)**
```sh
dirb http://example.com -i
```
🔹 Useful for case-insensitive **Windows servers (IIS)**.

---

### 7️⃣ **Ignoring Specific HTTP Response Codes**
```sh
dirb http://example.com -N 403
```
🔹 Skips **403 Forbidden** responses.

✅ Useful when scanning protected directories.

---

### 8️⃣ **Save Scan Results to a File**
```sh
dirb http://example.com -o results.txt
```
🔹 Stores findings for later analysis.

---

### 9️⃣ **Using HTTP Authentication (Basic Auth)**
```sh
dirb http://example.com -u admin:password
```
🔹 **Brute-forces directories** on **authenticated** areas.

---

### 🔟 **Fine-Tuning 404 Detection (Bypassing Security)**
```sh
dirb http://example.com -f
```
🔹 Helps bypass **custom 404 pages** (which may trick scanners).

---

### 1️⃣1️⃣ **Adding a Custom Header (Bypassing WAFs)**
```sh
dirb http://example.com -H "X-Forwarded-For: 127.0.0.1"
```
🔹 **Spoofs the IP address** to **bypass security rules**.

---

### 1️⃣2️⃣ **Slowing Down Requests (Avoiding Rate Limits)**
```sh
dirb http://example.com -z 200
```
🔹 Adds a **200-millisecond delay** to **avoid getting blocked**.

---

### 1️⃣3️⃣ **Recursive Directory Scanning**
```sh
dirb http://example.com -r
```
🔹 Searches **inside found directories** automatically.

---

### 1️⃣4️⃣ **Testing a Secure Website (HTTPS)**
```sh
dirb https://example.com
```
🔹 Works the same way but for **HTTPS** sites.

---

# **🔹 Combining Multiple Options**
Example: **Brute-force `.php`, `.bak`, and `.txt` files on an authenticated page, while using a proxy and saving output.**
```sh
dirb http://example.com -X .php,.bak,.txt -u admin:password -p http://127.0.0.1:8080 -o scan_results.txt
```

**Key Concepts:**

*   **Wordlists:** Lists of common directory and file names. Dirb uses these lists to guess what directories and files might exist on the server.  The effectiveness of Dirb heavily depends on the quality and comprehensiveness of the wordlist used.
*   **Brute-Force:** Dirb essentially performs a brute-force attack (though a somewhat targeted one) by trying many different combinations of directory and file names.

**Use Cases:**

*   **Web Application Security Testing:** Discovering hidden directories and files that might contain sensitive information or vulnerabilities.
*   **Reconnaissance:** Gathering information about the structure of a web application.

**Important Considerations:**

*   **Wordlist Selection:** The choice of wordlist is crucial.  Consider using multiple wordlists or customizing your own.  Common wordlists are often available with Dirb or online.
*   **Recursive Scanning:** Recursive scans can take a long time, especially on large websites.
*   **False Positives:** Dirb might report false positives.  It's important to verify the findings manually.
*   **Intrusive Scanning:** Dirb performs active scans, which can be detected.
*   **Ethical Use:** Only use Dirb on systems that you have explicit permission to test. Unauthorized scanning is illegal and unethical.
*   **Rate Limiting:** Be mindful of rate limiting.  Sending too many requests too quickly can overload the server or get your IP address blocked.  The `-z` option can help with this.

Dirb is a powerful tool for web directory brute-forcing, but it's important to use it responsibly and ethically.  Always obtain proper authorization before scanning any target.  Be aware of the limitations of the tool and the potential for false positives.  Use a good wordlist and consider the impact of your scans on the target server.
