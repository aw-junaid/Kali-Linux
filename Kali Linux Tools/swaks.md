![swaks.png](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/Images/swaks.png)

`swaks` (Swiss Army Knife for SMTP) is a versatile command-line tool for testing SMTP (Simple Mail Transfer Protocol) servers. It allows you to send various kinds of email messages, simulate different client behaviors, and diagnose SMTP server issues.  It's an invaluable tool for email administrators, developers, and security professionals.

**What `swaks` Does:**

`swaks` provides a way to interact directly with an SMTP server.  You can use it to:

* **Send Test Emails:** Send simple or complex emails to test server functionality.
* **Verify Server Configuration:** Check if the SMTP server is configured correctly (e.g., authentication, TLS).
* **Debug SMTP Issues:** Diagnose problems with email delivery.
* **Simulate Different Client Scenarios:** Test how the server handles various client behaviors (e.g., large attachments, unusual characters).
* **Load Testing:** Send a large number of emails to test server performance.
* **Spam Testing:**  Test how a server handles messages that might be flagged as spam.

**Key Features and Capabilities:**

* **Flexible Email Creation:**  Compose emails with custom headers, bodies, attachments, etc.
* **SMTP Command Control:**  Specify the SMTP commands to send to the server.
* **Authentication Support:**  Supports various authentication mechanisms (PLAIN, LOGIN, CRAM-MD5, NTLM).
* **TLS/SSL Support:**  Can connect to servers using TLS/SSL encryption.
* **Command-Line Interface:**  Powerful and scriptable.
* **Extensive Options:**  Provides fine-grained control over email sending.

**How to Use `swaks`:**

1. **Basic Usage:**

   ```bash
   swaks --to <recipient_email> --from <sender_email> --server <smtp_server>
   ```

   Replace `<recipient_email>`, `<sender_email>`, and `<smtp_server>` with the appropriate values.

2. **Options:**

   `swaks` has a wide range of options. Here are some of the most commonly used:

   * `--to <email_address>`: Recipient email address.
   * `--from <email_address>`: Sender email address.
   * `--server <hostname_or_IP>`: SMTP server hostname or IP address.
   * `--port <port_number>`: SMTP port (default is 25).
   * `--auth <mechanism>`: Authentication mechanism (PLAIN, LOGIN, CRAM-MD5, NTLM).
   * `--user <username>`: Username for authentication.
   * `--pass <password>`: Password for authentication.
   * `--tls`: Enable TLS encryption.
   * `--starttls`: Use STARTTLS to upgrade to TLS.
   * `--body <email_body>`: Email body text.
   * `--header "<header_name>: <header_value>"`: Add a custom header.
   * `--attach <file_path>`: Attach a file.
   * `--verbose`: Verbose output.
   * `--debug`: Debug output.
   * `--help`: Display help message.

3. **Example Usage:**

   * Sending a simple email:
     ```bash
     swaks --to test@example.com --from me@example.com --server mail.example.com --body "This is a test email."
     ```

   * Sending an email with authentication:
     ```bash
     swaks --to test@example.com --from me@example.com --server mail.example.com --auth LOGIN --user myuser --pass mypassword --body "This is a test email with authentication."
     ```

   * Sending an email with a custom header and attachment:
     ```bash
     swaks --to test@example.com --from me@example.com --server mail.example.com --header "X-Custom-Header: My Value" --attach /path/to/my/file.txt --body "This is a test email with a custom header and attachment."
     ```

   * Using STARTTLS:
      ```bash
      swaks --to test@example.com --from me@example.com --server mail.example.com --starttls --auth LOGIN --user myuser --pass mypassword --body "This is a test email with STARTTLS."
      ```

1. **Basic Email Delivery:**

   ```bash
   swaks --to user@example.com --server test-server.example.net
   ```
   This sends a basic test email to `user@example.com` on port 25 of the server `test-server.example.net`.

2. **Email with Authentication and Header:**

   ```bash
   swaks --to user@example.com --from me@example.com --auth CRAM-MD5 --auth-user me@example.com --header-X-Test "test email"
   ```
   This sends an email with CRAM-MD5 authentication (using the username `me@example.com`) and adds a custom header `X-Test`.  It mentions that the password will be prompted for if not found in your `.netrc` file (a common way to store credentials securely).

3. **Virus Scanner Test with Attachment:**

   ```bash
   swaks -t user@example.com --attach - --server test-server.example.com --suppress-data </path/to/eicar.txt
   ```
   This example shows how to test a virus scanner.  It attaches the EICAR test file (a standard virus test file) and uses `--suppress-data` to avoid displaying the email's DATA part (which would contain the virus signature).

4. **Spam Scanner Test with GTUBE:**

   ```bash
   swaks --to user@example.com --body @/path/to/gtube/file
   ```
   This tests a spam scanner using the GTUBE (Generic Test for Unsolicited Bulk Email) string in the email body. The `@` symbol before the file path indicates that the file content should be used as the email body.

5. **LMTP Delivery via UNIX Socket:**

   ```bash
   swaks --protocol LMTP --server /path/to/lmtp.socket
   ```
   This example demonstrates how to use `swaks` with the LMTP (Local Mail Transfer Protocol) protocol over a UNIX domain socket.  This is often used for local mail delivery.


**Key Concepts:**

* **SMTP Commands:** `swaks` allows you to send specific SMTP commands (e.g., `HELO`, `EHLO`, `MAIL FROM`, `RCPT TO`, `DATA`).
* **Email Headers:** You can customize email headers (e.g., `Subject`, `From`, `To`, `Cc`, `Bcc`).
* **Email Body:** You can specify the email body text.
* **Attachments:** You can attach files to emails.
* **Authentication:** `swaks` supports various authentication mechanisms.
* **TLS/SSL:** `swaks` can use encryption to secure the connection to the SMTP server.

**Use Cases:**

* **Testing Email Server Configuration:** Verify that the SMTP server is configured correctly.
* **Debugging Email Delivery Issues:** Diagnose problems with email sending and receiving.
* **Email Client Simulation:** Test how the server handles different client behaviors.
* **Spam Filtering Testing:** Evaluate how the server handles messages that might be flagged as spam.
* **Load Testing:**  Test server performance under heavy email loads.

**Important Considerations:**

* **Authentication:**  When testing with authentication, ensure you have the correct credentials.
* **TLS/SSL:**  It's crucial to use TLS/SSL encryption when communicating with SMTP servers, especially when sending authentication credentials.
* **Server Configuration:**  Be aware of the SMTP server's configuration (e.g., authentication requirements, size limits, spam filtering).
* **Ethical Use:** Only use `swaks` on mail servers that you own or have explicit permission to test. Unauthorized use is illegal and unethical.

`swaks` is a powerful and flexible tool for interacting with SMTP servers. It's an essential utility for anyone working with email systems.  However, it's crucial to use it responsibly and ethically.  Always obtain proper authorization before testing any mail server.
