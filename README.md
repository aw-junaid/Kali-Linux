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
[![The SQL Injection Handbook](https://img.shields.io/badge/The%20SQL%20Injection%20Handbook-336791?style=for-the-badge&logo=postgresql&logoColor=white)](https://buymeacoffee.com/awjunaid/e/565571)
[![Kali Linux Unleashed](https://img.shields.io/badge/Kali%20Linux%20Unleashed-9B59B6?style=for-the-badge&logo=kalilinux&logoColor=white)](https://buymeacoffee.com/awjunaid/e/558655)
[![359 Python Automation Scripts](https://img.shields.io/badge/359%20Python%20Automation%20Scripts-3776AB?style=for-the-badge&logo=python&logoColor=FFD43B)](https://buymeacoffee.com/awjunaid/e/558147)

**A guide to using Kali Linux tools for web penetration testing, ethical hacking, forensics, and bug bounty. Covers setup, key tools, methodologies, and best practices. Optimized for security professionals.**


> [!Note]
> This project is intended for educational and ethical purposes only. Unauthorized use, distribution, or modification of these tools without proper consent is prohibited. By using this repository, you agree to comply with all applicable laws and ethical guidelines. The author is not responsible for any misuse or damage caused by the tools provided herein.


## 1. Information Gathering

This phase involves collecting as much data as possible about a target system or network.

### 1.1. DNS Analysis
Tools for enumerating DNS records and identifying subdomains.

- [**dnsenum**](https://awjunaid.com/ethical-hacking/dnsenum-multithreaded-tool-for-dns-enumeration/): A multithreaded Perl script to enumerate DNS information from a domain, discover non-contiguous IP blocks, and perform reverse lookups.
- [**whois**](https://awjunaid.com/kali-linux/whois-complete-guide-to-domain-registration-and-ownership-lookup-using-kali-linux/): A tool for querying domain registration and ownership records, useful for early-stage reconnaissance.
- [**nslookup**](https://awjunaid.com/kali-linux/nslookup-complete-guide-to-dns-query-and-domain-name-troubleshooting-using-kali-linux/): A DNS query tool for looking up domain name records and troubleshooting resolution issues.
- [**dig**](https://awjunaid.com/kali-linux/dig-complete-guide-to-dns-lookup-and-network-troubleshooting-using-kali-linux/): A flexible DNS lookup utility used to query name servers and inspect DNS record types in detail.
- [**dnsdumpster**](https://awjunaid.com/kali-linux/dnsdumpster-the-complete-guide-to-dns-reconnaissance-for-security-researchers/): A DNS reconnaissance tool that maps a domain's visible infrastructure, including subdomains and related hosts.
- [**assetfinder**](https://awjunaid.com/kali-linux/assetfinder-complete-guide-to-asset-discovery-and-subdomain-enumeration-using-kali-linux/): A tool that finds domains and subdomains related to a given domain, using multiple public data sources.
- [**dnsmap**](https://awjunaid.com/kali-linux/dnsmap-subdomain-brute-forcing-tool/): A passive DNS mapping tool that performs brute-force subdomain discovery to identify hidden or non-linked hosts.
- [**dnsrecon**](https://awjunaid.com/kali-linux/dnsrecon-perform-dns-enumeration-and-zone-transfers/): A versatile DNS enumeration script that checks for zone transfers, performs SRV record enumeration, and supports various discovery techniques.
- [**fierce**](https://awjunaid.com/kali-linux/fierce-dns-reconnaissance-tool-for-locating-non-contiguous-ip-space/): A DNS reconnaissance tool for locating non-contiguous IP space and identifying domain names, often used as a last resort before a full port scan.
- [**subfinder**](https://awjunaid.com/kali-linux/subfinder-complete-guide-to-fast-passive-subdomain-enumeration-using-kali-linux/): A powerful subdomain discovery tool that focuses on speed and reliability, using passive online sources to enumerate valid subdomains.
- [**aquatone**](https://awjunaid.com/kali-linux/aquatone-complete-guide-to-web-application-screenshotting-and-attack-surface-visualization-using-kali-linux/): A tool for visual inspection of websites across many hosts, providing screenshots and HTTP response data for easy analysis.
- [**gobuster**](https://github.com/OJ/gobuster): A multi-purpose tool for brute-forcing URIs (directories and files), DNS subdomains, and virtual host names.
- [**shuffledns**](https://github.com/projectdiscovery/shuffledns): A wrapper around massdns that enumerates subdomains using a wordlist and various resolvers.

### 1.2. OSINT Analysis
Open-Source Intelligence (OSINT) tools for gathering information from publicly available sources.

- [**maltego**](https://awjunaid.com/kali-linux/maltego-open-source-intelligence-and-forensics-platform/): An interactive data mining tool that renders directed graphs for link analysis, allowing you to uncover relationships between people, companies, domains, and more.
- [**spiderfoot**](https://awjunaid.com/kali-linux/spiderfoot-automated-osint-tool-for-threat-intelligence/): An automated OSINT tool that integrates with numerous data sources to collect intelligence on targets, including IP addresses, domains, email addresses, and names.
- [**recon-ng**](https://awjunaid.com/kali-linux/recon-ng-osint-framework-for-automated-reconnaissance/): A full-featured Web Reconnaissance framework written in Python, providing a powerful environment for automated OSINT collection.
- [**theHarvester**](https://awjunaid.com/kali-linux/theharvester-complete-guide-to-osint-email-and-subdomain-enumeration-using-kali-linux/): A tool for gathering emails, subdomains, hosts, employee names, open ports, and banners from different public sources like search engines and PGP key servers.
- [**sherlock**](https://awjunaid.com/kali-linux/sherlock-complete-guide-to-username-enumeration-across-social-media-using-kali-linux/): A powerful tool to hunt down usernames across hundreds of social networks, making it invaluable for social media intelligence.
- [**waybackurls**](https://awjunaid.com/kali-linux/waybackurls-complete-guide-to-historical-url-enumeration-using-kali-linux/): Fetch URLs from the Wayback Machine for a given domain, useful for discovering hidden endpoints.
- [**gau**](https://awjunaid.com/kali-linux/gau-complete-guide-to-historical-url-collection-and-web-asset-discovery-using-kali-linux/): Get All URLs - Fetch known URLs from AlienVault's Open Threat Exchange, the Wayback Machine, and Common Crawl.
- [**shodan**](https://awjunaid.com/kali-linux/shodan-cli-complete-guide-to-internet-connected-device-reconnaissance-using-kali-linux/): The official command-line interface for Shodan, allowing you to search for internet-connected devices and services.
- [**foca**](https://awjunaid.com/kali-linux/foca-complete-guide-to-metadata-analysis-and-information-gathering-using-kali-linux/): A tool for finding metadata and hidden information in documents published on a target's website.
- [**metagoofil**](https://awjunaid.com/kali-linux/metagoofil-complete-guide-to-document-metadata-extraction-and-osint-using-kali-linux/): An information-gathering tool that extracts metadata from public documents belonging to a target organization.
- [**phoneinfoga**](https://awjunaid.com/kali-linux/phoneinfoga-complete-guide-to-phone-number-intelligence-and-osint-using-kali-linux/): An OSINT tool for gathering information on phone numbers, including carrier and location data.
- [**ghunt**](https://awjunaid.com/kali-linux/ghunt-complete-guide-to-google-account-osint-and-information-gathering-using-kali-linux/): An OSINT tool for investigating Google accounts and the information they expose.
- [**holehe**](https://awjunaid.com/kali-linux/holehe-complete-guide-to-email-account-enumeration-and-osint-using-kali-linux/): A tool that checks whether an email address is registered on various websites, aiding account enumeration.
- [**pastehunter**](https://awjunaid.com/kali-linux/pastehunter-a-practical-guide-to-automated-paste-site-monitoring-for-leaked-data/): A tool for monitoring paste sites for leaked credentials and sensitive data related to a target.

### 1.3. Live Host & Route Analysis
Tools for identifying live systems on a network and analyzing network paths.

- [**netdiscover**](https://awjunaid.com/kali-linux/netdiscover-active-passive-reconnaissance-tool-for-networks/): An active/passive ARP reconnaissance tool for discovering live hosts on a local network, useful for wardriving and network inventory.
- [**nmap**](https://awjunaid.com/kali-linux/nmap-network-mapping-and-port-scanning-tool/): The industry-standard network exploration and security auditing tool, used for host discovery, port scanning, version detection, and OS fingerprinting.
- [**masscan**](https://awjunaid.com/kali-linux/masscan-mass-ip-scanner-with-fast-scanning-speed/): A high-performance TCP port scanner that can scan the entire internet in minutes, transmitting packets at a very high rate.
- [**unicornscan**](https://awjunaid.com/kali-linux/unicornscan-network-reconnaissance-and-port-scanner/): A sophisticated network reconnaissance and port scanning tool with a high degree of control over packet transmission and data collection.
- [**fping**](https://awjunaid.com/kali-linux/fping-high-performance-ping-sweep-tool/): A high-performance ping tool capable of sending ICMP echo requests to multiple hosts in parallel, ideal for large-scale host discovery.
- [**hping3**](https://awjunaid.com/kali-linux/hping3-tcp-ip-packet-assembler-for-testing-network-security/): A command-line TCP/IP packet assembler and analyzer, often used for advanced port scanning, firewall testing, and manual path MTU discovery.
- [**arping**](https://awjunaid.com/kali-linux/arping-arp-level-ping-to-find-live-hosts-on-a-network/): A utility for sending ARP requests to discover and probe hosts on a local network, bypassing IP-level filters.
- [**thc-ipv6**](https://awjunaid.com/kali-linux/thc-ipv6-is-a-suite-of-tools-for-attacking-and-auditing-ipv6-networks/): A comprehensive suite of tools for attacking the inherent protocol weaknesses of IPv6 and ICMP6, essential for modern network audits.
- [**netmask**](https://awjunaid.com/kali-linux/netmask-analyzes-and-manages-ip-subnets/): A simple but useful tool for analyzing and managing IP subnets, converting between different netmask formats.
- [**httprobe**](https://github.com/tomnomnom/httprobe): A tool to probe for working HTTP and HTTPS servers from a list of hosts.
- [**naabu**](https://github.com/projectdiscovery/naabu): A fast port scanner written in Go that focuses on accuracy and simplicity.
- [**httpx**](https://awjunaid.com/kali-linux/httpx-complete-guide-to-http-probing-and-web-service-discovery-using-kali-linux/): A fast and multi-purpose HTTP toolkit that allows running multiple probes using the retryablehttp library.
- [**traceroute**](https://awjunaid.com/kali-linux/traceroute-complete-guide-to-network-path-discovery-and-troubleshooting-using-kali-linux/): A network diagnostic tool for tracing the path packets take to reach a destination host.
- [**arp-scan**](https://awjunaid.com/kali-linux/arp-scan-complete-guide-to-arp-based-network-discovery-and-host-enumeration-using-kali-linux/): An ARP-based network discovery tool for enumerating live hosts on a local network segment.
- [**rustscan**](https://awjunaid.com/kali-linux/rustscan-complete-guide-to-high-speed-port-scanning-and-service-discovery-using-kali-linux/): A high-speed port scanner written in Rust, often used to feed results into Nmap for deeper scanning.
- [**ping**](https://awjunaid.com/kali-linux/ping-complete-guide-to-network-connectivity-testing-and-host-availability-using-kali-linux/): A basic connectivity testing utility used to check whether a host is reachable on the network.

### 1.4. Service & Protocol Analysis
Specialized tools for enumerating and analyzing specific network services.

- [**nbtscan**](https://awjunaid.com/kali-linux/nbtscan-scans-for-netbios-name-information/): A scanner for NetBIOS name information, retrieving share lists, logged-in users, and MAC addresses from Windows hosts on a local network.
- [**smbmap**](https://awjunaid.com/kali-linux/smbmap-assesses-smb-shares-for-security-issues/): A handy SMB enumeration tool that allows pen testers to browse, upload, download, and execute commands on SMB shares, checking for common misconfigurations.
- [**smtp-user-enum**](https://awjunaid.com/kali-linux/smtp-user-enum-enumerates-valid-smtp-users/): A tool for enumerating valid users on SMTP servers using techniques like VRFY, EXPN, and RCPT TO.
- [**swaks**](https://awjunaid.com/kali-linux/swaks-swiss-army-knife-for-smtp-testing/): The "Swiss Army Knife" for SMTP, a featureful, flexible, and scriptable tool for testing email servers and verifying mail relays.
- [**onesixtyone**](https://awjunaid.com/kali-linux/onesixtyone-snmp-scanner-for-network-devices/): A fast and simple SNMP scanner that sends multiple community strings to a range of IP addresses to identify devices with default or weak SNMP configurations.
- [**snmp-check**](https://awjunaid.com/kali-linux/snmp-check-enumerates-snmp-devices-and-data/): A Perl script that enumerates information from SNMP devices, including running processes, open TCP ports, network interfaces, and installed software.
- [**ike-scan**](https://awjunaid.com/kali-linux/ike-scan-identifies-vpn-servers-and-devices-using-ike/): A command-line tool for discovering, fingerprinting, and testing IPsec VPN servers using IKE (Internet Key Exchange).
- [**ldapsearch**](https://awjunaid.com/kali-linux/ldapsearch-complete-guide-to-ldap-enumeration-and-directory-service-queries-using-kali-linux/): A command-line tool for querying LDAP directory services, useful for Active Directory enumeration.
- [**snmpwalk**](https://awjunaid.com/kali-linux/snmpwalk-complete-guide-to-snmp-enumeration-and-network-device-information-gathering-using-kali-linux/): A tool for walking an SNMP MIB tree to gather detailed information from network devices.

### 1.5. SSL/TLS Analysis
Tools for auditing and analyzing SSL/TLS configurations and certificates.

- [**sslscan**](https://awjunaid.com/kali-linux/sslscan-tests-ssl-tls-ciphers-and-vulnerabilities/): A fast SSL/TLS scanner that tests services for supported ciphers, protocols, and some common vulnerabilities like Heartbleed.
- [**sslyze**](https://awjunaid.com/kali-linux/sslyze-audits-ssl-tls-configurations/): A powerful and fast SSL/TLS scanning library and tool that analyzes server configurations for weak ciphers, certificate issues, and protocol support.
- [**ssldump**](https://awjunaid.com/kali-linux/ssldump-analyzes-ssl-connections/): An SSL/TLS network protocol analyzer that decodes and displays encrypted traffic, helping to identify the certificates and handshake details.
- [**sslh**](https://awjunaid.com/kali-linux/sslh-multiplexer-for-ssl-and-non-ssl-connections/): A protocol multiplexer that allows multiple services (like HTTPS, SSH, and OpenVPN) to listen on the same port by probing for and forwarding connections.

### 1.6. IDS/IPS Identification
Tools for detecting the presence of intrusion detection and prevention systems.

- [**lbd**](https://awjunaid.com/kali-linux/lbd-load-balancer-detector-for-identifying-load-balancers/): A load balancer detector that analyzes server responses to HTTP requests to determine if a domain is behind a load-balancing solution.
- [**wafw00f**](https://awjunaid.com/kali-linux/wafw00f-detect-web-application-firewalls-wafs/): A Web Application Firewall (WAF) fingerprinting tool that sends a series of malicious requests to identify the specific WAF product protecting a website.

### 1.7. General & Auxiliary Tools
- [**amass**](https://awjunaid.com/kali-linux/amass-subdomain-enumeration-tool/): An in-depth attack surface mapping and subdomain enumeration tool that uses OWASP's Amass project for active and passive reconnaissance.
- [**dmitry**](https://awjunaid.com/kali-linux/dmitry-deepmagic-information-gathering-tool/): A simple but effective tool for gathering information on a target, including subdomains, email addresses, and system uptime.
- [**netcat**](https://awjunaid.com/kali-linux/netcat-general-purpose-network-analysis-and-debugging-tool/): The "Swiss Army knife" of networking, used for reading from and writing to network connections, port scanning, and transferring files.

## 2. Vulnerability Analysis

Tools for identifying security weaknesses and potential vulnerabilities in systems and applications.

- [**nikto**](https://awjunaid.com/kali-linux/nikto-web-vulnerability-scanner-comprehensive-guide/): A comprehensive web server scanner that tests for dangerous files, outdated server software, and specific server misconfigurations.
- [**generic_chunked**](https://awjunaid.com/kali-linux/generic_chunked-checks-for-vulnerabilities-in-chunked-encoding/): A tool designed to test for vulnerabilities in chunked transfer encoding, a feature of HTTP/1.1.
- [**voiphopper**](https://awjunaid.com/kali-linux/voiphopper-tests-vlan-hopping-in-voip-networks/): A tool that tests for VLAN hopping vulnerabilities in VoIP networks by spoofing 802.1q frames.
- [**unix-privesc-check**](https://awjunaid.com/kali-linux/unix-privesc-check-identifies-privilege-escalation-paths-on-unix-systems/): A shell script that runs on Unix systems to identify common misconfigurations that could allow local privilege escalation.
- [**legion**](https://github.com/carlospolop/legion): An automated, semi-automated, and fully automated network penetration testing framework, aiding in discovery and vulnerability scanning.
- [**nuclei**](https://awjunaid.com/kali-linux/nuclei-complete-guide-to-fast-vulnerability-scanning-and-automated-security-testing-using-kali-linux/): A fast and customizable vulnerability scanner based on a simple YAML-based templating language.
- [**owasp-zap**](https://awjunaid.com/kali-linux/owasp-zap-complete-guide-to-web-application-security-testing-using-kali-linux/): An open-source web application security scanner for finding vulnerabilities during development and testing.
- [**yara**](https://awjunaid.com/kali-linux/yara-complete-guide-to-malware-detection-threat-hunting-and-rule-based-analysis-using-kali-linux/): A pattern-matching tool used by malware researchers to identify and classify malware samples via custom rules.
- [**vuls**](https://github.com/future-architect/vuls): A vulnerability scanner for Linux and FreeBSD, written in Go, with agentless architecture.
- [**clamav**](https://www.clamav.net/): An open-source antivirus engine for detecting trojans, viruses, malware, and other malicious threats.
- [**openvas**](https://www.greenbone.net/en/): A full-featured vulnerability scanner that includes a comprehensive set of network vulnerability tests.

## 3. Web Application Analysis

This section focuses on tools for assessing and attacking web applications.

### 3.1. Directory & File Discovery
- [**dirb**](https://awjunaid.com/kali-linux/dirb-scans-directories-and-files-on-web-servers/): A classic web content scanner that uses a dictionary-based attack to find hidden directories and files on web servers.
- [**dirbuster**](https://awjunaid.com/kali-linux/dirbuster-directory-brute-forcing-tool/): A multi-threaded, Java-based application for brute-forcing directories and files names on web/application servers.
- [**ffuf**](https://awjunaid.com/kali-linux/ffuf-fuzzing-web-applications-for-vulnerabilities/): A fast web fuzzer written in Go, allowing for directory discovery, parameter fuzzing, and vhost enumeration.
- [**gobuster**](https://github.com/OJ/gobuster): A multi-purpose brute-force tool for finding hidden directories, files, DNS subdomains, and virtual hosts.
- [**feroxbuster**](https://github.com/epi052/feroxbuster): A fast, simple, and recursive content discovery tool written in Rust.
- [**kiterunner**](https://github.com/assetnote/kiterunner): A contextual content discovery tool that uses common API paths and file extensions.
- [**hakrawler**](https://awjunaid.com/kali-linux/hakrawler-complete-guide-to-web-crawling-and-url-discovery-using-kali-linux/): A fast web crawler for discovering endpoints and URLs across a target application.
- [**katana**](https://awjunaid.com/kali-linux/katana-complete-guide-to-web-crawling-and-attack-surface-discovery-using-kali-linux/): A next-generation crawling and spidering framework for mapping a web application's attack surface.

### 3.2. Content & Technology Identification
- [**whatweb**](https://awjunaid.com/kali-linux/whatweb-identifies-technologies-used-by-websites/): A next-generation web scanner that identifies the technology stack of a website, including CMS, blogging platforms, JavaScript libraries, and web servers.
- [**wpscan**](https://awjunaid.com/kali-linux/wpscan-wordpress-security-scanner/): A black box WordPress security scanner used to enumerate users, themes, plugins, and identify potential vulnerabilities.
- [**cutycapt**](https://awjunaid.com/kali-linux/cutycapt-captures-web-screenshots/): A command-line utility that captures screenshots of web pages using WebKit, useful for visually documenting web applications.
- [**wappalyzer**](https://awjunaid.com/kali-linux/wappalyzer-cli-complete-guide-to-web-technology-fingerprinting-and-stack-detection-using-kali-linux/): A cross-platform utility that uncovers the technologies used on websites.
- [**cmseek**](https://awjunaid.com/kali-linux/cmseek-complete-guide-to-cms-detection-and-web-technology-enumeration-using-kali-linux/): A CMS detection and exploitation suite that identifies the content management system powering a site.
- [**eyewitness**](https://awjunaid.com/kali-linux/eyewitness-complete-guide-to-web-screenshotting-and-service-enumeration-using-kali-linux/): A tool for taking screenshots of websites and gathering basic service information across many hosts.

### 3.3. Vulnerability Scanning & Exploitation
- [**burpsuite**](https://awjunaid.com/kali-linux/burp-suite-the-ultimate-web-security-testing-tool/): An integrated platform for performing security testing of web applications, with tools for scanning, spidering, and exploiting vulnerabilities.
- [**sqlmap**](https://awjunaid.com/kali-linux/sqlmap-tool-installation-usage-and-troubleshooting/): An open-source penetration testing tool that automates the process of detecting and exploiting SQL injection flaws.
- [**commix**](https://awjunaid.com/kali-linux/commix-automates-exploitation-of-command-injection/): A tool written in Python that automates the detection and exploitation of command injection vulnerabilities.
- [**skipfish**](https://awjunaid.com/kali-linux/skipfish-automated-web-application-security-scanner/): An active web application security reconnaissance tool that prepares an interactive sitemap for the target site by conducting a recursive crawl and dictionary-based probes.
- [**wapiti**](https://awjunaid.com/kali-linux/wapiti-scans-web-applications-for-vulnerabilities/): A web application vulnerability scanner that performs "black-box" scans, injecting payloads to find vulnerabilities like XSS, SQLi, and file inclusions.
- [**xsstrike**](https://awjunaid.com/kali-linux/xsstrike-complete-guide-to-advanced-cross-site-scripting-xss-detection-and-testing-using-kali-linux/): An advanced XSS detection suite equipped with a powerful fuzzing engine and intelligent payload generator.
- [**jwt_tool**](https://github.com/ticarpi/jwt_tool): A toolkit for testing, attacking, and debugging JSON Web Tokens.
- [**corsy**](https://github.com/s0md3v/Corsy): A CORS misconfiguration scanner that identifies insecure cross-origin resource sharing policies.
- [**graphqlmap**](https://github.com/swisskyrepo/GraphQLmap): A scripting engine to interact with a GraphQL endpoint for security testing purposes.
- [**dalfox**](https://awjunaid.com/kali-linux/dalfox-complete-guide-to-automated-cross-site-scripting-xss-scanning-using-kali-linux/): A parameter analysis and XSS scanner focused on speed and automation.
- [**jsql-injection**](https://awjunaid.com/kali-linux/jsql-injection-complete-guide-to-sql-injection-testing-and-database-exploitation-using-kali-linux/): A Java-based automatic SQL injection tool for detecting and exploiting database vulnerabilities.
- [**xsshunter**](https://awjunaid.com/kali-linux/xsshunter-complete-guide-to-blind-cross-site-scripting-blind-xss-detection-using-kali-linux/): A service for detecting blind XSS vulnerabilities that would otherwise go unnoticed.
- [**nosqlmap**](https://awjunaid.com/kali-linux/nosqlmap-complete-guide-to-nosql-database-security-testing-and-exploitation-using-kali-linux/): An automated tool for auditing and exploiting NoSQL database injection vulnerabilities.
- [**beef**](https://awjunaid.com/kali-linux/beef-complete-guide-to-browser-exploitation-and-web-security-testing-using-kali-linux/): The Browser Exploitation Framework, used for assessing the security posture of a target through the web browser.
- [**routersploit**](https://awjunaid.com/kali-linux/routersploit-complete-guide-to-router-exploitation-and-embedded-device-security-testing-using-kali-linux/): An exploitation framework dedicated to embedded devices such as routers and IoT hardware.

### 3.4. WebDAV Analysis
- [**cadaver**](https://awjunaid.com/kali-linux/cadaver-webdav-command-line-client/): A command-line WebDAV client for Unix-like systems, supporting file operations like upload, download, and directory listings.
- [**davtest**](https://awjunaid.com/kali-linux/davtest-tests-webdav-servers-for-vulnerabilities/): A tool that scans a WebDAV-enabled web server to upload test files and determine if file uploads are possible and which file types are supported.

### 3.5. Post-Exploitation & Backdoors
- [**webshells**](https://awjunaid.com/kali-linux/webshells-backdoor-web-shells-for-post-exploitation/): A collection of web-based backdoors for various languages (ASP, PHP, JSP) to maintain access to a compromised web server.
- [**weevely3**](https://awjunaid.com/kali-linux/weeevely-a-web-shell-for-maintaining-access-and-performing-post-exploitation-activities/): A stealthy PHP web shell that provides a command-line interface for remote administration and post-exploitation.

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
- [**crackmapexec**](https://awjunaid.com/kali-linux/crackmapexec-a-tool-for-pentesters-to-automate-exploitation-of-windows-networks/): A swiss army knife for pentesting Windows/Active Directory environments, automating tasks like credential validation and SMB enumeration.
- [**evil-winrm**](https://awjunaid.com/kali-linux/evil-winrm-remote-administration-tool-for-windows/): A robust and customizable WinRM shell for remote administration and penetration testing of Windows hosts.
- [**mimikatz**](https://awjunaid.com/kali-linux/mimikatz-extracts-credentials-from-memory/): A renowned tool for extracting plaintexts passwords, hashes, PINs, and Kerberos tickets from memory on Windows systems.
- [**smbmap**](https://awjunaid.com/kali-linux/smbmap-enumerates-and-interacts-with-smb-shares/): A handy SMB enumeration tool (also listed under service analysis) that is crucial for post-exploitation and lateral movement.
- [**xfreedp**](https://awjunaid.com/kali-linux/xfreedp-exploits-remote-desktop-protocol-rdp/): A free implementation of the Remote Desktop Protocol (RDP) client, used for connecting to Windows systems, often in a post-exploitation context.
- [**sprayhound**](https://github.com/Hackndo/sprayhound): A password spraying tool integrated with BloodHound for Active Directory reconnaissance.
- [**netexec**](https://awjunaid.com/kali-linux/netexec-complete-guide-to-active-directory-assessment-and-network-exploitation-using-kali-linux/): The actively maintained successor to CrackMapExec, used for Active Directory assessment and exploitation.
- [**impacket**](https://awjunaid.com/kali-linux/impacket-complete-guide-to-network-protocol-exploitation-and-active-directory-attacks-using-kali-linux/): A collection of Python classes for working with network protocols, widely used for Active Directory attacks.
- [**enum4linux**](https://awjunaid.com/kali-linux/enum4linux-complete-guide-to-smb-enumeration-and-windows-network-reconnaissance-using-kali-linux/): A tool for enumerating information from Windows and Samba systems over SMB.
- [**enum4linux-ng**](https://awjunaid.com/kali-linux/enum4linux-ng-complete-guide-to-advanced-smb-enumeration-and-active-directory-reconnaissance-using-kali-linux/): A rewritten, actively maintained version of enum4linux with expanded Active Directory enumeration features.
- [**smbclient**](https://awjunaid.com/kali-linux/smbclient-complete-guide-to-smb-file-sharing-enumeration-and-remote-access-using-kali-linux/): A command-line client for accessing and enumerating SMB file shares.
- [**rpcclient**](https://awjunaid.com/kali-linux/rpcclient-complete-guide-to-windows-rpc-enumeration-and-active-directory-information-gathering-using-kali-linux/): A tool for querying Windows RPC interfaces to gather user, group, and domain information.
- [**ldapdomaindump**](https://awjunaid.com/kali-linux/ldapdomaindump-complete-guide-to-active-directory-enumeration-and-ldap-domain-analysis-using-kali-linux/): A tool that dumps and analyzes Active Directory information via LDAP into human-readable reports.

## 5. Wireless Attacks

This category covers tools for auditing and attacking wireless networks.

- [**aircrack-ng**](https://awjunaid.com/kali-linux/aircrack-ng-a-suite-for-monitoring-attacking-testing-and-cracking-wi-fi-networks/): A complete suite of tools for assessing Wi-Fi network security, focusing on monitoring, attacking, testing, and cracking WEP and WPA/WPA2 keys.
- [**kismet**](https://awjunaid.com/kali-linux/kismet-a-wireless-network-detector-sniffer-and-intrusion-detection-system/): A wireless network detector, sniffer, and intrusion detection system that works with any wireless card which supports raw monitoring mode.
- [**wifite**](https://awjunaid.com/kali-linux/wifite-automated-tool-for-cracking-wep-and-wpa-wireless-networks-using-various-attacks/): An automated wireless attack tool for cracking WEP, WPA, and WPA2 networks.
- [**reaver**](https://awjunaid.com/kali-linux/reaver-a-tool-for-breaking-wps-pins-and-cracking-wpa2-networks/): A tool for brute-forcing the WPS (Wi-Fi Protected Setup) PIN to recover WPA/WPA2 passphrases.
- [**bully**](https://awjunaid.com/kali-linux/bully-a-tool-for-exploiting-wps-vulnerabilities-in-wi-fi-networks/): Another implementation of the WPS brute-force attack, written in C, designed to be more portable and efficient than Reaver.
- [**pixiwps**](https://awjunaid.com/kali-linux/pixiwps-a-tool-for-exploiting-weak-wps-pins-on-routers-using-pixie-dust-attack/): A tool for offline brute-forcing of WPS PINs by exploiting a computational flaw (Pixie Dust attack) in many routers.
- [**wash**](https://awjunaid.com/kali-linux/wash-a-tool-for-discovering-wps-enabled-routers-to-exploit/): A tool that scans for access points with WPS enabled, providing crucial information needed for attacks with Reaver or Bully.
- [**fern-wifi-cracker**](https://awjunaid.com/kali-linux/fern-wifi-cracker-a-gui-tool-for-testing-wireless-network-security-focusing-on-wpa-wpa2-cracking/): A graphical user interface tool for wireless security testing, supporting various attacks like WEP/WPA cracking and WPS attacks.
- [**spooftooph**](https://awjunaid.com/kali-linux/spooftooph-bluetooth-hacking-tool-for-sniffing-spoofing-and-cracking-bluetooth-devices/): A tool designed for spoofing and manipulating Bluetooth devices and log files.
- [**bettercap**](https://awjunaid.com/kali-linux/bettercap-complete-guide-to-network-reconnaissance-and-wireless-security-testing-using-kali-linux/): A powerful, modular, and portable MITM framework that can be used for Wi-Fi, Bluetooth, and network attacks.
- [**mdk4**](https://github.com/aircrack-ng/mdk4): A proof-of-concept tool to exploit common IEEE 802.11 protocol weaknesses.
- [**horst**](https://github.com/br101/horst): A wireless network analysis tool that works as a spectrum analyzer and packet sniffer.

## 6. Sniffing & Spoofing

These tools are used to intercept, manipulate, and analyze network traffic.

- [**wireshark**](https://awjunaid.com/kali-linux/wireshark-complete-guide-to-packet-analysis-and-network-troubleshooting-using-kali-linux/): The world's foremost and widely-used network protocol analyzer, enabling deep inspection of hundreds of protocols.
- [**tcpdump**](https://awjunaid.com/kali-linux/tcpdump-a-packet-capture-tool-for-network-traffic-analysis/): A powerful command-line packet analyzer used for capturing and displaying network traffic.
- [**tshark**](https://awjunaid.com/kali-linux/tshark-complete-guide-to-command-line-packet-capture-and-network-traffic-analysis-using-kali-linux/): The command-line version of Wireshark, useful for scripting and remote packet capture.
- [**ettercap-pkexec**](https://awjunaid.com/kali-linux/ettercap-pkexec-a-man-in-the-middle-attack-tool-that-supports-sniffing-and-spoofing/): A comprehensive suite for man-in-the-middle attacks, supporting active and passive dissection of many protocols.
- [**responder**](https://awjunaid.com/kali-linux/responder-a-tool-for-poisoning-name-resolution-protocols-in-local-networks/): A tool for poisoning LLMNR, NBT-NS, and MDNS protocols to capture credentials on a local network.
- [**scapy**](https://awjunaid.com/kali-linux/scapy-a-python-based-tool-for-packet-crafting-and-network-exploration/): A powerful Python-based interactive packet manipulation program and library for crafting, sending, and sniffing network packets.
- [**dsniff**](https://awjunaid.com/kali-linux/dsniff-a-collection-of-network-tools-for-monitoring-and-spoofing-network-traffic/): A collection of tools for network auditing and penetration testing, including tools for password sniffing and traffic interception.
- [**sslsplit**](https://awjunaid.com/kali-linux/sslsplit-a-tool-for-intercepting-and-decrypting-ssl-tls-traffic/): A tool for man-in-the-middle attacks against SSL/TLS encrypted network connections.
- [**dnschef**](https://awjunaid.com/kali-linux/dnschef-a-dns-proxy-tool-used-for-manipulating-dns-queries/): A highly configurable DNS proxy that can be used to manipulate DNS responses for testing purposes.
- [**netsniff-ng**](https://awjunaid.com/kali-linux/netsniff-ng-a-high-performance-network-analyzer-and-packet-sniffer/): A high-performance Linux networking toolkit for packet sniffing, traffic generation, and analysis.
- [**tcpreplay**](https://awjunaid.com/kali-linux/tcpreplay-a-tool-to-replay-captured-network-traffic-for-testing-purposes/): A suite of tools to replay captured network traffic at various speeds, useful for testing network devices and security systems.
- [**dns-rebind**](https://awjunaid.com/kali-linux/dns-rebind-a-tool-for-dns-rebinding-attacks-to-bypass-security-measures/): A tool for performing DNS rebinding attacks to bypass same-origin policy and access internal network resources.
- [**macchanger**](https://awjunaid.com/kali-linux/macchanger-a-tool-for-changing-the-mac-address-of-network-interfaces/): A utility for viewing and changing the MAC address of network interfaces.
- [**minicom**](https://awjunaid.com/kali-linux/minicom-a-terminal-emulation-program-for-interacting-with-serial-devices/): A text-based modem control and terminal emulation program for communicating with serial devices.
- [**inveigh**](https://awjunaid.com/kali-linux/inveigh-complete-guide-to-llmnr-nbns-and-mdns-spoofing-using-kali-linux/): A Windows-focused spoofing and man-in-the-middle tool for LLMNR, NBNS, and mDNS poisoning.
- [**mitmf**](https://awjunaid.com/kali-linux/mitmf-complete-guide-to-man-in-the-middle-framework-and-network-traffic-manipulation-using-kali-linux/): A framework for man-in-the-middle attacks that brings together several sniffing and traffic manipulation tools.
- [**yersinia**](https://awjunaid.com/kali-linux/yersinia-complete-guide-to-layer-2-network-protocol-attacks-using-kali-linux/): A network tool for testing and exploiting weaknesses in Layer 2 protocols like STP, CDP, and DTP.
- [**zeek**](https://awjunaid.com/kali-linux/zeek-complete-guide-to-network-security-monitoring-and-traffic-analysis-using-kali-linux/): A powerful network security monitoring framework that analyzes traffic to detect anomalies and threats.
- [**networkminer**](https://awjunaid.com/kali-linux/networkminer-complete-guide-to-network-forensics-and-packet-analysis-using-kali-linux/): A network forensic analysis tool that extracts artifacts like files and credentials from captured traffic.

## 7. Exploitation Tools

Tools for developing, executing, and managing exploits against vulnerable targets.

- [**metasploit-framework**](https://awjunaid.com/kali-linux/metasploit-framework-complete-guide-to-penetration-testing-and-exploitation-using-kali-linux/): An advanced open-source platform for developing, testing, and executing exploits against remote targets.
- [**searchsploit**](https://awjunaid.com/kali-linux/searchsploit-a-command-line-tool-for-searching-exploit-dbs-public-exploits/): A command-line search tool for the Exploit Database, allowing you to find public exploits and shellcode.
- [**setoolkit**](https://awjunaid.com/kali-linux/setoolkit-a-social-engineering-framework-used-for-phishing-credential-harvesting-and-more/): The Social-Engineer Toolkit (SET) is a framework for automating advanced social engineering attacks.
- [**sqlmap**](https://awjunaid.com/kali-linux/sqlmap-an-automated-tool-for-detecting-and-exploiting-sql-injection-vulnerabilities/): (Also in Web Analysis) Automates the detection and exploitation of SQL injection flaws.
- [**crackmapexec**](https://awjunaid.com/kali-linux/crackmapexec-post-exploitation-and-penetration-testing-tool/): (Also in Password Attacks) A powerful tool for automating exploitation and post-exploitation of Windows networks.
- [**msfpc**](https://github.com/g0tmi1k/msfpc): The Metasploit Payload Creator, a quick way to generate various Meterpreter reverse shells.

## 8. Post-Exploitation & Tunneling

Tools used after initial access to maintain persistence, move laterally, and exfiltrate data.

- [**proxychains4**](https://awjunaid.com/kali-linux/proxychains4-a-tool-for-forcing-network-connections-to-go-through-proxy-servers/): A tool that forces any TCP connection made by a program to go through a proxy (or a chain of proxies).
- [**weeevely**](https://awjunaid.com/kali-linux/weeevely-a-web-shell-for-maintaining-access-and-performing-post-exploitation-activities/): A stealthy PHP web shell that provides a command-line interface for managing a compromised web server.
- [**powersploit**](https://awjunaid.com/kali-linux/powersploit-a-collection-of-powershell-scripts-used-for-post-exploitation-tasks-in-windows-environments/): A collection of Microsoft PowerShell modules that can be used for post-exploitation tasks during penetration tests.
- [**evil-winrm**](https://awjunaid.com/kali-linux/evil-winrm-remote-administration-tool-for-windows/): (Also in Password Attacks) A WinRM shell for Windows, often used for post-exploitation.
- [**stunnel4**](https://awjunaid.com/kali-linux/stunnel4-a-tool-for-creating-secure-ssl-tls-tunnels-to-protect-unencrypted-services/): A program that allows you to encrypt arbitrary TCP connections inside SSL/TLS.
- [**proxytunnel**](https://awjunaid.com/kali-linux/proxytunnel-a-tool-that-tunnels-https-traffic-through-an-http-proxy/): A tool that connects stdin and stdout to a remote server via an HTTPS proxy.
- [**ptunnel**](https://awjunaid.com/kali-linux/ptunnel-a-tool-to-create-a-tunnel-over-icmp-for-bypassing-firewalls/): A tool for tunneling TCP connections over ICMP echo request and reply packets.
- [**pwnat**](https://awjunaid.com/kali-linux/pwnat-a-nat-traversal-tool-for-reverse-shells-and-remote-control-via-nated-networks/): A tool that punches holes through NATs and firewalls, allowing clients to directly connect to a server behind NAT without port forwarding.
- [**udptunnel**](https://awjunaid.com/kali-linux/udptunnel-a-tool-for-tunneling-udp-traffic-through-a-firewall/): A tool to tunnel UDP packets over a TCP connection, useful for bypassing firewalls.
- [**dns2tcpc**](https://awjunaid.com/kali-linux/dns2tcpc-a-tool-for-tunneling-tcp-traffic-over-dns-queries-to-bypass-firewalls/): A client tool for tunneling TCP traffic over DNS.
- [**dns2tcpd**](https://awjunaid.com/kali-linux/dns2tcpd-a-server-side-tool-for-handling-dns-based-tcp-tunneling/): The server-side component for the DNS2TCP tunneling tool.
- [**iodine-client-start**](https://awjunaid.com/kali-linux/iodine-client-start-a-client-for-dns-tunneling-allows-ip-over-dns-based-network-communication/): A client for the Iodine DNS tunneling tool, which creates an IP tunnel over DNS.
- [**miredo**](https://awjunaid.com/kali-linux/miredo-a-teredo-ipv6-over-ipv4-tunneling-daemon-for-creating-a-vpn-like-connection/): A Teredo tunneling client that provides IPv6 connectivity behind NAT devices over IPv4 networks.
- [**laudanum**](https://awjunaid.com/kali-linux/laudanum-a-covert-channel-tool-for-encrypting-and-tunneling-data-over-a-network/): A collection of injectable files, intended to be used as a covert channel or for data exfiltration.
- [**dbd**](https://awjunaid.com/kali-linux/dbd-tool-in-kali-linux-complete-guide/): A tool for creating and managing database dumps, often used in post-exploitation to exfiltrate data.
- [**sbd**](https://awjunaid.com/kali-linux/sbd-a-tool-for-creating-secure-backdoors-over-dns-queries/): A tool that creates a backdoor and can communicate over AES-encrypted raw sockets or DNS.
- [**exe2hex**](https://github.com/g0tmi1k/exe2hex): A tool for converting executable files into a hexadecimal representation that can be pasted into a shell.
- [**sslh**](https://awjunaid.com/kali-linux/sslh-a-protocol-multiplexer-that-allows-services-like-https-ssh-and-openvpn-to-share-the-same-port/): (Also in SSL Analysis) A protocol multiplexer useful for hiding SSH traffic on port 443.
- [**empire**](https://github.com/BC-SECURITY/Empire): A post-exploitation framework that uses PowerShell agents without powershell.exe.
- [**pwncat**](https://github.com/calebstewart/pwncat): A netcat-like tool with advanced features like auto-completion and scriptable interaction.
- [**chisel**](https://github.com/jpillora/chisel): A fast TCP tunnel over HTTP, useful for tunneling through firewalls.
- [**ligolo-ng**](https://github.com/nicocha30/ligolo-ng): An advanced tunneling tool that creates a network tunnel from a reverse connection.

## 9. Reverse Engineering

Tools for analyzing and understanding the inner workings of software binaries.

- [**radare2**](https://awjunaid.com/kali-linux/radare2-a-framework-for-reverse-engineering-and-analyzing-binaries/): A complete framework for reverse-engineering and analyzing binaries, featuring a powerful command-line interface.
- [**clang**](https://awjunaid.com/kali-linux/clang-tool-in-kali-linux-a-comprehensive-guide/): A compiler front end for the C family of languages, useful for analyzing compilation processes.
- **clang++**: The C++ compiler front end of the Clang project.
- [**msf-nasm_shell**](https://awjunaid.com/kali-linux/msf-nasm_shell-a-metasploit-tool-for-writing-and-testing-shellcode/): A Metasploit tool that acts as a NASM-compatible assembler and disassembler, helpful for creating shellcode.
- [**ghidra**](https://github.com/NationalSecurityAgency/ghidra): A software reverse engineering (SRE) suite of tools developed by the NSA, supporting a wide range of processors and executables.
- [**gdb**](https://www.sourceware.org/gdb/): The GNU Project debugger, allowing you to see what is going on 'inside' a program while it executes.
- [**ida-free**](https://hex-rays.com/ida-free/): The freeware version of IDA Pro, a powerful disassembler and debugger.
- [**x64dbg**](https://github.com/x64dbg/x64dbg): An open-source Windows debugger for 64-bit applications.
- [**ollydbg**](http://www.ollydbg.de/): A 32-bit assembler-level debugger for Windows with a focus on binary code analysis.
- [**cutter**](https://github.com/rizinorg/cutter): A GUI for radare2, making reverse engineering more accessible.
- [**angr**](https://github.com/angr/angr): A platform-agnostic binary analysis framework developed at UCSB's Seclab.

## 10. Forensics

Tools for investigating, analyzing, and recovering data from digital media.

- [**autopsy**](https://awjunaid.com/kali-linux/autopsy-a-digital-forensics-tool-for-analyzing-hard-drives-and-smartphones-for-evidence/): A digital forensics platform and graphical interface to The Sleuth Kit, used for analyzing hard drives and smartphones.
- [**binwalk**](https://awjunaid.com/kali-linux/binwalk-a-tool-for-analyzing-and-extracting-data-from-firmware-images/): A tool for searching binary images for embedded files and executable code, commonly used for firmware analysis.
- [**bulk_extractor**](https://awjunaid.com/kali-linux/bulk_extractor-a-tool-for-extracting-useful-data-from-large-data-sets-such-as-disk-images/): A high-performance digital forensics tool that scans disk images and extracts important information without parsing the file system.
- [**magicrescue**](https://awjunaid.com/kali-linux/magicrescue-a-tool-for-recovering-files-from-damaged-filesystems/): A tool for recovering files from damaged or corrupted filesystems by scanning block devices for known file types.
- [**scalpel**](https://awjunaid.com/kali-linux/scalpel-a-file-carving-tool-for-recovering-files-from-disk-images/): A fast file carver that reads a database of header and footer definitions and extracts matching files from a set of image files.
- [**scrounge-ntfs**](https://awjunaid.com/kali-linux/scrounge-ntfs-comprehensive-guide-for-ntfs-data-recovery/): A data recovery utility for NTFS filesystems that can reconstruct data from a damaged partition.
- [**guymager**](https://awjunaid.com/kali-linux/guymager-a-forensic-imaging-tool-for-creating-disk-images-and-performing-hash-verification/): A fast and user-friendly forensic imager for creating disk images and verifying their integrity with hashes.
- [**pdf-parser**](https://awjunaid.com/kali-linux/pdf-parser-a-tool-for-parsing-and-analyzing-pdf-files-to-extract-data-or-metadata/): A tool to parse and analyze PDF files, extracting key information about their structure without rendering them.
- [**pdfid**](https://awjunaid.com/kali-linux/pdfid-a-tool-for-identifying-the-structure-and-objects-in-pdf-files/): A simple tool to scan a PDF file for certain keywords and characteristics, useful for detecting potentially malicious PDFs.
- [**hashdeep**](https://awjunaid.com/kali-linux/hashdeep-a-tool-for-computing-and-verifying-hash-values-of-files-in-a-directory/): A program for computing, matching, and auditing hash sets of files, ensuring data integrity and aiding in file identification.
- [**volatility**](https://awjunaid.com/kali-linux/volatility-complete-guide-to-memory-forensics-and-ram-analysis-using-kali-linux/): An advanced memory forensics framework for analyzing RAM dumps.
- [**foremost**](https://awjunaid.com/kali-linux/foremost-complete-guide-to-file-carving-and-data-recovery-using-kali-linux/): A console program to recover files based on their headers, footers, and internal data structures.
- [**sleuthkit**](https://awjunaid.com/kali-linux/the-sleuth-kit-complete-guide-to-digital-forensics-and-file-system-analysis-using-kali-linux/): A collection of command-line tools for forensic analysis of disk images.
- [**dcfldd**](https://github.com/resurrecting-open-source-projects/dcfldd): An enhanced version of dd with features useful for forensics and security.
- [**regripper**](https://github.com/keydet89/RegRipper3.0): A tool for extracting and analyzing Windows registry data.
- [**xplico**](https://github.com/xplico/xplico): A network forensics analysis tool that reconstructs the contents of captured data.

## 11. Mobile Security

Tools for analyzing and testing mobile applications and devices.

- [**apktool**](https://awjunaid.com/kali-linux/apktool-complete-guide-to-android-apk-reverse-engineering-and-application-analysis-using-kali-linux/): A tool for reverse engineering Android apps, allowing you to decode resources and rebuild them.
- [**dex2jar**](https://github.com/pxb1988/dex2jar): A tool to convert Android .dex files to .class files (JAR format).
- [**jadx**](https://awjunaid.com/kali-linux/jadx-complete-guide-to-android-apk-decompilation-and-source-code-analysis-using-kali-linux/): A Dex to Java decompiler that produces readable Java source code from APK files.
- [**mobsf**](https://awjunaid.com/kali-linux/mobsf-complete-guide-to-mobile-application-security-testing-and-malware-analysis-using-kali-linux/): An automated mobile app security testing framework for Android and iOS.
- [**objection**](https://awjunaid.com/kali-linux/objection-complete-guide-to-mobile-application-runtime-security-testing-using-kali-linux/): A runtime mobile exploration toolkit powered by Frida for security testing.
- [**frida**](https://awjunaid.com/kali-linux/frida-complete-guide-to-dynamic-application-instrumentation-and-runtime-analysis-using-kali-linux/): A dynamic instrumentation toolkit for developers and reverse engineers on multiple platforms.
- [**androguard**](https://github.com/androguard/androguard): A full Python tool for reverse engineering Android applications.
- [**adb**](https://developer.android.com/studio/command-line/adb): The Android Debug Bridge, a versatile command-line tool for communicating with Android devices.

## 12. Cloud Security

Tools for auditing and securing cloud infrastructure.

- [**pacu**](https://awjunaid.com/kali-linux/pacu-complete-guide-to-aws-exploitation-and-cloud-penetration-testing-using-kali-linux/): An AWS exploitation framework designed for testing the security of AWS environments.
- [**cloudsploit**](https://github.com/aquasecurity/cloudsploit): A cloud security scanning tool for AWS, Azure, and Google Cloud.
- [**scoutsuite**](https://awjunaid.com/kali-linux/scoutsuite-complete-guide-to-multi-cloud-security-auditing-and-configuration-assessment-using-kali-linux/): A multi-cloud security auditing tool that assesses the security posture of cloud environments.
- [**s3scanner**](https://awjunaid.com/kali-linux/s3scanner-complete-guide-to-amazon-s3-bucket-discovery-and-security-assessment-using-kali-linux/): A tool for scanning and enumerating AWS S3 buckets.
- [**cloudbrute**](https://awjunaid.com/kali-linux/cloudbrute-complete-guide-to-cloud-asset-discovery-and-attack-surface-enumeration-using-kali-linux/): A tool for discovering a company's infrastructure, files, and apps across multiple cloud providers.
- [**cloudsplaining**](https://github.com/salesforce/cloudsplaining): An AWS IAM security assessment tool that identifies violations of least privilege.
- [**kube-hunter**](https://awjunaid.com/kali-linux/kube-hunter-complete-guide-to-kubernetes-security-assessment-and-cluster-penetration-testing-using-kali-linux/): A tool for hunting security weaknesses in Kubernetes clusters.
- [**trivy**](https://awjunaid.com/kali-linux/trivy-complete-guide-to-container-kubernetes-and-vulnerability-scanning-using-kali-linux/): A comprehensive vulnerability scanner for containers and other artifacts.
- [**docker-bench-security**](https://awjunaid.com/kali-linux/docker-bench-complete-guide-to-docker-security-auditing-and-cis-benchmark-assessment-using-kali-linux/): A script that checks for dozens of common best-practices around deploying Docker containers in production.
- [**falco**](https://github.com/falcosecurity/falco): A cloud-native runtime security project for Kubernetes and container environments.

## 13. Container Security

Specialized tools for container security assessment.

- [**grype**](https://github.com/anchore/grype): A vulnerability scanner for container images and filesystems.
- [**dockle**](https://github.com/goodwithtech/dockle): A container image linter for security, helping to identify best practice violations.
- [**kubeaudit**](https://github.com/Shopify/kubeaudit): A command-line tool to audit Kubernetes clusters for security issues.
- [**kube-bench**](https://awjunaid.com/kali-linux/kube-bench-complete-guide-to-kubernetes-cis-benchmark-auditing-and-security-compliance-using-kali-linux/): A tool that checks Kubernetes clusters against the CIS Kubernetes Benchmark.
- [**kubesec**](https://github.com/controlplaneio/kubesec): A security risk analysis tool for Kubernetes resources.
- [**kubescape**](https://awjunaid.com/kali-linux/kubescape-complete-guide-to-kubernetes-security-scanning-and-compliance-assessment-using-kali-linux/): A Kubernetes security scanner that checks clusters against NSA-CISA and MITRE ATT&CK frameworks.

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
- [**exiftool**](https://awjunaid.com/kali-linux/exiftool-complete-guide-to-metadata-analysis-and-digital-forensics-using-kali-linux/): A tool for reading, writing, and editing metadata in files.

## 16. Anonymity & Privacy

Tools for maintaining anonymity during security assessments.

- [**torbrowser-launcher**](https://github.com/micahflee/torbrowser-launcher): A tool to download and launch the Tor Browser Bundle.
- [**torsocks**](https://github.com/dgoulet/torsocks): A wrapper to safely torify applications.
- [**nyx**](https://github.com/torproject/nyx): A command-line monitor for the Tor status and bandwidth usage.
- [**onionprobe**](https://github.com/athoune/onionprobe): A tool for monitoring the status of Onion services.
- [**anonsurf**](https://github.com/Und3rf10w/kali-anonsurf): A tool for anonymizing the entire system by routing traffic through Tor.

## 17. Reporting Tools

Tools to assist in documenting findings and creating professional penetration test reports.

- [**cherrytree**](https://awjunaid.com/kali-linux/cherrytree-a-hierarchical-note-taking-application-for-organizing-notes-and-information/): A hierarchical note-taking application that allows you to organize information in a tree structure, ideal for pentest documentation.
- [**cutycapt**](https://awjunaid.com/kali-linux/cutycapt-a-tool-for-capturing-screenshots-of-web-pages-and-converting-them-to-images/): (Also in Web Analysis) A tool for capturing screenshots of web pages, which can be embedded in reports for visual evidence.
- [**pipal**](https://awjunaid.com/kali-linux/pipal-a-tool-for-analyzing-password-statistics-from-password-dumps-to-assess-password-security/): A statistical analysis tool for password dumps that provides metrics to include in reports about password strength and complexity.
- [**dradis**](https://github.com/dradis/dradis-ce): A collaboration and reporting platform for security assessments.
- [**faraday**](https://github.com/infobyte/faraday): An integrated pentest environment that helps with collaboration and reporting.
- [**serpico**](https://github.com/SerpicoProject/Serpico): A penetration testing collaboration and reporting tool.

## 18. Social Engineering

Tools focused on human interaction and deception to gain access.

- [**setoolkit**](https://awjunaid.com/kali-linux/setoolkit-a-social-engineering-framework-used-for-phishing-credential-harvesting-and-more/): (Also in Exploitation Tools) The Social-Engineer Toolkit, a framework for attacks like spear-phishing, credential harvesting, and website cloning.
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

## 📖 More Guides & Resources

For in-depth, step-by-step guides on these tools and more, visit [**awjunaid.com**](https://awjunaid.com/) — covering Kali Linux, ethical hacking, offensive security, DevSecOps, networking, and programming.

<p align="center">
  <a href="https://awjunaid.com/">Website</a> •
  <a href="https://www.youtube.com/@awjunaid/featured">YouTube</a> •
  <a href="https://buymeacoffee.com/awjunaid">Buy Me a Coffee</a> •
  <a href="mailto:awjunaid@proton.me">Contact</a>
</p>

<p align="center">© <strong>aw-junaid</strong> — Educational use only. See the note at the top of this document.</p>

---
