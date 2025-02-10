![netmask.png](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/Images/netmask.png)

`netmask` is a simple command-line utility used to determine the network mask (also known as a subnet mask) associated with a given IP address.  It's a quick way to find out the network address and broadcast address for a given IP.

**What `netmask` Does:**

Given an IP address, `netmask` calculates and displays the corresponding network mask, network address, and broadcast address.  This information is fundamental for understanding IP networking and subnetting.

**Key Concepts:**

* **IP Address:** A numerical identifier for a device on a network.
* **Netmask (Subnet Mask):**  A mask that separates the network portion of an IP address from the host portion.  It determines how many bits are used for the network address and how many are used for the host address.
* **Network Address:** The address that represents the network itself.  It's the first address in a block of IP addresses.
* **Broadcast Address:** The last address in a block of IP addresses.  It's used to send a message to all hosts on the network.

**How to Use `netmask`:**

---

### **Basic Usage**
The general syntax is:
```bash
netmask spec [spec ...]
```
- `spec` is a specification that defines an IP address, range, or network.

---

### **Options**
| Option          | Description                                                                 |
|-----------------|-----------------------------------------------------------------------------|
| `-h, --help`    | Display a summary of the available options.                                 |
| `-v, --version` | Print the version number of the `netmask` utility.                          |
| `-d, --debug`   | Enable debug mode to print status/progress information.                     |
| `-s, --standard`| Output address/netmask pairs in standard format (e.g., `192.168.1.0/24`).   |
| `-c, --cidr`    | Output in CIDR format (e.g., `192.168.1.0/24`).                             |
| `-i, --cisco`   | Output in Cisco-style format (e.g., `192.168.1.0 255.255.255.0`).           |
| `-r, --range`   | Output the range of IP addresses in the network (e.g., `192.168.1.1-254`).  |
| `-x, --hex`     | Output address/netmask pairs in hexadecimal format.                         |
| `-o, --octal`   | Output address/netmask pairs in octal format.                               |
| `-b, --binary`  | Output address/netmask pairs in binary format.                              |
| `-n, --nodns`   | Disable DNS lookups for hostnames.                                          |
| `-f, --files`   | Treat arguments as input files containing specifications.                   |

---

### **Specifications (spec)**
A `spec` defines the IP address, range, or network. It can be any of the following formats:

1. **Single Address**:
   - Example: `192.168.1.10`
   - Represents a single IP address.

2. **Address Range**:
   - Example: `192.168.1.10:192.168.1.20`
   - Represents a range of IP addresses from `192.168.1.10` to `192.168.1.20`.

3. **Address with Offset**:
   - Example: `192.168.1.10:+10`
   - Represents a range starting at `192.168.1.10` and extending 10 addresses forward.

4. **Address with Netmask**:
   - Example: `192.168.1.0/24`
   - Represents a network with the specified netmask.

---

### **Address Formats**
An address can be specified in any of the following formats:
- **Decimal**: `3232235776` (equivalent to `192.168.1.0`).
- **Octal**: `0300.0250.0001.0000` (equivalent to `192.168.1.0`).
- **Hexadecimal**: `0xC0A80100` (equivalent to `192.168.1.0`).
- **Dotted Quad**: `192.168.1.0`.
- **Hostname**: `example.com` (resolved to an IP address via DNS, unless `--nodns` is used).

---

### **Examples**

1. **Standard Output**:
   ```bash
   netmask 192.168.1.0/24 --standard
   ```
   Output:
   ```
   192.168.1.0/255.255.255.0
   ```

2. **CIDR Output**:
   ```bash
   netmask 192.168.1.0/24 --cidr
   ```
   Output:
   ```
   192.168.1.0/24
   ```

3. **Cisco Output**:
   ```bash
   netmask 192.168.1.0/24 --cisco
   ```
   Output:
   ```
   192.168.1.0 255.255.255.0
   ```

4. **Range Output**:
   ```bash
   netmask 192.168.1.0/24 --range
   ```
   Output:
   ```
   192.168.1.1-192.168.1.254
   ```

5. **Hexadecimal Output**:
   ```bash
   netmask 192.168.1.0/24 --hex
   ```
   Output:
   ```
   0xC0A80100/0xFFFFFF00
   ```

6. **Binary Output**:
   ```bash
   netmask 192.168.1.0/24 --binary
   ```
   Output:
   ```
   11000000.10101000.00000001.00000000/11111111.11111111.11111111.00000000
   ```

7. **Disable DNS Lookup**:
   ```bash
   netmask example.com --nodns
   ```
   Output:
   ```
   (Resolves `example.com` to its IP address without DNS lookup.)
   ```

8. **Input from File**:
   ```bash
   netmask --files input.txt
   ```
   (Processes specifications from `input.txt`.)


**Interpreting the Results:**

`netmask` typically outputs three lines:

* **Netmask:** The subnet mask (e.g., 255.255.255.0).
* **Network Address:** The network address (e.g., 192.168.1.0).
* **Broadcast Address:** The broadcast address (e.g., 192.168.1.255).

**Example Output:**

```
Netmask:   255.255.255.0
Network Address: 192.168.1.0
Broadcast Address: 192.168.1.255
```

**How It Works:**

`netmask` uses the IP address and its class (A, B, or C, or based on CIDR notation if provided) to determine the default or configured subnet mask.  It then performs bitwise operations to calculate the network address and broadcast address.

**Use Cases:**

* **Network Configuration:** Determining the correct netmask, network address, and broadcast address for a given IP address.
* **Subnetting Calculations:** Understanding how IP addresses are divided into subnets.
* **Network Troubleshooting:** Diagnosing network connectivity issues.

**Important Considerations:**

* **CIDR Notation:** `netmask` may or may not support CIDR notation (e.g., 192.168.1.10/24).  If it doesn't, you'll need to use other tools (like `ipcalc` or online calculators) for CIDR-based calculations.
* **Simplicity:** `netmask` is a very basic tool.  For more advanced network calculations and information, other utilities like `ipcalc`, `ifconfig` (deprecated, but still commonly seen), `ip`, or online subnet calculators are often used.

`netmask` is a handy utility for quickly getting the network mask and related information for a given IP address.  However, for more complex subnetting scenarios or when dealing with CIDR notation, other tools might be necessary.
