![sslscan.png](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/Images/sslscan.png)

`sslscan` is a command-line tool used to scan SSL/TLS (Secure Sockets Layer/Transport Layer Security) services on a server. It checks for various security vulnerabilities, supported cipher suites, and other SSL/TLS configuration issues.  It's an essential tool for security auditing and ensuring the secure configuration of web servers and other SSL/TLS-enabled services.

**What `sslscan` Does:**

`sslscan` connects to a server's SSL/TLS port (typically 443 for HTTPS) and performs a series of tests, including:

* **SSL/TLS Version Support:** Identifies which SSL/TLS versions are supported by the server (SSLv2, SSLv3, TLSv1.0, TLSv1.1, TLSv1.2, TLSv1.3).
* **Cipher Suite Support:** Lists the supported cipher suites and their order of preference.  This is crucial for identifying weak or insecure cipher suites.
* **Certificate Validation:** Checks the validity of the server's SSL certificate (expiration date, issuer, etc.).
* **Heartbleed Vulnerability Check:** Tests for the Heartbleed vulnerability (CVE-2014-0160).
* **POODLE Vulnerability Check:** Tests for the POODLE vulnerability (CVE-2014-3566).
* **FREAK Vulnerability Check:** Tests for the FREAK vulnerability (CVE-2015-0204).
* **Logjam Vulnerability Check:** Tests for the Logjam vulnerability (CVE-2015-4000).
* **Other Security Checks:**  Performs various other checks for known SSL/TLS vulnerabilities.

**Key Features and Capabilities:**

* **Comprehensive SSL/TLS Scanning:**  Performs a wide range of security checks.
* **Vulnerability Detection:**  Identifies known SSL/TLS vulnerabilities.
* **Cipher Suite Analysis:**  Lists and analyzes supported cipher suites.
* **Certificate Information:**  Retrieves and displays certificate details.
* **Command-Line Interface:**  Easy to use and scriptable.

**How to Use `sslscan`:**

**Basic Usage:**

```bash
sslscan [options] [host:port | host]
```

**Options:**

* `--targets=<file>`: A file containing a list of hosts to check (one per line). Hosts can be specified with ports (host:port).
* `--sni-name=<name>`: Hostname for Server Name Indication (SNI).  This is important for virtual hosting where multiple SSL certificates are served from the same IP address.
* `--ipv4, -4`: Only use IPv4.
* `--ipv6, -6`: Only use IPv6.

**Certificate Options:**

* `--show-certificate`: Show full certificate information.
* `--show-certificates`: Show chain of full certificate information.
* `--show-client-cas`: Show trusted Certificate Authorities (CAs) for TLS client authentication.
* `--no-check-certificate`: Don't warn about weak certificate algorithms or keys. Use with extreme caution as this disables critical security checks.
* `--ocsp`: Request Online Certificate Status Protocol (OCSP) response from the server.
* `--pk=<file>`: A file containing the private key or a PKCS#12 file (containing a private key/certificate pair). Used for client certificate authentication.
* `--pkpass=<password>`: The password for the private key or PKCS#12 file.
* `--certs=<file>`: A file containing PEM/ASN1 formatted client certificates.

**SSL/TLS Version and Cipher Options:**

* `--ssl2`: Only check if SSLv2 is enabled.
* `--ssl3`: Only check if SSLv3 is enabled.
* `--tls10`: Only check TLSv1.0 ciphers.
* `--tls11`: Only check TLSv1.1 ciphers.
* `--tls12`: Only check TLSv1.2 ciphers.
* `--tls13`: Only check TLSv1.3 ciphers.
* `--tlsall`: Only check TLS ciphers (all versions).
* `--show-ciphers`: Show supported client ciphers.
* `--show-cipher-ids`: Show cipher IDs.
* `--iana-names`: Use IANA/RFC cipher names rather than OpenSSL ones.
* `--show-times`: Show handshake times in milliseconds.
* `--no-cipher-details`: Disable Elliptic Curve (EC) curve names and Diffie-Hellman (DH/DHE) key lengths output.
* `--no-ciphersuites`: Do not check for supported ciphersuites.
* `--no-compression`: Do not check for TLS compression (CRIME vulnerability).
* `--no-fallback`: Do not check for TLS Fallback SCSV (vulnerability related to protocol downgrade attacks).
* `--no-groups`: Do not enumerate key exchange groups.
* `--no-heartbleed`: Do not check for the Heartbleed vulnerability (CVE-2014-0160).
* `--no-renegotiation`: Do not check for TLS renegotiation vulnerability.
* `--show-sigs`: Enumerate signature algorithms.

**STARTTLS Options:**

These options configure `sslscan` to test STARTTLS on various services:

* `--starttls-ftp`: STARTTLS setup for FTP.
* `--starttls-imap`: STARTTLS setup for IMAP.
* `--starttls-irc`: STARTTLS setup for IRC.
* `--starttls-ldap`: STARTTLS setup for LDAP.
* `--starttls-mysql`: STARTTLS setup for MySQL.
* `--starttls-pop3`: STARTTLS setup for POP3.
* `--starttls-psql`: STARTTLS setup for PostgreSQL.
* `--starttls-smtp`: STARTTLS setup for SMTP.
* `--starttls-xmpp`: STARTTLS setup for XMPP.
* `--xmpp-server`: Use a server-to-server XMPP handshake.
* `--rdp`: Send RDP preamble before starting scan.

**General Options:**

* `--bugs`: Enable SSL implementation bug workarounds.
* `--no-colour`: Disable colored output.
* `--sleep=<msec>`: Pause between connection requests (in milliseconds). Default is disabled. Useful for rate limiting.
* `--timeout=<sec>`: Set socket timeout (in seconds). Default is 3 seconds.
* `--connect-timeout=<sec>`: Set connection timeout (in seconds). Default is 75 seconds.
* `--verbose`: Display verbose output.
* `--version`: Display the program version.
* `--xml=<file>`: Output results to an XML file. Use `-` for STDOUT.
* `--help`: Display this help text.

### `sslscan` Examples:

#### **1. Basic SSL Scan**
```bash
sslscan example.com
```
👉 This scans `example.com` for available SSL/TLS versions and cipher suites.

---

#### **2. Scan a Server on a Specific Port**
```bash
sslscan example.com:443
```
👉 This scans the SSL/TLS configuration of `example.com` on port **443** (HTTPS).  

If the service is running on a different port (e.g., 465 for SMTPS, 993 for IMAPS), replace `443` accordingly.

---

#### **3. Scan with SNI (Server Name Indication)**
```bash
sslscan --sni-name=sub.example.com example.com
```
👉 If the server uses **SNI**, this ensures the correct certificate is tested.

---

#### **4. Check for TLSv1.2 Support Only**
```bash
sslscan --tls12 example.com
```
👉 This checks if **TLS 1.2** is supported and which cipher suites are available.

---

#### **5. Check for TLS 1.3 Ciphers**
```bash
sslscan --tls13 example.com
```
👉 This checks for **TLS 1.3** support and lists its ciphers.

---

#### **6. Show Detailed Certificate Information**
```bash
sslscan --show-certificate example.com
```
👉 This displays the full certificate chain, including expiration and issuer details.

---

#### **7. Detect OpenSSL Heartbleed Vulnerability**
```bash
sslscan --no-heartbleed example.com
```
👉 By default, `sslscan` checks for **Heartbleed (CVE-2014-0160)**.  
Use `--no-heartbleed` if you don’t want to check for it.

---

#### **8. Scan an IP Address**
```bash
sslscan 192.168.1.1
```
👉 This scans an internal network IP instead of a domain.

---

#### **9. Scan with STARTTLS for SMTP**
```bash
sslscan --starttls-smtp mail.example.com
```
👉 This initiates a STARTTLS connection with an **SMTP** server.

---

#### **10. Save Results to an XML File**
```bash
sslscan --xml=output.xml example.com
```
👉 Saves scan results in **XML format** for automated processing.

---


**Interpreting the Results:**

`sslscan` outputs a report showing the results of the various checks performed. It lists supported SSL/TLS versions, cipher suites, certificate details, and any vulnerabilities found. Pay close attention to warnings and errors.

**Key Concepts:**

* **Cipher Suites:**  A combination of cryptographic algorithms used for key exchange, encryption, and message authentication.  Weak cipher suites can be exploited by attackers.
* **SSL/TLS Versions:** Older SSL/TLS versions (SSLv2 and SSLv3) are known to be insecure and should be disabled.
* **Vulnerabilities:**  Heartbleed, POODLE, FREAK, and Logjam are examples of serious SSL/TLS vulnerabilities.

**Use Cases:**

* **Security Auditing:**  Assessing the security of SSL/TLS configurations.
* **Vulnerability Scanning:**  Identifying SSL/TLS vulnerabilities.
* **Compliance Testing:**  Ensuring compliance with security standards.

**Important Considerations:**

* **Cipher Suite Selection:**  Prioritize strong cipher suites and disable weak or outdated ones.
* **SSL/TLS Version Support:**  Disable support for SSLv2 and SSLv3.  Prefer TLSv1.2 and TLSv1.3.
* **Vulnerability Patching:**  If `sslscan` identifies vulnerabilities, apply the necessary patches or updates to your server.
* **Regular Scanning:**  Perform regular SSL/TLS scans to ensure ongoing security.

`sslscan` is an essential tool for anyone responsible for the security of web servers or other SSL/TLS-enabled services.  It helps identify and address potential security weaknesses, ensuring the confidentiality and integrity of communication.  It's crucial to keep `sslscan` updated for the latest vulnerability checks.
