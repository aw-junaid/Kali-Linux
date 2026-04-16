# Kali Linux Tools Documentation
<img align = "" src="https://github.com/aw-junaid/aw-junaid/blob/main/Assets/asset1.webp" width="1000" height="250" alt="awjunaid">

![GitHub contributors](https://img.shields.io/github/contributors/aw-junaid/kali-linux)
![GitHub followers](https://img.shields.io/github/followers/aw-junaid)
![YouTube Channel Subscribers](https://img.shields.io/youtube/channel/subscribers/UClhKVCHjOxBTNM50lOBTgoA)
![Discord](https://img.shields.io/discord/1163365511309049948)
![X (formerly Twitter) Follow](https://img.shields.io/twitter/follow/awjunaid_)
![GitHub commit activity](https://img.shields.io/github/commit-activity/t/aw-junaid/kali-linux)
![Website](https://img.shields.io/website?url=https%3A%2F%2Fawjunaid.com%2F)
![GitHub repo size](https://img.shields.io/github/repo-size/aw-junaid/kali-linux)

# Contact With Me:


  <a href="https://www.youtube.com/@awjunaid/featured" target="_blank">
    <img src="https://img.shields.io/static/v1?message=Youtube&logo=youtube&label=&color=FF0000&logoColor=white&labelColor=&style=for-the-badge" height="27" alt="youtube logo"  />
  </a>
  <a href="https://www.instagram.com/awjunaid_" target="_blank">
    <img src="https://img.shields.io/static/v1?message=Instagram&logo=instagram&label=&color=E4405F&logoColor=white&labelColor=&style=for-the-badge" height="27" alt="instagram logo"  />
  </a>
  <a href="https://www.twitch.tv/awjunaid" target="_blank">
    <img src="https://img.shields.io/static/v1?message=Twitch&logo=twitch&label=&color=9146FF&logoColor=white&labelColor=&style=for-the-badge" height="27" alt="twitch logo"  />
  </a>
  <a href="mailto:awjunaid@proton.me" target="_blank">
    <img src="https://img.shields.io/static/v1?message=Proton%20Mail&logo=protonmail&label=&color=7341FF&logoColor=white&labelColor=&style=for-the-badge" height="27" alt="proton mail logo"  />
  </a>
  <a href="https://www.linkedin.com/in/aw-junaid" target="_blank">
    <img src="https://img.shields.io/static/v1?message=LinkedIn&logo=linkedin&label=&color=0077B5&logoColor=white&labelColor=&style=for-the-badge" height="27" alt="linkedin logo"  />
  </a>
  <a href="https://twitter.com/awjunaid_" target="_blank">
    <img src="https://img.shields.io/static/v1?message=Twitter&logo=twitter&label=&color=1DA1F2&logoColor=white&labelColor=&style=for-the-badge" height="27" alt="twitter logo"  />
  </a>
  <a href="https://discord.gg/Neddn8gPqY" target="_blank">
    <img src="https://img.shields.io/static/v1?message=Discord&logo=discord&label=&color=7289DA&logoColor=white&labelColor=&style=for-the-badge" height="27" alt="discord logo"  />
  </a>



  # 💰 You can help me by Donating
  [![BuyMeACoffee](https://img.shields.io/badge/Buy%20Me%20a%20Coffee-ffdd00?style=for-the-badge&logo=buy-me-a-coffee&logoColor=black)](https://buymeacoffee.com/awjunaid) 

**A guide to using Kali Linux tools for web penetration testing, ethical hacking, forensics, and bug bounty. Covers setup, key tools, methodologies, and best practices. Optimized for security professionals.**


> [!Note]
> This repository contains tools and scripts sourced from various GitHub repositories and other open-source platforms. All original works are credited to their respective authors. If you are the owner of any content and wish to have it removed, please contact the repository author directly. This project is intended for educational and ethical purposes only. Unauthorized use, distribution, or modification of these tools without proper consent is prohibited. By using this repository, you agree to comply with all applicable laws and ethical guidelines. The author is not responsible for any misuse or damage caused by the tools provided herein.


## 1. Information Gathering

This phase involves collecting as much data as possible about a target system or network.

### 1.1. DNS Analysis
Tools for enumerating DNS records and identifying subdomains.

- [**dnsenum**](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/dnsenum.md): A multithreaded Perl script to enumerate DNS information from a domain, discover non-contiguous IP blocks, and perform reverse lookups.
- [**dnsmap**](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/dnsmap.md): A passive DNS mapping tool that performs brute-force subdomain discovery to identify hidden or non-linked hosts.
- [**dnsrecon**](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/dnsrecon.md): A versatile DNS enumeration script that checks for zone transfers, performs SRV record enumeration, and supports various discovery techniques.
- [**fierce**](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/fierce.md): A DNS reconnaissance tool for locating non-contiguous IP space and identifying domain names, often used as a last resort before a full port scan.
- [**subfinder**](https://github.com/projectdiscovery/subfinder): A powerful subdomain discovery tool that focuses on speed and reliability, using passive online sources to enumerate valid subdomains.
- [**aquatone**](https://github.com/michenriksen/aquatone): A tool for visual inspection of websites across many hosts, providing screenshots and HTTP response data for easy analysis.
- [**gobuster**](https://github.com/OJ/gobuster): A multi-purpose tool for brute-forcing URIs (directories and files), DNS subdomains, and virtual host names.
- [**shuffledns**](https://github.com/projectdiscovery/shuffledns): A wrapper around massdns that enumerates subdomains using a wordlist and various resolvers.

### 1.2. OSINT Analysis
Open-Source Intelligence (OSINT) tools for gathering information from publicly available sources.

- [**maltego**](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/maltego.md): An interactive data mining tool that renders directed graphs for link analysis, allowing you to uncover relationships between people, companies, domains, and more.
- [**spiderfoot**](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/spiderfoot.md): An automated OSINT tool that integrates with numerous data sources to collect intelligence on targets, including IP addresses, domains, email addresses, and names.
- [**recon-ng**](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/recon-ng.md): A full-featured Web Reconnaissance framework written in Python, providing a powerful environment for automated OSINT collection.
- [**theHarvester**](https://github.com/laramies/theHarvester): A tool for gathering emails, subdomains, hosts, employee names, open ports, and banners from different public sources like search engines and PGP key servers.
- [**sherlock**](https://github.com/sherlock-project/sherlock): A powerful tool to hunt down usernames across hundreds of social networks, making it invaluable for social media intelligence.
- [**waybackurls**](https://github.com/tomnomnom/waybackurls): Fetch URLs from the Wayback Machine for a given domain, useful for discovering hidden endpoints.
- [**gau**](https://github.com/lc/gau): Get All URLs - Fetch known URLs from AlienVault's Open Threat Exchange, the Wayback Machine, and Common Crawl.
- [**shodan**](https://cli.shodan.io/): The official command-line interface for Shodan, allowing you to search for internet-connected devices and services.

### 1.3. Live Host & Route Analysis
Tools for identifying live systems on a network and analyzing network paths.

- [**netdiscover**](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/netdiscover.md): An active/passive ARP reconnaissance tool for discovering live hosts on a local network, useful for wardriving and network inventory.
- [**nmap**](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/Nmap.md): The industry-standard network exploration and security auditing tool, used for host discovery, port scanning, version detection, and OS fingerprinting.
- [**masscan**](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/masscan.md): A high-performance TCP port scanner that can scan the entire internet in minutes, transmitting packets at a very high rate.
- [**unicornscan**](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/unicornscan.md): A sophisticated network reconnaissance and port scanning tool with a high degree of control over packet transmission and data collection.
- [**fping**](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/fping.md): A high-performance ping tool capable of sending ICMP echo requests to multiple hosts in parallel, ideal for large-scale host discovery.
- [**hping3**](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/hping3.md): A command-line TCP/IP packet assembler and analyzer, often used for advanced port scanning, firewall testing, and manual path MTU discovery.
- [**arping**](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/arping.md): A utility for sending ARP requests to discover and probe hosts on a local network, bypassing IP-level filters.
- [**thc-ipv6**](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/thc-ipv6.md): A comprehensive suite of tools for attacking the inherent protocol weaknesses of IPv6 and ICMP6, essential for modern network audits.
- [**netmask**](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/netmask.md): A simple but useful tool for analyzing and managing IP subnets, converting between different netmask formats.
- [**httprobe**](https://github.com/tomnomnom/httprobe): A tool to probe for working HTTP and HTTPS servers from a list of hosts.
- [**naabu**](https://github.com/projectdiscovery/naabu): A fast port scanner written in Go that focuses on accuracy and simplicity.
- [**httpx**](https://github.com/projectdiscovery/httpx): A fast and multi-purpose HTTP toolkit that allows running multiple probes using the retryablehttp library.

### 1.4. Service & Protocol Analysis
Specialized tools for enumerating and analyzing specific network services.

- [**nbtscan**](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/nbtscan.md): A scanner for NetBIOS name information, retrieving share lists, logged-in users, and MAC addresses from Windows hosts on a local network.
- [**smbmap**](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/smbmap.md): A handy SMB enumeration tool that allows pen testers to browse, upload, download, and execute commands on SMB shares, checking for common misconfigurations.
- [**smtp-user-enum**](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/smtp-user-enum.md): A tool for enumerating valid users on SMTP servers using techniques like VRFY, EXPN, and RCPT TO.
- [**swaks**](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/swaks.md): The "Swiss Army Knife" for SMTP, a featureful, flexible, and scriptable tool for testing email servers and verifying mail relays.
- [**onesixtyone**](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/onesixtyone.md): A fast and simple SNMP scanner that sends multiple community strings to a range of IP addresses to identify devices with default or weak SNMP configurations.
- [**snmp-check**](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/snmp-check.md): A Perl script that enumerates information from SNMP devices, including running processes, open TCP ports, network interfaces, and installed software.
- [**ike-scan**](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/ike-scan.md): A command-line tool for discovering, fingerprinting, and testing IPsec VPN servers using IKE (Internet Key Exchange).

### 1.5. SSL/TLS Analysis
Tools for auditing and analyzing SSL/TLS configurations and certificates.

- [**sslscan**](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/sslscan.md): A fast SSL/TLS scanner that tests services for supported ciphers, protocols, and some common vulnerabilities like Heartbleed.
- [**sslyze**](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/sslyze.md): A powerful and fast SSL/TLS scanning library and tool that analyzes server configurations for weak ciphers, certificate issues, and protocol support.
- [**ssldump**](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/ssldump.md): An SSL/TLS network protocol analyzer that decodes and displays encrypted traffic, helping to identify the certificates and handshake details.
- [**sslh**](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/sslh.md): A protocol multiplexer that allows multiple services (like HTTPS, SSH, and OpenVPN) to listen on the same port by probing for and forwarding connections.

### 1.6. IDS/IPS Identification
Tools for detecting the presence of intrusion detection and prevention systems.

- [**lbd**](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/lbd.md): A load balancer detector that analyzes server responses to HTTP requests to determine if a domain is behind a load-balancing solution.
- [**wafw00f**](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/wafw00f.md): A Web Application Firewall (WAF) fingerprinting tool that sends a series of malicious requests to identify the specific WAF product protecting a website.

### 1.7. General & Auxiliary Tools
- [**amass**](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/amass.md): An in-depth attack surface mapping and subdomain enumeration tool that uses OWASP's Amass project for active and passive reconnaissance.
- [**dmitry**](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/dmitry.md): A simple but effective tool for gathering information on a target, including subdomains, email addresses, and system uptime.
- [**netcat**](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/netcat.md): The "Swiss Army knife" of networking, used for reading from and writing to network connections, port scanning, and transferring files.

## 2. Vulnerability Analysis

Tools for identifying security weaknesses and potential vulnerabilities in systems and applications.

- [**nikto**](https://awjunaid.com/kali-linux/nikto-web-vulnerability-scanner-comprehensive-guide/): A comprehensive web server scanner that tests for dangerous files, outdated server software, and specific server misconfigurations.
- [**generic_chunked**](https://awjunaid.com/kali-linux/generic_chunked-checks-for-vulnerabilities-in-chunked-encoding/): A tool designed to test for vulnerabilities in chunked transfer encoding, a feature of HTTP/1.1.
- [**voiphopper**](https://awjunaid.com/kali-linux/voiphopper-tests-vlan-hopping-in-voip-networks/): A tool that tests for VLAN hopping vulnerabilities in VoIP networks by spoofing 802.1q frames.
- [**unix-privesc-check**](https://awjunaid.com/kali-linux/unix-privesc-check-identifies-privilege-escalation-paths-on-unix-systems/): A shell script that runs on Unix systems to identify common misconfigurations that could allow local privilege escalation.
- [**legion**](https://github.com/carlospolop/legion): An automated, semi-automated, and fully automated network penetration testing framework, aiding in discovery and vulnerability scanning.
- [**nuclei**](https://github.com/projectdiscovery/nuclei): A fast and customizable vulnerability scanner based on a simple YAML-based templating language.
- [**vuls**](https://github.com/future-architect/vuls): A vulnerability scanner for Linux and FreeBSD, written in Go, with agentless architecture.
- [**clamav**](https://www.clamav.net/): An open-source antivirus engine for detecting trojans, viruses, malware, and other malicious threats.
- [**openvas**](https://www.greenbone.net/en/): A full-featured vulnerability scanner that includes a comprehensive set of network vulnerability tests.

## 3. Web Application Analysis

This section focuses on tools for assessing and attacking web applications.

### 3.1. Directory & File Discovery
- [**dirb**](https://awjunaid.com/kali-linux/dirb-scans-directories-and-files-on-web-servers/): A classic web content scanner that uses a dictionary-based attack to find hidden directories and files on web servers.
- [**dirbuster**](https://awjunaid.com/kali-linux/dirbuster-directory-brute-forcing-tool/): A multi-threaded, Java-based application for brute-forcing directories and files names on web/application servers.
- [**ffuf**](https://github.com/ffuf/ffuf): A fast web fuzzer written in Go, allowing for directory discovery, parameter fuzzing, and vhost enumeration.
- [**gobuster**](https://github.com/OJ/gobuster): A multi-purpose brute-force tool for finding hidden directories, files, DNS subdomains, and virtual hosts.
- [**feroxbuster**](https://github.com/epi052/feroxbuster): A fast, simple, and recursive content discovery tool written in Rust.
- [**kiterunner**](https://github.com/assetnote/kiterunner): A contextual content discovery tool that uses common API paths and file extensions.

### 3.2. Content & Technology Identification
- [**whatweb**](https://awjunaid.com/kali-linux/whatweb-identifies-technologies-used-by-websites/): A next-generation web scanner that identifies the technology stack of a website, including CMS, blogging platforms, JavaScript libraries, and web servers.
- [**wpscan**](https://awjunaid.com/kali-linux/wpscan-wordpress-security-scanner/): A black box WordPress security scanner used to enumerate users, themes, plugins, and identify potential vulnerabilities.
- [**cutycapt**](https://awjunaid.com/kali-linux/cutycapt-captures-web-screenshots/): A command-line utility that captures screenshots of web pages using WebKit, useful for visually documenting web applications.
- [**wappalyzer**](https://github.com/AliasIO/wappalyzer): A cross-platform utility that uncovers the technologies used on websites.

### 3.3. Vulnerability Scanning & Exploitation
- [**burpsuite**](https://awjunaid.com/kali-linux/burp-suite-the-ultimate-web-security-testing-tool/): An integrated platform for performing security testing of web applications, with tools for scanning, spidering, and exploiting vulnerabilities.
- [**sqlmap**](https://github.com/sqlmapproject/sqlmap): An open-source penetration testing tool that automates the process of detecting and exploiting SQL injection flaws.
- [**commix**](https://awjunaid.com/kali-linux/commix-automates-exploitation-of-command-injection/): A tool written in Python that automates the detection and exploitation of command injection vulnerabilities.
- [**skipfish**](https://awjunaid.com/kali-linux/skipfish-automated-web-application-security-scanner/): An active web application security reconnaissance tool that prepares an interactive sitemap for the target site by conducting a recursive crawl and dictionary-based probes.
- [**wapiti**](https://awjunaid.com/kali-linux/wapiti-scans-web-applications-for-vulnerabilities/): A web application vulnerability scanner that performs "black-box" scans, injecting payloads to find vulnerabilities like XSS, SQLi, and file inclusions.
- [**xsstrike**](https://github.com/s0md3v/XSStrike): An advanced XSS detection suite equipped with a powerful fuzzing engine and intelligent payload generator.
- [**jwt_tool**](https://github.com/ticarpi/jwt_tool): A toolkit for testing, attacking, and debugging JSON Web Tokens.
- [**corsy**](https://github.com/s0md3v/Corsy): A CORS misconfiguration scanner that identifies insecure cross-origin resource sharing policies.
- [**graphqlmap**](https://github.com/swisskyrepo/GraphQLmap): A scripting engine to interact with a GraphQL endpoint for security testing purposes.
- [**dalfox**](https://github.com/hahwul/dalfox): A parameter analysis and XSS scanner focused on speed and automation.

### 3.4. WebDAV Analysis
- [**cadaver**](https://awjunaid.com/kali-linux/cadaver-webdav-command-line-client/): A command-line WebDAV client for Unix-like systems, supporting file operations like upload, download, and directory listings.
- [**davtest**](https://awjunaid.com/kali-linux/davtest-tests-webdav-servers-for-vulnerabilities/): A tool that scans a WebDAV-enabled web server to upload test files and determine if file uploads are possible and which file types are supported.

### 3.5. Post-Exploitation & Backdoors
- [**webshells**](https://awjunaid.com/kali-linux/webshells-backdoor-web-shells-for-post-exploitation/): A collection of web-based backdoors for various languages (ASP, PHP, JSP) to maintain access to a compromised web server.
- [**weevely3**](https://github.com/epinna/weevely3): A stealthy PHP web shell that provides a command-line interface for remote administration and post-exploitation.

## 4. Password Attacks

Tools for auditing password security through various attack vectors.

### 4.1. Online Attacks
- [**hydra**](https://awjunaid.com/kali-linux/hydra-parallelized-network-login-cracker/): A powerful parallelized login cracker that supports numerous protocols for fast and flexible password brute-forcing.
- [**medusa**](https://awjunaid.com/kali-linux/medusa-fast-network-brute-forcing-tool/): A massively parallel, modular, and login brute-forcer similar to Hydra, aiming for speed and stability.
- [**ncrack**](https://awjunaid.com/kali-linux/ncrack-high-speed-network-authentication-cracker/): A high-speed network authentication cracking tool designed to be fast and reliable for protocols like RDP, SSH, HTTP, and more.
- [**thc-pptp-bruter**](https://awjunaid.com/kali-linux/thc-pptp-bruter-cracks-pptp-vpn-logins/): A tool for performing brute-force attacks against PPTP VPN endpoints.
- [**patator**](https://github.com/lanjelot/patator): A multi-purpose brute-forcing tool with a modular design for various protocols and services.
- [**crowbar**](https://github.com/galkan/crowbar): A brute-forcing tool that supports OpenVPN, RDP, SSH, and VNC protocols with a focus on reliability.
- [**keimpx**](https://github.com/inquisb/keimpx): A tool to check valid credentials across a network via SMB, RDP, and HTTP.

### 4.2. Offline Attacks
- [**john**](https://awjunaid.com/kali-linux/john-password-cracking-tool-john-the-ripper/): A fast password cracker, also known as John the Ripper, used for detecting weak passwords through various attack modes.
- [**hashcat**](https://awjunaid.com/kali-linux/hashcat-gpu-accelerated-password-cracker/): The world's fastest and most advanced password recovery utility, supporting GPU acceleration and a wide variety of hash types.
- [**hash-identifier**](https://awjunaid.com/kali-linux/hash-identifier-identifies-hash-types/): A simple Python script to identify the different types of hashes used to encrypt data.
- [**hashid**](https://awjunaid.com/kali-linux/hashid-identifies-types-of-hash-values/): Another tool for identifying hash types, functioning similarly to `hash-identifier`.
- [**ophcrack-cli**](https://awjunaid.com/kali-linux/ophcrack-cli-cracks-windows-passwords-using-lm-nt-hashes/): A command-line version of Ophcrack, a Windows password cracker based on rainbow tables for LM and NTLM hashes.
- [**samdump2**](https://awjunaid.com/kali-linux/sampasswd-tool-in-kali-linux-guide/): A utility to dump the password hashes from a Windows SAM (Security Account Manager) file.
- [**chntpw**](https://awjunaid.com/kali-linux/chntpw-resets-windows-passwords/): A utility for resetting or changing passwords on Windows systems by modifying the SAM registry file.
- [**truecrack**](https://awjunaid.com/kali-linux/truecrack-cracks-truecrypt-containers/): A password cracking tool for TrueCrypt disk encryption volumes.

### 4.3. Wordlist Generation & Profiling
- [**crunch**](https://awjunaid.com/kali-linux/crunch-tool-in-kali-linux-a-comprehensive-guide/): A wordlist generator that can create custom wordlists based on character sets and a specified pattern.
- [**cewl**](https://awjunaid.com/kali-linux/cewl-generates-wordlists-from-web-content/): A tool that spiders a target website and creates a custom wordlist based on the words found on the site.
- [**rsmangler**](https://awjunaid.com/kali-linux/rsmangler-generates-mutations-of-input-wordlists/): A tool that takes a base wordlist and applies a series of common mutations (e.g., capitalization, leet speak, common appends) to create a new, more extensive list.
- [**wordlists**](https://awjunaid.com/kali-linux/wordlists-pre-compiled-lists-of-common-passwords-for-attacks/): A directory containing various pre-compiled wordlists, such as rockyou.txt, for password cracking and dictionary attacks.
- [**seclists**](https://github.com/danielmiessler/SecLists): A comprehensive collection of multiple types of lists used during security assessments, including usernames, passwords, URLs, and fuzzing payloads.
- [**probable-wordlists**](https://github.com/berzerk0/Probable-Wordlists): A collection of curated and sorted password dictionaries based on real-world data.

### 4.4. "Passing the Hash" & Lateral Movement
- [**crackmapexec**](https://github.com/byt3bl33d3r/CrackMapExec): A swiss army knife for pentesting Windows/Active Directory environments, automating tasks like credential validation and SMB enumeration.
- [**evil-winrm**](https://github.com/Hackplayers/evil-winrm): A robust and customizable WinRM shell for remote administration and penetration testing of Windows hosts.
- [**mimikatz**](https://github.com/gentilkiwi/mimikatz): A renowned tool for extracting plaintexts passwords, hashes, PINs, and Kerberos tickets from memory on Windows systems.
- [**smbmap**](https://github.com/ShawnDEvans/smbmap): A handy SMB enumeration tool (also listed under service analysis) that is crucial for post-exploitation and lateral movement.
- [**xfreedp**](https://github.com/FreeRDP/FreeRDP): A free implementation of the Remote Desktop Protocol (RDP) client, used for connecting to Windows systems, often in a post-exploitation context.
- [**sprayhound**](https://github.com/Hackndo/sprayhound): A password spraying tool integrated with BloodHound for Active Directory reconnaissance.

## 5. Wireless Attacks

This category covers tools for auditing and attacking wireless networks.

- [**aircrack-ng**](https://github.com/aircrack-ng/aircrack-ng): A complete suite of tools for assessing Wi-Fi network security, focusing on monitoring, attacking, testing, and cracking WEP and WPA/WPA2 keys.
- [**kismet**](https://github.com/kismetwireless/kismet): A wireless network detector, sniffer, and intrusion detection system that works with any wireless card which supports raw monitoring mode.
- [**wifite**](https://github.com/derv82/wifite2): An automated wireless attack tool for cracking WEP, WPA, and WPA2 networks.
- [**reaver**](https://github.com/t6x/reaver-wps-fork-t6x): A tool for brute-forcing the WPS (Wi-Fi Protected Setup) PIN to recover WPA/WPA2 passphrases.
- [**bully**](https://github.com/aanarchyy/bully): Another implementation of the WPS brute-force attack, written in C, designed to be more portable and efficient than Reaver.
- [**pixiwps**](https://github.com/wiire/pixiewps): A tool for offline brute-forcing of WPS PINs by exploiting a computational flaw (Pixie Dust attack) in many routers.
- [**wash**](https://github.com/t6x/reaver-wps-fork-t6x): A tool that scans for access points with WPS enabled, providing crucial information needed for attacks with Reaver or Bully.
- [**fern-wifi-cracker**](https://github.com/savio-code/fern-wifi-cracker): A graphical user interface tool for wireless security testing, supporting various attacks like WEP/WPA cracking and WPS attacks.
- [**spooftooph**](https://github.com/sensepost/spooftooph): A tool designed for spoofing and manipulating Bluetooth devices and log files.
- [**bettercap**](https://github.com/bettercap/bettercap): A powerful, modular, and portable MITM framework that can be used for Wi-Fi, Bluetooth, and network attacks.
- [**mdk4**](https://github.com/aircrack-ng/mdk4): A proof-of-concept tool to exploit common IEEE 802.11 protocol weaknesses.
- [**horst**](https://github.com/br101/horst): A wireless network analysis tool that works as a spectrum analyzer and packet sniffer.

## 6. Sniffing & Spoofing

These tools are used to intercept, manipulate, and analyze network traffic.

- [**wireshark**](https://www.wireshark.org/): The world's foremost and widely-used network protocol analyzer, enabling deep inspection of hundreds of protocols.
- [**tcpdump**](https://www.tcpdump.org/): A powerful command-line packet analyzer used for capturing and displaying network traffic.
- [**tshark**](https://www.wireshark.org/docs/man-pages/tshark.html): The command-line version of Wireshark, useful for scripting and remote packet capture.
- [**ettercap-pkexec**](https://github.com/Ettercap/ettercap): A comprehensive suite for man-in-the-middle attacks, supporting active and passive dissection of many protocols.
- [**responder**](https://github.com/lgandx/Responder): A tool for poisoning LLMNR, NBT-NS, and MDNS protocols to capture credentials on a local network.
- [**scapy**](https://github.com/secdev/scapy): A powerful Python-based interactive packet manipulation program and library for crafting, sending, and sniffing network packets.
- [**dsniff**](https://github.com/dugsong/dsniff): A collection of tools for network auditing and penetration testing, including tools for password sniffing and traffic interception.
- [**sslsplit**](https://github.com/droe/sslsplit): A tool for man-in-the-middle attacks against SSL/TLS encrypted network connections.
- [**dnschef**](https://github.com/iphelix/dnschef): A highly configurable DNS proxy that can be used to manipulate DNS responses for testing purposes.
- [**netsniff-ng**](http://netsniff-ng.org/): A high-performance Linux networking toolkit for packet sniffing, traffic generation, and analysis.
- [**tcpreplay**](https://github.com/appneta/tcpreplay): A suite of tools to replay captured network traffic at various speeds, useful for testing network devices and security systems.
- [**dns-rebind**](https://github.com/brannondorsey/dns-rebind): A tool for performing DNS rebinding attacks to bypass same-origin policy and access internal network resources.
- [**macchanger**](https://github.com/alobbs/macchanger): A utility for viewing and changing the MAC address of network interfaces.
- [**minicom**](https://salsa.debian.org/minicom-team/minicom): A text-based modem control and terminal emulation program for communicating with serial devices.

## 7. Exploitation Tools

Tools for developing, executing, and managing exploits against vulnerable targets.

- [**metasploit-framework**](https://github.com/rapid7/metasploit-framework): An advanced open-source platform for developing, testing, and executing exploits against remote targets.
- [**searchsploit**](https://github.com/offensive-security/exploitdb): A command-line search tool for the Exploit Database, allowing you to find public exploits and shellcode.
- [**setoolkit**](https://github.com/trustedsec/social-engineer-toolkit): The Social-Engineer Toolkit (SET) is a framework for automating advanced social engineering attacks.
- [**sqlmap**](https://github.com/sqlmapproject/sqlmap): (Also in Web Analysis) Automates the detection and exploitation of SQL injection flaws.
- [**crackmapexec**](https://github.com/byt3bl33d3r/CrackMapExec): (Also in Password Attacks) A powerful tool for automating exploitation and post-exploitation of Windows networks.
- [**msfpc**](https://github.com/g0tmi1k/msfpc): The Metasploit Payload Creator, a quick way to generate various Meterpreter reverse shells.

## 8. Post-Exploitation & Tunneling

Tools used after initial access to maintain persistence, move laterally, and exfiltrate data.

- [**proxychains4**](https://github.com/haad/proxychains): A tool that forces any TCP connection made by a program to go through a proxy (or a chain of proxies).
- [**weeevely**](https://github.com/epinna/weevely3): A stealthy PHP web shell that provides a command-line interface for managing a compromised web server.
- [**powersploit**](https://github.com/PowerShellMafia/PowerSploit): A collection of Microsoft PowerShell modules that can be used for post-exploitation tasks during penetration tests.
- [**evil-winrm**](https://github.com/Hackplayers/evil-winrm): (Also in Password Attacks) A WinRM shell for Windows, often used for post-exploitation.
- [**stunnel4**](https://www.stunnel.org/): A program that allows you to encrypt arbitrary TCP connections inside SSL/TLS.
- [**proxytunnel**](https://github.com/proxytunnel/proxytunnel): A tool that connects stdin and stdout to a remote server via an HTTPS proxy.
- [**ptunnel**](https://github.com/lnslbrty/ptunnel-ng): A tool for tunneling TCP connections over ICMP echo request and reply packets.
- [**pwnat**](https://github.com/samyk/pwnat): A tool that punches holes through NATs and firewalls, allowing clients to directly connect to a server behind NAT without port forwarding.
- [**udptunnel**](https://github.com/microchip-ung/udp-tunnel): A tool to tunnel UDP packets over a TCP connection, useful for bypassing firewalls.
- [**dns2tcpc**](https://github.com/alex-sector/dns2tcp): A client tool for tunneling TCP traffic over DNS.
- [**dns2tcpd**](https://github.com/alex-sector/dns2tcp): The server-side component for the DNS2TCP tunneling tool.
- [**iodine-client-start**](https://github.com/yarrick/iodine): A client for the Iodine DNS tunneling tool, which creates an IP tunnel over DNS.
- [**miredo**](https://github.com/ytakano/miredo): A Teredo tunneling client that provides IPv6 connectivity behind NAT devices over IPv4 networks.
- [**laudanum**](https://github.com/jbarcia/WebShells/tree/master/laudanum): A collection of injectable files, intended to be used as a covert channel or for data exfiltration.
- [**dbd**](https://github.com/git收集/DBD): A tool for creating and managing database dumps, often used in post-exploitation to exfiltrate data.
- [**sbd**](https://github.com/geocar/sbd): A tool that creates a backdoor and can communicate over AES-encrypted raw sockets or DNS.
- [**exe2hex**](https://github.com/g0tmi1k/exe2hex): A tool for converting executable files into a hexadecimal representation that can be pasted into a shell.
- [**sslh**](https://github.com/yrutschle/sslh): (Also in SSL Analysis) A protocol multiplexer useful for hiding SSH traffic on port 443.
- [**empire**](https://github.com/BC-SECURITY/Empire): A post-exploitation framework that uses PowerShell agents without powershell.exe.
- [**pwncat**](https://github.com/calebstewart/pwncat): A netcat-like tool with advanced features like auto-completion and scriptable interaction.
- [**chisel**](https://github.com/jpillora/chisel): A fast TCP tunnel over HTTP, useful for tunneling through firewalls.
- [**ligolo-ng**](https://github.com/nicocha30/ligolo-ng): An advanced tunneling tool that creates a network tunnel from a reverse connection.

## 9. Reverse Engineering

Tools for analyzing and understanding the inner workings of software binaries.

- [**radare2**](https://github.com/radareorg/radare2): A complete framework for reverse-engineering and analyzing binaries, featuring a powerful command-line interface.
- [**clang**](https://clang.llvm.org/): A compiler front end for the C family of languages, useful for analyzing compilation processes.
- **clang++**: The C++ compiler front end of the Clang project.
- [**msf-nasm_shell**](https://github.com/rapid7/metasploit-framework): A Metasploit tool that acts as a NASM-compatible assembler and disassembler, helpful for creating shellcode.
- [**ghidra**](https://github.com/NationalSecurityAgency/ghidra): A software reverse engineering (SRE) suite of tools developed by the NSA, supporting a wide range of processors and executables.
- [**gdb**](https://www.sourceware.org/gdb/): The GNU Project debugger, allowing you to see what is going on 'inside' a program while it executes.
- [**ida-free**](https://hex-rays.com/ida-free/): The freeware version of IDA Pro, a powerful disassembler and debugger.
- [**x64dbg**](https://github.com/x64dbg/x64dbg): An open-source Windows debugger for 64-bit applications.
- [**ollydbg**](http://www.ollydbg.de/): A 32-bit assembler-level debugger for Windows with a focus on binary code analysis.
- [**cutter**](https://github.com/rizinorg/cutter): A GUI for radare2, making reverse engineering more accessible.
- [**angr**](https://github.com/angr/angr): A platform-agnostic binary analysis framework developed at UCSB's Seclab.

## 10. Forensics

Tools for investigating, analyzing, and recovering data from digital media.

- [**autopsy**](https://github.com/sleuthkit/autopsy): A digital forensics platform and graphical interface to The Sleuth Kit, used for analyzing hard drives and smartphones.
- [**binwalk**](https://github.com/ReFirmLabs/binwalk): A tool for searching binary images for embedded files and executable code, commonly used for firmware analysis.
- [**bulk_extractor**](https://github.com/simsong/bulk_extractor): A high-performance digital forensics tool that scans disk images and extracts important information without parsing the file system.
- [**magicrescue**](https://github.com/jbj/magicrescue): A tool for recovering files from damaged or corrupted filesystems by scanning block devices for known file types.
- [**scalpel**](https://github.com/sleuthkit/scalpel): A fast file carver that reads a database of header and footer definitions and extracts matching files from a set of image files.
- [**scrounge-ntfs**](https://github.com/rick-colosi/scrounge-ntfs): A data recovery utility for NTFS filesystems that can reconstruct data from a damaged partition.
- [**guymager**](https://guymager.sourceforge.io/): A fast and user-friendly forensic imager for creating disk images and verifying their integrity with hashes.
- [**pdf-parser**](https://blog.didierstevens.com/programs/pdf-tools/): A tool to parse and analyze PDF files, extracting key information about their structure without rendering them.
- [**pdfid**](https://blog.didierstevens.com/programs/pdf-tools/): A simple tool to scan a PDF file for certain keywords and characteristics, useful for detecting potentially malicious PDFs.
- [**hashdeep**](https://github.com/jessek/hashdeep): A program for computing, matching, and auditing hash sets of files, ensuring data integrity and aiding in file identification.
- [**volatility**](https://github.com/volatilityfoundation/volatility): An advanced memory forensics framework for analyzing RAM dumps.
- [**foremost**](https://github.com/korczis/foremost): A console program to recover files based on their headers, footers, and internal data structures.
- [**sleuthkit**](https://github.com/sleuthkit/sleuthkit): A collection of command-line tools for forensic analysis of disk images.
- [**dcfldd**](https://github.com/resurrecting-open-source-projects/dcfldd): An enhanced version of dd with features useful for forensics and security.
- [**regripper**](https://github.com/keydet89/RegRipper3.0): A tool for extracting and analyzing Windows registry data.
- [**xplico**](https://github.com/xplico/xplico): A network forensics analysis tool that reconstructs the contents of captured data.

## 11. Mobile Security

Tools for analyzing and testing mobile applications and devices.

- [**apktool**](https://github.com/iBotPeaches/Apktool): A tool for reverse engineering Android apps, allowing you to decode resources and rebuild them.
- [**dex2jar**](https://github.com/pxb1988/dex2jar): A tool to convert Android .dex files to .class files (JAR format).
- [**jadx**](https://github.com/skylot/jadx): A Dex to Java decompiler that produces readable Java source code from APK files.
- [**mobsf**](https://github.com/MobSF/Mobile-Security-Framework-MobSF): An automated mobile app security testing framework for Android and iOS.
- [**objection**](https://github.com/sensepost/objection): A runtime mobile exploration toolkit powered by Frida for security testing.
- [**frida**](https://github.com/frida/frida): A dynamic instrumentation toolkit for developers and reverse engineers on multiple platforms.
- [**androguard**](https://github.com/androguard/androguard): A full Python tool for reverse engineering Android applications.
- [**adb**](https://developer.android.com/studio/command-line/adb): The Android Debug Bridge, a versatile command-line tool for communicating with Android devices.

## 12. Cloud Security

Tools for auditing and securing cloud infrastructure.

- [**pacu**](https://github.com/RhinoSecurityLabs/pacu): An AWS exploitation framework designed for testing the security of AWS environments.
- [**cloudsploit**](https://github.com/aquasecurity/cloudsploit): A cloud security scanning tool for AWS, Azure, and Google Cloud.
- [**scoutsuite**](https://github.com/nccgroup/ScoutSuite): A multi-cloud security auditing tool that assesses the security posture of cloud environments.
- [**s3scanner**](https://github.com/sa7mon/S3Scanner): A tool for scanning and enumerating AWS S3 buckets.
- [**cloudsplaining**](https://github.com/salesforce/cloudsplaining): An AWS IAM security assessment tool that identifies violations of least privilege.
- [**kube-hunter**](https://github.com/aquasecurity/kube-hunter): A tool for hunting security weaknesses in Kubernetes clusters.
- [**trivy**](https://github.com/aquasecurity/trivy): A comprehensive vulnerability scanner for containers and other artifacts.
- [**docker-bench-security**](https://github.com/docker/docker-bench-security): A script that checks for dozens of common best-practices around deploying Docker containers in production.
- [**falco**](https://github.com/falcosecurity/falco): A cloud-native runtime security project for Kubernetes and container environments.

## 13. Container Security

Specialized tools for container security assessment.

- [**grype**](https://github.com/anchore/grype): A vulnerability scanner for container images and filesystems.
- [**dockle**](https://github.com/goodwithtech/dockle): A container image linter for security, helping to identify best practice violations.
- [**kubeaudit**](https://github.com/Shopify/kubeaudit): A command-line tool to audit Kubernetes clusters for security issues.
- [**kube-bench**](https://github.com/aquasecurity/kube-bench): A tool that checks Kubernetes clusters against the CIS Kubernetes Benchmark.
- [**kubesec**](https://github.com/controlplaneio/kubesec): A security risk analysis tool for Kubernetes resources.

## 14. Physical Security/Hardware Hacking

Tools for testing physical security devices and hardware.

- [**wifipumpkin3**](https://github.com/P0cL4bs/wifipumpkin3): A powerful framework for creating rogue access points and MITM attacks.
- [**fluxion**](https://github.com/FluxionNetwork/fluxion): A tool for creating evil twin attacks to capture WPA handshakes.
- [**wifiphisher**](https://github.com/wifiphisher/wifiphisher): A rogue Access Point framework for conducting red team engagements.
- [**proxmark3**](https://github.com/Proxmark/proxmark3): A RFID/NFC cloning and analysis tool.
- [**hcitool**](http://www.bluez.org/): A Bluetooth testing tool included in the BlueZ package.
- [**ubertooth**](https://github.com/greatscottgadgets/ubertooth): An open-source 2.4 GHz wireless development platform for Bluetooth experimentation.

## 15. Steganography

Tools for hiding and discovering hidden data within files.

- [**steghide**](https://github.com/StefanoDeVuono/steghide): A steganography program that hides data in various image and audio files.
- [**zsteg**](https://github.com/zed-0xff/zsteg): A tool for detecting steganography in PNG and BMP files.
- [**stegsolve**](https://github.com/zardus/ctf-tools/tree/master/stegsolve): A tool for solving steganography challenges by applying various transformations.
- [**outguess**](https://github.com/crorvick/outguess): A steganography tool for hiding data in the redundant bits of data sources.
- [**stegdetect**](https://github.com/abeluck/stegdetect): An automated tool for detecting steganographic content in image files.
- [**exiftool**](https://github.com/exiftool/exiftool): A tool for reading, writing, and editing metadata in files.

## 16. Anonymity & Privacy

Tools for maintaining anonymity during security assessments.

- [**torbrowser-launcher**](https://github.com/micahflee/torbrowser-launcher): A tool to download and launch the Tor Browser Bundle.
- [**torsocks**](https://github.com/dgoulet/torsocks): A wrapper to safely torify applications.
- [**nyx**](https://github.com/torproject/nyx): A command-line monitor for the Tor status and bandwidth usage.
- [**onionprobe**](https://github.com/athoune/onionprobe): A tool for monitoring the status of Onion services.
- [**anonsurf**](https://github.com/Und3rf10w/kali-anonsurf): A tool for anonymizing the entire system by routing traffic through Tor.

## 17. Reporting Tools

Tools to assist in documenting findings and creating professional penetration test reports.

- [**cherrytree**](https://www.giuspen.com/cherrytree/): A hierarchical note-taking application that allows you to organize information in a tree structure, ideal for pentest documentation.
- [**cutycapt**](https://github.com/0x09al/cutycapt): (Also in Web Analysis) A tool for capturing screenshots of web pages, which can be embedded in reports for visual evidence.
- [**pipal**](https://github.com/digininja/pipal): A statistical analysis tool for password dumps that provides metrics to include in reports about password strength and complexity.
- [**dradis**](https://github.com/dradis/dradis-ce): A collaboration and reporting platform for security assessments.
- [**faraday**](https://github.com/infobyte/faraday): An integrated pentest environment that helps with collaboration and reporting.
- [**serpico**](https://github.com/SerpicoProject/Serpico): A penetration testing collaboration and reporting tool.

## 18. Social Engineering

Tools focused on human interaction and deception to gain access.

- [**setoolkit**](https://github.com/trustedsec/social-engineer-toolkit): (Also in Exploitation Tools) The Social-Engineer Toolkit, a framework for attacks like spear-phishing, credential harvesting, and website cloning.
- [**msfpc**](https://github.com/g0tmi1k/msfpc): (Also in Exploitation Tools) The Metasploit Payload Creator, used to generate payloads for social engineering campaigns.
- [**Phishing**](https://github.com/aw-junaid/Kali-Linux/blob/main/Kali%20Linux%20Tools/Phishing/zphisher.md) - [**zphisher**](https://github.com/htr-tech/zphisher): An automated, feature-rich phishing tool with a wide variety of pre-made templates for popular websites.
- [**gophish**](https://github.com/gophish/gophish): An open-source phishing framework that makes it easy to launch and track phishing campaigns.
- [**kingphisher**](https://github.com/securestate/king-phisher): A tool for creating and managing multiple simultaneous phishing attacks.
- [**evilginx2**](https://github.com/kgretzky/evilginx2): A man-in-the-middle attack framework for phishing credentials and session cookies with 2FA bypass.
- [**modlishka**](https://github.com/drk1wi/Modlishka): A flexible and powerful reverse proxy for phishing campaigns.
- [**hiddeneye**](https://github.com/DarkSecDevelopers/HiddenEye): A phishing tool with modern techniques and security bypass methods.
- [**blackeye**](https://github.com/An0nUD4Y/blackeye): A phishing toolkit with many website templates.

## 19. Custom Wordlists & Dictionaries

Comprehensive collections for password attacks and content discovery.

- [**seclists**](https://github.com/danielmiessler/SecLists): The most comprehensive collection of wordlists for security assessments.
- [**probable-wordlists**](https://github.com/berzerk0/Probable-Wordlists): A collection of curated and sorted password dictionaries based on real-world data.
- [**fuzzdb**](https://github.com/fuzzdb-project/fuzzdb): A dictionary of attack patterns and discovery wordlists for fuzzing.
- [**rockyou**](https://github.com/brannondorsey/naive-hashcat/releases/download/data/rockyou.txt): The famous RockYou password wordlist from the 2009 data breach.
- [**assetnote-wordlists**](https://github.com/assetnote/wordlists): A collection of wordlists for content discovery and subdomain enumeration.

---
