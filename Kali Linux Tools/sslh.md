![sslh.png](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/Images/sslh.png)

### **`sslh` - SSL/SSH Multiplexer**  

`sslh` is a tool that allows you to run multiple services (like SSH, HTTPS, and others) on the same port (typically port 443).  It does this by analyzing the initial bytes of the incoming connection to determine which protocol is being used and then forwarding the connection to the appropriate backend service.  It's useful when you have limited ports available or want to simplify network configuration.

**What `sslh` Does:**

`sslh` acts as a protocol multiplexer.  It listens on a single port and distinguishes between different protocols based on the initial bytes of the connection.  It then forwards the connection to the correct backend service. This means you can have, for example, SSH and HTTPS both running on port 443, and `sslh` will direct the traffic appropriately.

**Key Features and Capabilities:**

* **Protocol Multiplexing:** Runs multiple services on the same port.
* **Protocol Detection:**  Identifies protocols based on initial connection bytes.
* **Backend Forwarding:**  Forwards connections to appropriate backend services.
* **Configuration File:**  Uses a configuration file to define how to handle different protocols.
* **Daemon Mode:**  Can run as a daemon in the background.

---

## **📜 Installation**
### **🔹 On Debian/Ubuntu**
```bash
sudo apt update && sudo apt install sslh
```
### **🔹 On RHEL/CentOS**
```bash
sudo yum install sslh
```
### **🔹 On Arch Linux**
```bash
sudo pacman -S sslh
```
### **🔹 From Source**
```bash
git clone https://github.com/yrutschle/sslh.git
cd sslh
make
sudo make install
```

**Options:**

* `-F, --config=<file>`: Specify the configuration file. This is the primary way to configure `sslh`.
* `--verbose-config=<n>`: Print configuration at startup.  The higher the number, the more verbose.
* `--verbose-config-error=<n>`: Print configuration errors.
* `--verbose-connections=<n>`: Trace established incoming address to forward address.
* `--verbose-connections-try=<n>`: Connection attempts towards targets.
* `--verbose-connections-error=<n>`: Connection errors.
* `--verbose-fd=<n>`: File descriptor activity.
* `--verbose-packets=<n>`: Hexdump packets on which probing is done.
* `--verbose-probe-info=<n>`: Trace the probe process.
* `--verbose-probe-error=<n>`: Failures and problems during probing.
* `--verbose-system-error=<n>`: System call failures.
* `--verbose-int-error=<n>`: Internal errors.
* `-V, --version`: Print version information and exit.
* `-f, --foreground`: Run in foreground instead of as a daemon. Useful for testing.
* `-i, --inetd`: Run in inetd mode: use stdin/stdout.
* `-n, --numeric`: Print IP addresses and ports as numbers (no reverse DNS lookup).
* `--transparent`: Set up as a transparent proxy.
* `-t, --timeout=<n>`: Set timeout before connecting to the default target.
* `--udp-max-connections=<n>`: Number of concurrent UDP connections.
* `-u, --user=<str>`: Username to change to after setup.
* `-P, --pidfile=<file>`: Path to file to store PID.
* `-C, --chroot=<path>`: Root to change to after setup.
* `--syslog-facility=<str>`: Facility to syslog to.
* `--logfile=<str>`: Log messages to a file.
* `--on-timeout=<str>`: Target to connect to when timing out.
* `--prefix=<str>`: Reserved for testing.

**Listening and Target Options (Crucial):**

These options define the port `sslh` listens on and how it forwards connections:

* `-p, --listen=<host:port>`: Listen on host:port.  This is how you specify the main listening port (e.g., `-p 0.0.0.0:443` or `-p 192.168.1.100:443`).
* `--ssh=<host:port>`: Set up SSH target.
* `--tls=<host:port>`: Set up TLS/SSL target.
* `--ssl=<host:port>`: Set up TLS/SSL target (same as `--tls`).
* `--openvpn=<host:port>`: Set up OpenVPN target.
* `--tinc=<host:port>`: Set up tinc target.
* `--wireguard=<host:port>`: Set up WireGuard target.
* `--xmpp=<host:port>`: Set up XMPP target.
* `--http=<host:port>`: Set up HTTP (plain) target.
* `--adb=<host:port>`: Set up ADB target.
* `--socks5=<host:port>`: Set up SOCKS5 target.
* `--syslog=<host:port>`: Set up syslog target.
* `--msrdp=<host:port>`: Set up MSRDP target.
* `--anyprot=<host:port>`: Set up default target (for any unmatched protocol).

---

## **📌 Basic Usage & Configuration**

### **1️⃣ Run `sslh` with Default Settings**
```bash
sudo sslh -F 0.0.0.0:443 --ssh 127.0.0.1:22 --ssl 127.0.0.1:8443
```
📌 This listens on **port 443** and forwards:
- SSH traffic → **port 22**  
- HTTPS traffic → **port 8443**  

---

### **2️⃣ Configure `sslh` via Config File**
Edit `/etc/default/sslh` (Debian-based systems):
```ini
RUN=yes
DAEMON=/usr/sbin/sslh
DAEMON_OPTS="--user sslh --listen 0.0.0.0:443 --ssh 127.0.0.1:22 --ssl 127.0.0.1:8443 --pidfile /var/run/sslh.pid -n"
```
📌 Restart `sslh` to apply changes:
```bash
sudo systemctl restart sslh
```

---

### **3️⃣ Running `sslh` as a Systemd Service**
```bash
sudo systemctl enable sslh
sudo systemctl start sslh
```
📌 Check status:
```bash
sudo systemctl status sslh
```

---

## **📌 Advanced Usage**

### **🔹 Add OpenVPN to `sslh`**
```bash
sudo sslh --listen 0.0.0.0:443 --ssh 127.0.0.1:22 --ssl 127.0.0.1:4433 --openvpn 127.0.0.1:1194
```
📌 This setup allows **SSH, HTTPS, and OpenVPN** on **port 443**.

---

### **🔹 Run `sslh` in Transparent Mode (for NAT setups)**
```bash
sudo sslh --transparent --listen 0.0.0.0:443 --ssh 192.168.1.2:22 --ssl 192.168.1.2:443
```
📌 This **preserves original source IP addresses**.

---

### **🔹 Logging and Debugging**
Start in debug mode:
```bash
sudo sslh -v
```
Check logs:
```bash
journalctl -u sslh --no-pager | tail -n 20
```

---

## **🚀 Real-World Use Case**
### **Scenario:** SSH over HTTPS Port (Bypassing Restrictions)
1️⃣ Run SSH on **port 443**:
   ```bash
   sudo sslh --listen 0.0.0.0:443 --ssh 127.0.0.1:22 --ssl 127.0.0.1:8443
   ```
2️⃣ Connect via SSH:
   ```bash
   ssh -p 443 user@yourserver.com
   ```
📌 Useful if your ISP **blocks SSH (22)** but allows **HTTPS (443)**.

---

**Important Considerations:**

* **Protocol Detection:** `sslh` relies on identifying protocols based on the initial bytes of the connection.  This might not be foolproof for all protocols.
* **HTTPS Handling:**  If you are using `sslh` to multiplex HTTPS, you'll need to have a separate HTTPS server running on a different port (as shown in the example configuration). `sslh` itself doesn't handle HTTPS; it just forwards the connections.
* **Firewall:** Make sure your firewall allows traffic on the port that `sslh` is listening on (typically 443).
* **Configuration:**  Correctly configuring the `sslh.cfg` file is crucial.
* **Security:**  Be mindful of the security implications of running multiple services on the same port.

`sslh` is a useful tool for simplifying network configurations and running multiple services on a single port.  However, it's essential to understand its limitations and configure it correctly.  Always test your configuration thoroughly after making changes.
