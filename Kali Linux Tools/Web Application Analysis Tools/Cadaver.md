![Cadaver.png](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/Images/Vulnerability%20Analysis%20Tools/Cadaver.png)

Cadaver is a command-line WebDAV client for Unix-like systems.  WebDAV (Web Distributed Authoring and Versioning) is an extension to HTTP that allows users to collaboratively edit and manage files on remote web servers.  Cadaver provides a way to interact with these WebDAV servers from the command line, enabling file upload, download, deletion, directory creation, and other file management operations.

**What Cadaver Does:**

Cadaver allows you to browse, create, edit, move, copy, and delete files and directories on a WebDAV server, much like you would with a local file system using commands like `cd`, `ls`, `cp`, `mv`, and `rm`.

**Key Features and Capabilities:**

*   **Command-Line Interface:**  Suitable for scripting and automation.
*   **Interactive Mode:** Allows you to navigate and manage files interactively.
*   **SSL/TLS Support:** Can connect to WebDAV servers using secure connections.
*   **Proxy Support:** Can use a proxy server for connections.
*   **Basic Authentication:** Supports username/password authentication.

**How to Use Cadaver:**

**Installation:** Cadaver is often available in the package repositories of most Linux distributions.  For example, on Debian/Ubuntu:

```bash
sudo apt-get install cadaver
```

    On macOS, you might need to use a package manager like Homebrew:

```bash
brew install cadaver
```

**Basic Usage:**

```bash
cadaver [OPTIONS] http://hostname[:port]/path
```

*   `http://hostname[:port]/path`: This is the URL of the WebDAV server.
    *   `hostname`: The hostname or IP address of the server.
    *   `port`: The port number (defaults to 80 if not specified).
    *   `path`: The path to the WebDAV share on the server (defaults to `/`).

**Options:**

*   `-t, --tolerant`: Allow `cd` (change directory) and `open` (to open a file in an external editor) commands to work even if the target collection (directory) is not explicitly WebDAV-enabled.  This can be useful for servers that don't correctly advertise WebDAV support but still allow WebDAV operations. Use with caution as it might lead to unexpected behavior.
*   `-r, --rcfile=FILE`: Read commands from `FILE` instead of the default configuration file `~/.cadaverrc`. This is useful for scripting and automating Cadaver. You can put a series of Cadaver commands in a file and then use this option to execute them.
*   `-p, --proxy=PROXY[:PORT]`: Use a proxy server.  Specify the proxy hostname (`PROXY`) and optionally the port (`PORT`).  For example, `-p myproxy.example.com:8080`.
*   `-V, --version`: Display version information about Cadaver.
*   `-h, --help`: Display this help message.

**Explanation of Key Elements:**

*   **URL:** The URL is the most important part.  Make sure you include the protocol (`http://` or `https://`), the hostname (or IP), and the correct path.  If you omit the port, it defaults to 80 (standard HTTP).  For HTTPS, you *must* include `https://`.
*   **Tolerant Mode (`-t`):** This is useful when the WebDAV server's configuration is not fully compliant.  However, be aware that it might not always work as expected.  It's best to use it only if you know the server supports WebDAV but isn't advertising it correctly.
*   **RC File (`-r`):** The RC file is a powerful way to automate Cadaver.  You can create a file (e.g., `my_cadaver_script.txt`) containing Cadaver commands, one per line:

    ```
    open https://mywebdav.com/share
    put myfile.txt
    ls
    quit
    ```

    Then, you can run:

    ```bash
    cadaver -r my_cadaver_script.txt
    ```

*   **Proxy (`-p`):**  Use this if you need to connect to the WebDAV server through a proxy.


**Interactive Commands:** Once connected, Cadaver provides an interactive prompt where you can use various commands:

*   `ls`: List files and directories.
*   `cd <directory>`: Change directory.
*   `pwd`: Print the current working directory.
*   `get <remote_file> <local_file>`: Download a file.
*   `put <local_file> <remote_file>`: Upload a file.
*   `mput <local_files> <remote_directory>`: Upload multiple files.
*   `mkdir <directory>`: Create a directory.
*   `rm <file>`: Delete a file.
*   `rmdir <directory>`: Delete a directory.
*   `mv <source> <destination>`: Move or rename a file or directory.
*   `cp <source> <destination>`: Copy a file or directory.
*   `help`: Display help information.
*   `quit`: Disconnect from the server.


## **🚀 Example**
### **1️⃣ Connect to a WebDAV Server**
```sh
cadaver https://example.com/
```
👉 **You'll be prompted for a username and password.**

### **2️⃣ List Directory Contents**
```sh
ls
```
📌 Similar to `ls` in Linux, **displays remote files & directories**.

### **3️⃣ Upload a File**
```sh
put localfile.txt
```
📌 **Uploads `localfile.txt` to the WebDAV server**.

### **4️⃣ Download a File**
```sh
get remotefile.txt
```
📌 **Downloads `remotefile.txt` from the WebDAV server**.

### **5️⃣ Create a Directory**
```sh
mkdir newfolder
```
📌 **Creates a directory `newfolder` on the WebDAV server**.

### **6️⃣ Delete a File or Directory**
```sh
rm file.txt   # Delete a file
rmdir folder  # Delete a directory
```
📌 **Removes files or directories**.

### **7️⃣ Move or Rename a File**
```sh
mv oldname.txt newname.txt
```
📌 **Renames `oldname.txt` to `newname.txt`**.

### **8️⃣ Exit Cadaver**
```sh
quit
```

## **🔥 Example Session**
```sh
cadaver https://webdav.example.com/
Username: admin
Password: ********

dav:/ > ls
Listing collection `/': succeeded.
  documents/
  images/
  report.pdf

dav:/ > put myfile.txt
Uploading myfile.txt to `/myfile.txt': succeeded.

dav:/ > get report.pdf
Downloading `/report.pdf' to `report.pdf': succeeded.

dav:/ > quit
```


**Use Cases:**

*   **Collaborative File Sharing:** Accessing and managing files on a WebDAV server for collaboration.
*   **Website Management:** Managing website files on a WebDAV-enabled server.
*   **Backup and Storage:**  Using a WebDAV server for remote file storage and backups.
*   **Automation:** Scripting file management tasks on a WebDAV server.

**Important Considerations:**

*   **Authentication:** You'll usually need a username and password to connect to a WebDAV server.  Cadaver will prompt you for these when you connect.
*   **SSL/TLS:** It's highly recommended to use HTTPS when connecting to a WebDAV server to protect your credentials and data.
*   **Error Handling:** Pay attention to any error messages Cadaver displays.
*   **Server Compatibility:**  Cadaver should work with most standard WebDAV servers, but there might be compatibility issues with some non-standard implementations.

Cadaver is a useful tool for managing files on WebDAV servers from the command line.  Its interactive mode and support for common file management operations make it a convenient way to work with remote files.  However, remember to use it securely and responsibly.
