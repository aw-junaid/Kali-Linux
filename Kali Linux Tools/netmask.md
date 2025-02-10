`netmask` is a simple command-line utility used to determine the network mask (also known as a subnet mask) associated with a given IP address.  It's a quick way to find out the network address and broadcast address for a given IP.

**What `netmask` Does:**

Given an IP address, `netmask` calculates and displays the corresponding network mask, network address, and broadcast address.  This information is fundamental for understanding IP networking and subnetting.

**Key Concepts:**

* **IP Address:** A numerical identifier for a device on a network.
* **Netmask (Subnet Mask):**  A mask that separates the network portion of an IP address from the host portion.  It determines how many bits are used for the network address and how many are used for the host address.
* **Network Address:** The address that represents the network itself.  It's the first address in a block of IP addresses.
* **Broadcast Address:** The last address in a block of IP addresses.  It's used to send a message to all hosts on the network.

**How to Use `netmask`:**

**Basic Usage:**

```bash
netmask spec [spec ...]
```

* `netmask`: The command to run the utility.
* `spec [spec ...]`: One or more specifications for IP addresses and netmasks.

**Options:**

* `-h, --help`: Print a summary of the options (this help message).
* `-v, --version`: Print the version number.
* `-d, --debug`: Print status/progress information (for debugging).
* `-s, --standard`: Output address/netmask pairs in standard dotted-decimal notation.
* `-c, --cidr`: Output CIDR format address lists (e.g., 192.168.1.0/24).
* `-i, --cisco`: Output Cisco-style address lists (wildcard masks).
* `-r, --range`: Output IP address ranges.
* `-x, --hex`: Output address/netmask pairs in hexadecimal.
* `-o, --octal`: Output address/netmask pairs in octal.
* `-b, --binary`: Output address/netmask pairs in binary.
* `-n, --nodns`: Disable DNS lookups for addresses.
* `-f, --files`: Treat arguments as input files (each file contains address specifications).

**Definitions (How to specify addresses and masks):**

* **`spec` can be any of:**
    * `address`: A single IP address.
    * `address:address`: A range of IP addresses (inclusive).
    * `address:+address`: A range of IP addresses (from `address` up to `address + address`).
    * `address/mask`: An IP address with a netmask specified.

* **`address` can be any of:**
    * `N`: A decimal number.
    * `0N`: An octal number (starts with 0).
    * `0xN`: A hexadecimal number (starts with 0x).
    * `N.N.N.N`: A dotted-quad IP address (e.g., 192.168.1.1).
    * `hostname`: A DNS domain name (will be resolved to an IP address).

* **`mask`:** The number of bits set to one from the left in the netmask (e.g., `/24` means 24 bits are set to 1).

**Examples:**

* **Standard Output:**
  ```bash
  netmask 192.168.1.10/24
  ```
  Output:
  ```
  192.168.1.10 255.255.255.0
  ```

* **CIDR Output:**
  ```bash
  netmask -c 192.168.1.0/24
  ```
  Output:
  ```
  192.168.1.0/24
  ```

* **Cisco Output:**
  ```bash
  netmask -i 192.168.1.0/24
  ```
  Output:
  ```
  192.168.1.0 0.0.0.255
  ```

* **IP Range:**
  ```bash
  netmask 192.168.1.1:192.168.1.10
  ```
  Output (using `-r`):
  ```
  192.168.1.1-192.168.1.10
  ```

* **Hex Output:**
  ```bash
  netmask -x 192.168.1.10/24
  ```
  Output:
  ```
  0xc0a8010a 0xffffff00
  ```

* **Using a file:**
  Create a file named `ips.txt` with the following content:
  ```
  192.168.1.10/24
  10.0.0.1/16
  ```
  Then run:
  ```bash
  netmask -f ips.txt
  ```

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
