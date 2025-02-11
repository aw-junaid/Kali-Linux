![smpt-user-enum.png](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/Images/smpt-user-enum.png)

`smtp-user-enum` is a command-line tool used to enumerate valid usernames on mail servers that are vulnerable to VRFY, EXPN, or RCPT TO enumeration attacks. These attacks exploit vulnerabilities in the SMTP (Simple Mail Transfer Protocol) server configuration that allow an attacker to determine which usernames are valid on the system without actually sending an email.

**What `smtp-user-enum` Does:**

`smtp-user-enum` attempts to verify the existence of usernames by using one of the following SMTP commands:

* **VRFY:**  Asks the SMTP server to verify if a given user exists. (Often disabled due to security concerns).
* **EXPN:**  Asks the SMTP server to expand a given username to its full name or mailing list. (Also often disabled).
* **RCPT TO:**  Attempts to send an email to a given username.  If the user exists, the server will usually respond with a success code (e.g., 250 OK). If the user does not exist, the server will respond with an error code (e.g., 550 No such user here).

`smtp-user-enum` automates the process of trying these commands with a list of usernames, allowing you to quickly identify valid accounts.

**Key Features and Capabilities:**

* **User Enumeration:**  Identifies valid usernames on vulnerable SMTP servers.
* **Multiple Enumeration Methods:** Uses VRFY, EXPN, and RCPT TO.
* **Wordlist Support:**  Can use a wordlist of usernames.
* **Command-Line Interface:**  Easy to use from the terminal.

**How to Use `smtp-user-enum`:**

**Basic Usage:**

```bash
smtp-user-enum [options] ( -u username | -U file-of-usernames ) ( -t host | -T file-of-targets )
```

**Options:**

* `-m n`: Maximum number of processes to run concurrently (default: 5).  This controls how many usernames are checked at the same time.
* `-M mode`: Method to use for username guessing: `EXPN`, `VRFY`, or `RCPT` (default: `VRFY`).  `RCPT` is usually the most reliable but might be slower.
* `-u user`: Check if a single `user` exists on the remote system.
* `-f addr`: MAIL FROM email address. Used only in "RCPT TO" mode (default: `user@example.com`). This is the "from" address used when the tool tries to send a "test" email to check for valid users.
* `-D dom`: Domain to append to the supplied user list to make email addresses. Use this when you want to guess valid email addresses (e.g., `-D example.com` would try `user@example.com` instead of just `user`).
* `-U file`: File containing a list of usernames to check.
* `-t host`: Server host running the SMTP service.
* `-T file`: File containing a list of hostnames running the SMTP service.
* `-p port`: TCP port on which the SMTP service runs (default: 25).
* `-d`: Debugging output.
* `-w n`: Wait a maximum of `n` seconds for a reply (default: 5).
* `-v`: Verbose output.
* `-h`: This help message.

**Key Points:**

* **Username Specification:** You *must* specify either a single username with `-u` or a file of usernames with `-U`.
* **Target Specification:**  You *must* specify either a single target host with `-t` or a file of target hosts with `-T`.
* **Enumeration Method (`-M`):**  Choose the appropriate enumeration method (`VRFY`, `EXPN`, or `RCPT`).  `RCPT` is often the most effective but can be slower.  `VRFY` and `EXPN` are frequently disabled on modern servers.
* **Email Address Guessing (`-D`):**  This option is useful for trying to determine valid email addresses, not just usernames.
* **Parallel Processes (`-m`):**  Increasing the number of processes can speed up the scan, but be mindful of the load on the target server.
* **Timeouts (`-w`):** Adjust the timeout if you are experiencing network latency.

**Examples:**

* **Using VRFY method:**
  ```bash
  smtp-user-enum -M VRFY -U users.txt -t 10.0.0.1
  ```

* **Using EXPN method:**
```bash
  smtp-user-enum -M EXPN -u admin1 -t 10.0.0.1
Starting smtp-user-enum v1.2 ( http://pentestmonkey.net/tools/smtp-user-enum )

 ----------------------------------------------------------
|                   Scan Information                       |
 ----------------------------------------------------------

Mode ..................... EXPN
Worker Processes ......... 5
Target count ............. 1
Username count ........... 1
Target TCP port .......... 25
Query timeout ............ 5 secs
Target domain ............ 

######## Scan started at Tue Feb 11 02:22:25 2025 #########
######## Scan completed at Tue Feb 11 02:22:30 2025 #########
0 results.

1 queries in 5 seconds (0.2 queries / sec)

```

* **Using RCPT method with multiple targets:**
  ```bash
  smtp-user-enum -M RCPT -U users.txt -T mail-server-ips.txt
  ```

* **Guessing email addresses with EXPN:**
  ```bash
  smtp-user-enum -M EXPN -D example.com -U users.txt -t 10.0.0.1
  ```

   * Enumerating users from a file:
     ```bash
     smtp-user-enum -u users.txt mail.example.com
     ```

   * Using a wordlist:
     ```bash
     smtp-user-enum -w common_usernames.txt mail.example.com
     ```

   * Specifying the RCPT TO method:
     ```bash
     smtp-user-enum -m RCPT mail.example.com
     ```

   * Specifying a different port:
     ```bash
     smtp-user-enum -p 587 mail.example.com  # Example: port 587 for submission
     ```
---

**Interpreting the Results:**

`smtp-user-enum` displays the results of the enumeration attempts. It will typically show which usernames were found to be valid.

**Important Considerations:**

* **Vulnerable Servers:**  `smtp-user-enum` only works against mail servers that are vulnerable to VRFY, EXPN, or RCPT TO enumeration attacks.  Modern mail servers often disable these features to prevent this type of attack.
* **Ethical Use:** Only use `smtp-user-enum` on mail servers that you own or have explicit permission to test. Unauthorized use is illegal and unethical.
* **Detection:**  Mail servers can often log these enumeration attempts.  Be aware that your activity might be detected.
* **Limited Information:**  `smtp-user-enum` only identifies valid usernames. It does not provide any information about passwords or other account details.

`smtp-user-enum` is a useful tool for security testing and identifying vulnerable mail servers. However, it's crucial to use it responsibly and ethically.  Be aware of the limitations of the tool and the potential for detection.  Always obtain proper authorization before testing any mail server.
