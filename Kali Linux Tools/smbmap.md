![smbmap.png](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/Images/smbmap.png)

`smbmap` is a powerful tool for enumerating SMB shares on a target system. It goes beyond simply identifying open SMB ports, allowing you to explore shares, list files and directories, check permissions, and even attempt anonymous logins.  It's a valuable tool for penetration testing and security auditing.

**What `smbmap` Does:**

`smbmap` provides a more comprehensive way to interact with SMB shares than simply detecting their presence. It allows you to:

* **Enumerate Shares:** List all available SMB shares on a target.
* **List Files and Directories:** Explore the contents of shares.
* **Check Permissions:** Determine access rights to shares and files (read, write, execute).
* **Attempt Anonymous Login:**  Check for shares accessible without credentials.
* **Download Files (with proper permissions):** Retrieve files from shares.
* **Upload Files (with proper permissions):** Send files to shares.
* **Execute Commands (if allowed):** In some cases, if the share permissions allow it.
* **SMB Version Detection:** Identifies the SMB protocol version being used (SMBv1, SMBv2, SMBv3).

**Key Features and Capabilities:**

* **Comprehensive SMB Enumeration:**  Provides detailed information about shares.
* **File System Interaction:**  Allows listing files and directories.
* **Permission Checking:**  Determines access rights.
* **Anonymous Login Attempts:**  Checks for anonymous access.
* **File Transfer:**  Enables downloading and uploading files (with appropriate permissions).
* **Command Execution (limited):**  In some specific configurations.
* **Scripting:**  Can be used in scripts for automation.

**How to Use `smbmap`:**

 **Basic Usage:**

   ```bash
   smbmap -H <target_host>
   ```

   Replace `<target_host>` with the hostname or IP address of the target.

**Options:**

* **Main Arguments:**
    * `-h, --help`: Show this help message and exit.
    * `-H HOST`: IP address or FQDN of the target host.
    * `--host-file FILE`: File containing a list of target hosts.
    * `-u USERNAME, --username USERNAME`: Username for authentication (if omitted, a null session is attempted).
    * `-p PASSWORD, --password PASSWORD`: Password or NTLM hash (LMHASH:NTHASH format).
    * `--prompt`: Prompt for a password interactively.
    * `-s SHARE`: Specify a share (default is `C$`).
    * `-d DOMAIN`: Domain name (default is `WORKGROUP`).
    * `-P PORT`: SMB port (default is 445).
    * `-v, --version`: Return the OS version of the remote host.
    * `--signing`: Check if SMB signing is disabled, enabled, or required.
    * `--admin`: Just report if the user is an admin.
    * `--no-banner`: Removes the banner from the output.
    * `--no-color`: Removes color from the output.
    * `--no-update`: Removes the "Working on it" message.
    * `--timeout SCAN_TIMEOUT`: Set port scan socket timeout (default is 0.5 seconds).

* **Kerberos Settings:**
    * `-k, --kerberos`: Use Kerberos authentication.
    * `--no-pass`: Use CCache file (requires setting the `KRB5CCNAME` environment variable).
    * `--dc-ip IP or Host`: IP or FQDN of the Domain Controller.

* **Command Execution:**
    * `-x COMMAND`: Execute a command on the target (use with caution).
    * `--mode CMDMODE`: Set the execution method (wmi or psexec, default is wmi).

* **Share Drive Search:**
    * `-L`: List all drives on the host (requires admin rights).
    * `-r [PATH]`: Recursively list directories and files.
    * `-g FILE`: Output to a file in grep-friendly format (used with `-r`).
    * `--csv FILE`: Output to a CSV file.
    * `--dir-only`: List only directories, omit files.
    * `--no-write-check`: Skip the check for write access.
    * `-q`: Quiet verbose output (only shows shares with read or write access).
    * `--depth DEPTH`: Traverse a directory tree to a specific depth (default is 1).
    * `--exclude SHARE [SHARE...]`: Exclude shares from searching and listing.
    * `-A PATTERN`: Define a file name pattern (regex) to automatically download files.

* **File Content Search:**
    * `-F PATTERN`: Search for a pattern in file content (requires admin access and PowerShell).
    * `--search-path PATH`: Specify the drive/path to search (default is `C:\Users`).
    * `--search-timeout TIMEOUT`: Specify a timeout for the file search.

* **Filesystem Interaction:**
    * `--download PATH`: Download a file from the remote system.
    * `--upload SRC DST`: Upload a file to the remote system.
    * `--delete PATH TO FILE`: Delete a remote file.
    * `--skip`: Skip delete file confirmation prompt.

 **Example Usage:**

   * Listing shares on a host:
     ```bash
     smbmap -H 192.168.1.100
     ```

   * Attempting anonymous login:
     ```bash
     smbmap -H 192.168.1.100 -a
     ```

   * Specifying credentials:
     ```bash
     smbmap -H 192.168.1.100 -u myuser -p mypassword
     ```

   * Listing files in a specific share:
     ```bash
     smbmap -H 192.168.1.100 -s "MyShare" -R
     ```

   * Getting share ACL:
     ```bash
     smbmap -H 192.168.1.100 -g "MyShare"
     ```
 **Basic usage with credentials:**
  ```bash
  smbmap -u jsmith -p password1 -d workgroup -H 192.168.0.1
  ```

 **Using an NTLM hash:**
  ```bash
  smbmap -u jsmith -p 'aad3b435b51404eeaad3b435b51404ee:da76f2c4c96028b7a6111aef4a50a94d' -H 172.16.0.20
  ```

 **Executing a command:**
```bash
  smbmap -u 'apadmin' -p 'asdf1234!' -d ACME -H 10.1.3.30 -x 'net group "Domain Admins" /domain'
```
**Interpreting the Results:**

`smbmap` displays information about discovered shares, including their names, types, comments, and access rights.  It also shows the contents of shares when listing files and directories.

**Important Considerations:**

* **Authentication:** `smbmap` can attempt anonymous logins or use provided credentials.  Make sure you have proper authorization before attempting to access any shares.
* **Permissions:**  `smbmap` helps identify permissions, but it's crucial to verify them before attempting any actions (downloading, uploading, executing).
* **SMB Versions:**  Older SMB versions (SMBv1) are insecure.  `smbmap` can help identify systems using these outdated versions.
* **Firewall Considerations:** Firewalls can block SMB traffic, preventing `smbmap` from discovering or accessing shares.

`smbmap` is a valuable tool for security assessments and penetration testing.  It provides a more comprehensive way to interact with SMB shares than basic SMB scanning tools.  However, it's essential to use it responsibly and ethically, and only on systems you have permission to test.
