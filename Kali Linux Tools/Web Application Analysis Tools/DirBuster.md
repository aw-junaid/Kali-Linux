![dirbuster.png](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/Images/Vulnerability%20Analysis%20Tools/dirbuster.png)

DirBuster is a Java-based web application fuzzer used to discover hidden directories and files on web servers. It works by brute-forcing directory and file names using wordlists, similar to `dirb`.  It has a graphical user interface (GUI), making it a bit more user-friendly for some tasks compared to command-line tools like `dirb`.

**What DirBuster Does:**

DirBuster automates the process of guessing directory and file names on a web server. It uses wordlists to generate potential names and sends HTTP requests to the server to check if they exist.  It then displays the results in its GUI.

**Key Features and Capabilities:**

*   **GUI Interface:** Provides a graphical interface for easier use.
*   **Wordlist-Based:** Uses wordlists to guess directory and file names.
*   **Recursive Scanning:** Can recursively scan subdirectories.
*   **Customizable:** Allows you to specify custom wordlists, extensions, and other options.
*   **Multi-threading:** Supports multi-threading for faster scanning.
*   **Reporting:** Can generate reports of discovered directories and files.

**How to Use DirBuster:**

  **Installation:** DirBuster is a Java application, so you'll need a Java Runtime Environment (JRE) installed. You can download DirBuster from various security websites or repositories.

  **Running DirBuster:** Once downloaded, you can usually run it by double-clicking the JAR file (e.g., `dirbuster-x.x.jar`) or from the command line:

```bash
  java -jar dirbuster-x.x.jar
```

**Using the GUI:**

1. **Target URL:** Enter the target URL (e.g., `http://example.com/`) in the "Target URL" field.
2. **Wordlist:** Select the wordlist file you want to use. You can browse for a file or choose from predefined wordlists.
3. **Number of Threads:** Specify the number of threads to use for scanning.  More threads mean faster scanning but also a higher load on the server.
4. **File Extensions:** Add any file extensions you want to search for (e.g., `.php`, `.html`).
5. **Start:** Click the "Start" button to begin the scan.


 **Options:**

1. `-h`: Display this help message.
2. `-H`: Start DirBuster in headless mode (no GUI). The report will be automatically saved upon completion. This is useful for scripting and automation.
3. `-l <Word list to use>`: Specify the wordlist file. The default wordlist is `/home/komugi/directory-list-2.3-small.txt` in this user's case.  *You'll almost certainly want to change this to a wordlist more appropriate for your target.*
4. `-g`: Only use GET requests. By default, DirBuster might use other HTTP methods.  This option restricts it to GET.
5. `-e <File Extention list>`: Specify file extensions to search for (e.g., `-e asp,aspx`). The default is `php`.  You can provide a comma-separated list.
6. `-t <Number of Threads>`: Set the number of threads. The default is 10.  Be careful with increasing this too much as it can overload the server.
7.  `-s <Start point>`: Set the starting point for the scan (e.g., `-s /admin`). The default is `/`.
8. `-v`: Verbose output. This will provide more detailed information during the scan.
9.  `-P`: Don't parse HTML.  This might speed up the scan but could miss some directories if the server uses unusual redirects or techniques.
10. `-R`: Don't be recursive.  DirBuster will only scan the specified URL and not its subdirectories.
11. `-r <location>`: Specify the file to save the report to. The default is `/home/komugi/DirBuster-Report-[hostname]-[port].txt`.

### **🔥 DirBuster (1.0-RC1) – Headless Mode & CLI Usage**  


## **🔹 Basic Usage (CLI Mode)**  
### **1️⃣ Start a Basic Scan**
```sh
java -jar DirBuster-1.0-RC1.jar -u http://example.com/
```
🔹 Runs with **default settings** (10 threads, `/` as the start point, and `.php` as the default extension).

---

### **2️⃣ Headless Mode (No GUI, Auto-Save Report)**
```sh
java -jar DirBuster-1.0-RC1.jar -H -u http://example.com/
```
🔹 Runs **without GUI** and **automatically saves results**.

📌 **Default Save Location:**  
```
/home/komugi/DirBuster-Report-[hostname]-[port].txt
```

---

### **3️⃣ Use a Custom Wordlist**
```sh
java -jar DirBuster-1.0-RC1.jar -u http://example.com/ -l /usr/share/wordlists/dirb/big.txt
```
🔹 Uses a **larger** wordlist for **better directory discovery**.

✅ **Recommended Wordlists:**  
- `/usr/share/wordlists/dirb/common.txt`  
- `/usr/share/seclists/Discovery/Web-Content/raft-medium-directories.txt`  

---

### **4️⃣ Brute-Force Specific File Extensions**
```sh
java -jar DirBuster-1.0-RC1.jar -u http://example.com/ -e html,asp,jsp
```
🔹 Searches for `.html`, `.asp`, and `.jsp` files.

---

### **5️⃣ Increase the Number of Threads (Faster Scans)**
```sh
java -jar DirBuster-1.0-RC1.jar -u http://example.com/ -t 50
```
🔹 Uses **50 threads** instead of the default **10**, making the scan **much faster**.

⚠️ **Warning:** Too many threads can overload the target server and may trigger rate-limiting.

---

### **6️⃣ Start from a Specific Subdirectory**
```sh
java -jar DirBuster-1.0-RC1.jar -u http://example.com/ -s /admin/
```
🔹 Starts scanning **inside `/admin/`** instead of `/`.

---

### **7️⃣ Disable Recursive Scanning**
```sh
java -jar DirBuster-1.0-RC1.jar -u http://example.com/ -R
```
🔹 Prevents **recursive directory scanning**.

---

### **8️⃣ Save Report to a Custom Location**
```sh
java -jar DirBuster-1.0-RC1.jar -u http://example.com/ -r /home/komugi/reports/example-report.txt
```
🔹 Saves the scan results in a custom file.

---

### **9️⃣ Run with Verbose Output (Debugging)**
```sh
java -jar DirBuster-1.0-RC1.jar -u http://example.com/ -v
```
🔹 Provides **detailed output** while scanning.

---

### **🔟 Use Only GET Requests**
```sh
java -jar DirBuster-1.0-RC1.jar -u http://example.com/ -g
```
🔹 Forces **only GET requests**, useful when dealing with **strict WAF rules**.

---

## **🔹 Full Example: Advanced Scan**
🔍 **Scan `http://example.com/`, using `big.txt` wordlist, `.php & .bak` files, 50 threads, and saving results to a custom file.**
```sh
java -jar DirBuster-1.0-RC1.jar -H -u http://example.com/ -l /usr/share/wordlists/dirb/big.txt -e php,bak -t 50 -r /home/komugi/reports/example-scan.txt
```


**Use Cases:**

*   **Web Application Security Testing:** Discovering hidden directories and files that might contain sensitive information or vulnerabilities.
*   **Reconnaissance:** Mapping the structure of a web application.

**Important Considerations:**

*   **Wordlist Selection:** Choose a relevant and comprehensive wordlist.  Consider using multiple wordlists.
*   **Thread Count:** Be careful with the number of threads.  Too many threads can overwhelm the server and lead to inaccurate results or even a denial of service.
*   **False Positives:** DirBuster can report false positives.  It's crucial to verify the results manually.
*   **Intrusive Scanning:** DirBuster performs active scans that can be detected.
*   **Ethical Use:** Only use DirBuster on systems that you have explicit permission to test. Unauthorized scanning is illegal and unethical.
*   **Rate Limiting:** Be respectful of the server's resources.  Avoid sending requests too rapidly.

**Comparison with `dirb`:**

*   **GUI vs. Command-Line:** DirBuster has a GUI, while `dirb` is command-line based.  This makes DirBuster easier to use for some, but `dirb` is more scriptable.
*   **Java vs. C:** DirBuster is written in Java, while `dirb` is in C.
*   **Features:** Both tools have similar core functionality, but they may have different options and features.

DirBuster is a useful tool for web directory brute-forcing, especially for those who prefer a graphical interface.  However, like any security tool, it should be used responsibly and ethically.  Always obtain proper authorization before scanning any target.  Choose your wordlists carefully, be mindful of the impact on the target server, and verify the results.
