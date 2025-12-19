# 🦊 DarkFox 12/05/2025

**Dark Web CTI & OSINT Investigation Framework**
<img width="1401" height="772" alt="1aDarkfox" src="https://github.com/user-attachments/assets/51cd783f-f1f1-42ca-811f-cad01ec04163" />

[![License](https://img.shields.io/badge/license-GPL--3.0-blue.svg)](LICENSE)
[![Platform](https://img.shields.io/badge/platform-Kali%20Linux-557C94.svg)](https://www.kali.org/)
[![Bash](https://img.shields.io/badge/bash-5.0+-green.svg)](https://www.gnu.org/software/bash/)

> **⚠️ LEGAL DISCLAIMER**: DarkFox is designed for authorized security research, cyber threat intelligence (CTI), and lawful OSINT investigations only. Users are responsible for complying with all applicable laws and regulations. Unauthorized access to computer systems is illegal.

---

## 🎯 What is DarkFox?
<img width="1017" height="561" alt="1darkfox" src="https://github.com/user-attachments/assets/2a05fae6-d846-4247-8ccf-add4282b6f3b" />

🦊 DarkFox is an automated Dark Web investigation framework that streamlines the OSINT/CTI workflow:
<img width="913" height="861" alt="2darkfox" src="https://github.com/user-attachments/assets/dcdb3d52-0e08-49b2-b16f-d549d6119520" />

- 🔍 **Discover** - Search for .onion sites using Ahmia
- ✅ **Verify** - Validate discovered onion addresses
- 📸 **Document** - Capture screenshots and forensic metadata without visiting the darkweb site!
- 📊 **Report** - Document and organize findings in a LibreOffice spreadsheet
- 🔒 **Secure** - Route all traffic through Tor network

**Perfect for:**
- Cyber Threat Intelligence (CTI) analysts
- Security researchers
- Law enforcement (authorized)
- OSINT investigators
- Red team operations
- Blue team operations
<img width="932" height="769" alt="4darkfox" src="https://github.com/user-attachments/assets/bd9ede29-867b-469c-8302-38df27032f3e" />

---

## ✨ Features
<img width="932" height="769" alt="5darkfox" src="https://github.com/user-attachments/assets/fe3a8bcf-7e64-4859-816f-f092ac9ef274" />

### Core Capabilities
- 🌐 **Automated Tor Integration** - Connect via TorGhostNG with country selection
- 🔎 **Dark Web Search** - pyAhmia powered onion discovery
- 🖼️ **Screenshot Capture** - GoWitness automated site screenshots
- 📝 **Investigation Documentation** - LibreOffice Calc worksheets
- 🔄 **Real-time Verification** - Check onion site availability
- 🗺️ **Network Mapping** - Track your IP changes (clearnet vs Tor)

### Security Features
- ✅ Input sanitization to prevent command injection
- ✅ Proper permission management (no 777 permissions)
- ✅ Process cleanup on exit
- ✅ Tor connection verification
- ✅ Isolated Python virtual environments
<img width="1920" height="1200" alt="6darkfox" src="https://github.com/user-attachments/assets/1a7349cc-9953-4f4a-a1b0-0fb1b3ca286c" />

---

## 🚀 Quick Start

### Prerequisites

**Required:**
- Kali Linux XFCE (or Debian-based distro)
- Root/sudo access
- Active internet connection

**Automatically Installed Requirements:**
- Tor & TorGhostNG
- pyAhmia
- GoWitness 3.0.5
- LibreOffice Calc
- Firefox ESR
- Python 3 + dependencies

### Installation

```bash
# Clone the repository
sudo git clone https://github.com/aryanguenthner/darkfox /opt/darkfox

# Navigate to directory
cd /opt/darkfox

# Make scripts executable
sudo chmod +x darkfox.sh

# Run DarkFox
sudo bash darkfox.sh
```

### First Investigation

1. **Run the tool:**
   ```bash
   sudo bash darkfox.sh
   ```

2. **Enter your search query:**
   ```
   What are you researching: cybercrime forums
   ```

3. **Wait for results:**
   - Tool searches for .onion sites
   - Connects to Tor network
   - Verifies discovered sites
   - Captures screenshots
   - Opens workspace

4. **Review CTI findings:**
   - LibreOffice opens a spreadsheet with results (Great for taking notes and keeping track of your investigation)
   - Firefox opens a visual gallery using gowitness (Examine the darkweb deepweb target without visiting the site)
   - Top relevant sites open automatically

---

## 📖 Usage

### Basic Investigation

```bash
sudo bash darkfox.sh
```

Follow the interactive prompts:
1. Enter research topic
2. Wait for onion discovery
3. Review results in workspace
4. Document findings in spreadsheet
5. Investigate findings in a visual format

### Advanced Options

**Custom Tor Exit Country:**
Edit `darkfox.sh` and modify:
```bash
connect_tor_network "nl"  # Netherlands (default)
# Options: nl, cz, de, us, ca, mx, ru, br, gb, fr, etc.
# Exit the Tor: torghostng -x --dns
```

**Adjust Screenshot Threads:**
```bash
# In darkfox.sh, find GoWitness command:
--threads 10  # Increase for faster scanning (use with caution)
```

---

## 📂 Directory Structure

After installation, DarkFox creates:

```
/opt/darkfox/
├── investigations/              # All investigation results
│   └── [topic_name_timestamp]/  # Individual investigation
│       ├── results.onion.csv    # Raw search results
│       ├── onion_page_titles.csv # Verified sites with titles
│       ├── screenshots/         # GoWitness captures
│       └── gowitness.db        # Screenshot database
├── tools/
│   ├── gowitness              # Screenshot tool
│   └── onion_verifier.py      # Verification script
├── logs/
│   ├── tor_connection.log     # Tor connection logs
│   ├── verification.log       # Onion verification logs
│   └── gowitness.log         # Screenshot capture logs
└── venv/                      # Python virtual environment
```

---

## 🔧 Components

### Integrated Tools

| Tool | Purpose | Version |
|------|---------|---------|
| **Ahmia** | Dark web search engine | 0.7.3 |
| **GoWitness** | Screenshot capture | 3.0.5 |
| **TorGhostNG** | Tor routing & anonymity | Latest |
| **LibreOffice Calc** | Documentation & reporting | Latest |
| **Firefox ESR** | .onion site browsing | Latest |

### Custom Scripts

- `darkfox.sh` - Main orchestration script
- `onion_verifier.py` - Validates .onion addresses
- Installation automation for all dependencies

---

## 🛡️ Security Considerations

### Best Practices

1. **Use a Dedicated VM**: Run DarkFox in an isolated virtual machine
2. **No Personal Info**: Never use personal accounts while investigating
3. **VPN + Tor**: Consider additional VPN layer before Tor
4. **NoScript**: Install NoScript addon in Firefox (blocks malicious JS)
5. **Regular Updates**: Keep Kali Linux and tools updated

### Threat Model

DarkFox protects against:
- ✅ IP address exposure (via Tor)
- ✅ Command injection attacks (input sanitization)
- ✅ Process leakage (cleanup handlers)

DarkFox does NOT protect against:
- ❌ Browser fingerprinting
- ❌ Advanced traffic analysis
- ❌ Malicious .onion sites
- ❌ Social engineering

**Always practice operational security (OPSEC)!**

---

## 🐛 Troubleshooting

### Tor Connection Fails

```bash
# Check Tor service
sudo systemctl status tor

# Restart Tor
sudo systemctl restart tor

# Try different exit country
# Edit darkfox.sh: connect_tor_network "us"
```
### GoWitness Fails

```bash
# Check if running
ps aux | grep gowitness

# Manually download
cd /opt/darkfox/tools
wget https://github.com/sensepost/gowitness/releases/download/3.0.5/gowitness-3.0.5-linux-amd64 -O gowitness
chmod +x gowitness
```

### Permission Errors

```bash
# Fix ownership (replace 'kali' with your username)
sudo chown -R kali:kali /opt/darkfox/investigations

# Fix permissions
sudo chmod 755 /opt/darkfox
sudo chmod a+x /opt/darkfox/*.sh
```

### Firefox Won't Open .onion Sites

```bash
# Manually configure Firefox
# Open Firefox, go to about:config
# Search: network.dns.blockDotOnion
# Set to: false
```

---

## 📊 Sample Output

```
╔══════════════════════════════════════════════════════════════╗
║                        DarkFox v1.0                          ║
║            CTI Cyber Threat Intelligence Tool                ║
╚══════════════════════════════════════════════════════════════╝

[INFO] Today is 2025-01-15 14:23:45
[INFO] Current Network Information:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
│ Label          │ Value                │
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
│ Public IP      │ 13.88.214.23         │
│ Country        │ United States        │
│ State/Region   │ California           │
│ City           │ Los Angeles          │
│ Local IP       │ 192.168.2.23        │
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

What are you researching: ransomware

[INFO] Searching for .onion sites related to: marketplace
[✓] Found 47 unique .onion sites
[✓] Verification complete
[INFO] Capturing screenshots with GoWitness...
[✓] GoWitness server running at http://127.0.0.1:7171
[✓] Investigation setup complete!
```

---

## 🤝 Contributing

Contributions welcome! Please:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/improvement`)
3. Commit changes (`git commit -m 'Add new feature'`)
4. Push to branch (`git push origin feature/improvement`)
5. Open a Pull Request

**Areas for contribution:**
- Additional OSINT data sources
- Enhanced verification algorithms
- Report export formats (PDF, HTML, JSON)
- Internationalization (i18n)
- Additional Tor circuit management

---

## 📜 Legal & Ethics

### Authorized Use Only

DarkFox is intended for:
- ✅ Authorized security research
- ✅ Legitimate CTI/OSINT investigations
- ✅ Law enforcement with proper authorization
- ✅ Academic research
- ✅ Penetration testing (with written permission)

### Prohibited Activities

- ❌ Unauthorized access to computer systems
- ❌ Illegal marketplace transactions
- ❌ Distribution of illegal content
- ❌ Harassment or stalking
- ❌ Any activity violating local/international law

**You are solely responsible for your actions. The authors assume no liability for misuse.**

---

## 📚 Resources

### Learning Materials
- [OWASP Testing Guide](https://owasp.org/www-project-web-security-testing-guide/)
- [SANS CTI Reading Room](https://www.sans.org/white-papers/)
- [Tor Project Documentation](https://www.torproject.org/docs/)
- [OSINT Framework](https://osintframework.com/)

### Related Tools
- [Spiderfoot](https://github.com/smicallef/spiderfoot) - OSINT automation
- [Maltego](https://www.maltego.com/) - Link analysis
- [Shodan](https://www.shodan.io/) - Internet-wide scanning
- [OnionScan](https://github.com/s-rah/onionscan) - .onion site analysis

---

## 🙏 Credits

**Created by:** [Aryan Guenthner](https://github.com/aryanguenthner)
**Connect ***** [Aryan Guenthner](https://www.linkedin.com/in/aryancyber

**Built with:**
- [pyAhmia](https://github.com/escrapism/pyahmia) - Dark web search
- [GoWitness](https://github.com/sensepost/gowitness) - Screenshot capture
- [TorGhostNG](https://github.com/giterlizzi/torghostng) - Tor routing
- [Tor Project](https://www.torproject.org/) - Anonymity network
- [Ai](Aryan Intelligence) - My Own Brain, My Own idea, Gemini, ChatGPT, Claude, and more.


---

## 📄 License

This project is licensed under the **GNU General Public License v3.0** - see [LICENSE](LICENSE) file for details.

```
DarkFox - Dark Web CTI & OSINT Investigation Framework
Copyright (C) 2025 Aryan Guenthner

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.
```

---

## 🔄 Version History

### v1.0 (Current)
- ✨ Complete rewrite with modular architecture
- 🔒 Enhanced security (proper permissions, input sanitization)
- 📊 Improved investigation organization
- 🐛 Better error handling and logging
- 🎨 Enhanced user interface

### v1.0
- 🎉 Initial release as "DarkSheets"
- Basic .onion discovery and documentation

---

## 💬 Support

- **Issues**: [GitHub Issues](https://github.com/aryanguenthner/darkfox/issues)
- **Discussions**: [GitHub Discussions](https://github.com/aryanguenthner/darkfox/discussions)
- **Security**: Report vulnerabilities privately via GitHub Security Advisories

---

## ⭐ Show Your Support

If DarkFox helps your investigations, please:
- ⭐ Star this repository
- 🍴 Fork and contribute
- 📢 Share with the OSINT/CTI community
- 💬 Provide feedback

---

**Stay secure. Stay ethical.** 🦊
