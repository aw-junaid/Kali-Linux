![cutycapt.png](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/Images/Vulnerability%20Analysis%20Tools/cutycapt.png)


CutyCapt is a command-line tool that captures web pages as various image formats (PNG, JPEG, PDF, etc.) using the QtWebKit rendering engine.  It's useful for automating website screenshots, creating thumbnails, or converting web pages to other formats.

**What CutyCapt Does:**

CutyCapt essentially acts like a headless web browser.  It takes a URL as input and renders the web page as if it were being viewed in a browser, then saves the rendered output as an image or PDF.

**Key Features and Capabilities:**

*   **Multiple Output Formats:** Supports PNG, JPEG, TIFF, PDF, PS, and SVG.
*   **Command-Line Interface:**  Easy to use in scripts and automation.
*   **Customizable:**  Allows you to control the viewport size, zoom level, and other rendering options.
*   **Fast and Efficient:**  Generally faster than using a full-fledged browser automation tool for simple screenshots.

## **How to Use CutyCapt:**

  **Installation:** CutyCapt is often available in the package repositories of many Linux distributions.  For example, on Debian/Ubuntu:

```bash
 sudo apt-get install cutycapt
```

You might need to compile it from source if it's not available in your distribution's repositories.  Check the CutyCapt website or GitHub page for instructions.

  **Basic Usage:**

 ```bash
  CutyCapt --url=<url> --out=<output_file>
```

*   `--url=<url>`: The URL of the web page to capture.
*   `--out=<output_file>`: The path and filename for the output image.

##  **Options:**


**General Options:**

*   `--help`: Prints this help message and exits.
*   `--out-format=<f>`: Specifies the output format explicitly.  This overrides the format determined by the file extension in `--out`.  `<f>` can be `svg`, `ps`, `pdf`, `itext`, `html`, `rtree`, `png`, `jpeg`, `mng`, `tiff`, `gif`, `bmp`, `ppm`, `xbm`, `xpm`.
*   `--min-width=<int>`: Minimal width for the image (default: 800 pixels).
*   `--min-height=<int>`: Minimal height for the image (default: 600 pixels).
*   `--max-wait=<ms>`: Maximum time to wait for the page to load (in milliseconds).  Default is 90000 (90 seconds). Use `0` for infinite wait.
*   `--delay=<ms>`: Delay (in milliseconds) after the page has loaded before capturing.  Useful for dynamic content.
*   `--user-style-path=<path>`: Path to a user stylesheet file.
*   `--user-style-string=<css>`: User style rules as a CSS string.

**HTTP Request Options:**

*   `--header=<name>:<value>`: Add a custom HTTP header.  This option can be repeated.
*   `--method=<get|post|put>`: Specifies the HTTP request method (default: `get`).
*   `--body-string=<string>`: Unencoded request body (for `post` or `put` requests).
*   `--body-base64=<base64>`: Base64-encoded request body.

**User Agent and Browser Emulation:**

*   `--app-name=<name>`: `appName` used in the User-Agent string.
*   `--app-version=<version>`: `appVers` used in the User-Agent string.
*   `--user-agent=<string>`: Override the User-Agent header.

**Browser Settings:**

*   `--javascript=<on|off>`: Enable or disable JavaScript execution (default: `on`).
*   `--java=<on|off>`: Enable or disable Java execution (default: `unknown`).
*   `--plugins=<on|off>`: Enable or disable plugin execution (default: `unknown`).
*   `--private-browsing=<on|off>`: Enable or disable private browsing mode (default: `unknown`).
*   `--auto-load-images=<on|off>`: Enable or disable automatic image loading (default: `on`).
*   `--js-can-open-windows=<on|off>`: Allow JavaScript to open new windows (default: `unknown`).
*   `--js-can-access-clipboard=<on|off>`: Allow JavaScript to access the clipboard (default: `unknown`).
*   `--print-backgrounds=<on|off>`: Include background images in PDF/PS output (default: `off`).
*   `--zoom-factor=<float>`: Page zoom factor (default: no zooming).
*   `--zoom-text-only=<on|off>`: Zoom only text (default: `off`).

**Network Options:**

*   `--http-proxy=<url>`: Address of an HTTP proxy server.
*   `--insecure`: Ignore SSL/TLS certificate errors. *Use with caution!*

**Other Options:**

*   `--smooth`: Attempt to enable Qt's high-quality rendering settings.

**Output Formats:**

The help message lists the supported output formats: `svg`, `ps`, `pdf`, `itext`, `html`, `rtree`, `png`, `jpeg`, `mng`, `tiff`, `gif`, `bmp`, `ppm`, `xbm`, `xpm`.


## Examples

### 1️⃣ **Basic Screenshot of a Webpage**
```sh
cutycapt --url=https://example.com --out=example.png
```
Captures a screenshot of `https://example.com` and saves it as `example.png`.

---

### 2️⃣ **Setting a Custom Resolution**
```sh
cutycapt --url=https://example.com --out=example.png --min-width=1920 --min-height=1080
```
Forces a **1920x1080 resolution** screenshot.

---

### 3️⃣ **Adding a Delay for JavaScript Rendering**
```sh
cutycapt --url=https://example.com --out=example.png --delay=5000
```
Waits **5 seconds** before taking a screenshot (useful for pages with JavaScript animations or lazy-loading elements).

---

### 4️⃣ **Capturing in Different File Formats**
#### Capture as PDF:
```sh
cutycapt --url=https://example.com --out=example.pdf
```
#### Capture as JPEG:
```sh
cutycapt --url=https://example.com --out=example.jpeg
```
#### Capture as SVG:
```sh
cutycapt --url=https://example.com --out=example.svg
```
(See the list in your output for more supported formats.)

---

### 5️⃣ **Using a Proxy Server**
```sh
cutycapt --url=https://example.com --out=example.png --http-proxy=http://proxyserver:8080
```
This routes the request through a **proxy server**.

---

### 6️⃣ **Customizing the User-Agent**
```sh
cutycapt --url=https://example.com --out=example.png --user-agent="Mozilla/5.0 (Windows NT 10.0; Win64; x64)"
```
This makes `CutyCapt` **pretend to be a different browser**.

---

### 7️⃣ **Taking Screenshots of Local HTML Files**
```sh
cutycapt --url=file:///home/user/page.html --out=local.png
```
Useful for testing local HTML files.

---

### 8️⃣ **Disabling JavaScript**
```sh
cutycapt --url=https://example.com --out=example.png --javascript=off
```
For taking screenshots of pages **without running JavaScript**.

---

### 9️⃣ **Ignoring SSL Certificate Errors**
```sh
cutycapt --url=https://example.com --out=example.png --insecure
```
Useful for **bypassing SSL/TLS errors** on misconfigured HTTPS sites.


**Key Concepts:**

*   **QtWebKit:** The rendering engine used by CutyCapt.  It's based on WebKit, the same engine used in Safari.
*   **Headless Browser:**  A web browser that runs without a graphical user interface.  CutyCapt acts like a headless browser.

**Use Cases:**

*   **Website Screenshots:**  Automating the creation of website screenshots.
*   **Web Page Thumbnails:** Generating thumbnails of web pages.
*   **Website Archiving:**  Saving web pages as images or PDFs.
*   **Automated Testing:**  Capturing screenshots as part of automated web testing.

**Important Considerations:**

*   **Dynamic Content:**  For websites that heavily rely on JavaScript and dynamic content loading, you might need to use the `--delay` option to ensure that the content is fully loaded before the capture.
*   **JavaScript:**  While JavaScript is enabled by default, you might need to experiment with the `--delay` option to handle complex JavaScript interactions.  In some cases, a full-fledged browser automation tool (like Selenium or Puppeteer) might be necessary for capturing very dynamic content.
*   **Dependencies:** Make sure you have all the required QtWebKit dependencies installed.
*   **Performance:** CutyCapt is generally efficient, but capturing complex web pages can still take some time.

CutyCapt is a handy command-line tool for quickly and easily capturing web pages as images or PDFs.  It's particularly useful for simple screenshots and automation tasks.  For more complex scenarios involving dynamic content, consider using a more powerful browser automation framework.
