![onesixtyone.png](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/Images/onesixtyone.png)

`onesixtyone` is a command-line tool used for SNMP (Simple Network Management Protocol) scanning and enumeration. It's designed to discover SNMP-enabled devices on a network and retrieve information from them.  It's a valuable tool for network administrators and security professionals.

**What `onesixtyone` Does:**

`onesixtyone` sends SNMP requests to specified IP addresses or networks to identify devices that are responding to SNMP queries.  It can:

* **Discover SNMP Devices:**  Identify devices that have SNMP enabled.
* **Enumerate SNMP Information:** Retrieve system information, interfaces, and other data from SNMP-enabled devices.
* **Identify SNMP Communities:** Discover the SNMP community strings (like passwords) used by devices.  This is crucial for security assessments, as default or weak community strings pose a security risk.

**Key Features and Capabilities:**

* **SNMP Scanning:**  Scans for SNMP-enabled devices.
* **Community String Discovery:**  Identifies SNMP community strings.
* **Information Retrieval:**  Retrieves system information and other SNMP data.
* **Command-Line Interface:**  Easy to use and scriptable.

**How to Use `onesixtyone`:**

**Basic Usage:**

```bash
onesixtyone [options] <host> <community>
```
Replace `<target_host_or_network>` with the IP address or network you want to scan (e.g., `192.168.1.1`, `192.168.1.0/24`).  Replace `<community_string>` with the SNMP community string to try (often `public` for read-only access, but you might need to try others).

**Options:**

* `-c <communityfile>`: Specifies a file containing a list of community names to try (one per line). This is crucial for brute-forcing community strings.
* `-i <inputfile>`: Specifies a file containing a list of target hosts (one IP address or network per line).
* `-o <outputfile>`: Specifies a file to write the output log to.  This is useful for saving results and using `-q` (quiet mode).
* `-p`: Specifies an alternate destination SNMP port.  The default SNMP port is 161.
* `-d`: Enables debug mode. Use twice (`-dd`) for more detailed debugging information.
* `-s`: Enables short mode. Only prints the IP addresses of discovered hosts.
* `-w n`: Sets the wait time (in milliseconds) between sending packets. The default is 10 milliseconds.  Increasing this can be helpful on slower networks or if you are being rate-limited.
* `-q`: Enables quiet mode. Does not print the log to standard output (stdout).  Usually used with the `-o` option to save the output to a file.

**Arguments:**

* `<host>`: The target host or network. This can be either a single IPv4 address (e.g., `192.168.1.10`) or an IPv4 address with a netmask (e.g., `192.168.1.0/24`).
* `<community>`: The initial SNMP community string to try.  Common default community strings are `public` and `private`.

**Important Information:**

* **Default Communities:**  `onesixtyone` tries the `public` and `private` community strings by default, even if you don't provide them on the command line.
* **Limits:**
    * Maximum number of hosts: 65536
    * Maximum community length: 32 characters
    * Maximum number of communities (from a file): 16384

**Examples:**

* **Scanning a network with a specific community string:**
  ```bash
  onesixtyone 192.168.4.0/24 public
  ```

* **Using a community file, host file, and output file:**
  ```bash
  onesixtyone -c dict.txt -i hosts -o my.log -w 100
  ```
  This command will:
    1. Read community strings from `dict.txt`.
    2. Read target hosts from `hosts`.
    3. Write the output to `my.log`.
    4. Wait 100 milliseconds between sending packets.

   * Scanning a single host with a known community string:
     ```bash
     onesixtyone 192.168.1.10 public
     ```

   * Scanning a network and trying common community strings from a file:
     ```bash
     onesixtyone 192.168.1.0/24 -c community_strings.txt
     ```

   * Using verbose output:
     ```bash
     onesixtyone -v 192.168.1.10 public
     ```

**Interpreting the Results:**

`onesixtyone` displays information about discovered SNMP devices, including their IP addresses, community strings (if found), and other SNMP data.

**Important Considerations:**

* **Community Strings:**  Default or weak SNMP community strings (like `public` or `private`) are a major security vulnerability.  `onesixtyone` helps identify these weaknesses.
* **Firewall Considerations:** Firewalls can block SNMP traffic, preventing `onesixtyone` from discovering devices.
* **SNMP Versions:** `onesixtyone` primarily works with SNMPv1 and SNMPv2c.  SNMPv3 is more secure and uses authentication, making it harder to enumerate.
* **Ethical Use:** Only use `onesixtyone` on networks and devices that you own or have explicit permission to test. Unauthorized scanning is illegal and unethical.

`onesixtyone` is a useful tool for network discovery, security auditing, and identifying SNMP-related vulnerabilities.  However, it's crucial to use it responsibly and ethically.  Always obtain proper authorization before testing any network.  Be aware of the limitations of the tool and the potential for detection.
