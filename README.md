# 🛡️ Cybersecurity Toolkit

<p align="center">
  <img src="Spiderscorpion.png" alt="Cybersecurity Toolkit" width="500"/>
</p>

A comprehensive collection of cybersecurity tools for web scraping, metadata analysis, authentication, and anonymous hosting.

<div align="center">

![Python](https://img.shields.io/badge/Python-3.x-blue.svg)
![Docker](https://img.shields.io/badge/Docker-Ready-2496ED.svg)
![License](https://img.shields.io/badge/License-Educational-green.svg)
![Status](https://img.shields.io/badge/Status-Active-success.svg)

</div>

---

## 📋 Table of Contents

- [Overview](#overview)
- [Projects](#projects)
  - [Spider - Web Image Crawler](#-spider---web-image-crawler)
  - [Scorpion - Metadata Viewer](#-scorpion---metadata-viewer)
  - [OTP Generator](#-otp-generator)
  - [Tor Hidden Service](#-tor-hidden-service)
- [Quick Start](#quick-start)
- [Requirements](#requirements)
- [Security Notice](#security-notice)
- [License](#license)

---

## 🎯 Overview

This repository contains four distinct cybersecurity tools, each designed for specific security research and educational purposes:

1. **Spider** - Recursive web crawler for image collection
2. **Scorpion** - EXIF and metadata extraction tool
3. **OTP Generator** - RFC 4226 compliant HOTP implementation
4. **Tor Hidden Service** - Anonymous .onion hosting platform

---

## 📦 Projects

### 🕷️ Spider - Web Image Crawler

**Location:** `spider/`

A powerful recursive web crawler that downloads images from websites.

#### Features
- ✅ Recursive crawling with depth control
- ✅ Multiple image format support
- ✅ Efficient link parsing
- ✅ Error handling and retry logic

#### Quick Start
```bash
cd spider
python main.py -r -l 3 https://example.com
```

#### Usage

**Basic Usage (Single Page)**
```bash
python main.py <URL>
```

**Recursive Mode**
```bash
python main.py -r <URL>
```

**With Custom Depth**
```bash
python main.py -r -l <DEPTH> <URL>
```

#### Arguments

| Argument | Description | Default |
|----------|-------------|---------|
| `URL` | Target website URL to crawl | Required |
| `-r` | Enable recursive crawling | Disabled |
| `-l LEVEL` | Maximum recursion depth | 5 |

---

### 🦂 Scorpion - Metadata Viewer

**Location:** `scorpion/`

Extract and analyze comprehensive image metadata with CLI and GUI interfaces.

#### Features
- ✅ EXIF data extraction
- ✅ File property analysis
- ✅ Dual interface (CLI/GUI)
- ✅ Batch processing support

#### Quick Start
```bash
cd scorpion
python scorpion.py -gui
```

#### Usage

**CLI Mode - Single Image**
```bash
python scorpion.py image.jpg
```

**CLI Mode - Multiple Images**
```bash
python scorpion.py image1.jpg image2.png image3.gif
```

**GUI Mode**
```bash
python scorpion.py -gui
```

#### Extracted Information

| Category | Information |
|----------|-------------|
| **File Info** | Size (bytes), Creation date, Modification date |
| **Image Info** | Format (JPG/PNG/GIF/etc.), Color mode, Dimensions (width × height) |
| **EXIF Data** | Camera settings, GPS coordinates, Timestamps, Device info, and more |

---

### 🔐 OTP Generator

**Location:** `otp-generator/`

<p align="center">
  <img src="otp-generator/otp-banner.png" alt="OTP Generator" width="400"/>
</p>

Secure HOTP-based one-time password generator following RFC 4226.

#### Features
- ✅ RFC 4226 compliant
- ✅ Encrypted key storage
- ✅ Counter-based generation
- ✅ Cryptographic security (HMAC-SHA1)

#### Quick Start
```bash
cd otp-generator
echo "your64charhexkey" > key.hex
python ft_otp.py -g key.hex
python ft_otp.py -k  # Generate OTP
```

#### Commands

| Command | Description |
|---------|-------------|
| `-g <file>` / `--generate-key <file>` | Store a new encryption key from file |
| `-k` / `--get_otp` | Generate a new one-time password |

[📖 Full Documentation →](otp-generator/README.md)

---

### 🧅 Tor Hidden Service

**Location:** `tor-hidden-service/`

<p align="center">
  <img src="tor-hidden-service/tor-banner.png" alt="Tor Hidden Service" width="400"/>
</p>

Docker-based Tor hidden service with custom HTML hosting.

#### Features
- ✅ Automated .onion address generation
- ✅ NGINX web server
- ✅ SSH access for management
- ✅ Fully containerized

#### Quick Start
```bash
cd tor-hidden-service
docker build -t tor-service .
docker run -d -p 4242:4242 tor-service
docker exec tor-service cat /var/lib/tor/hidden_service/hostname
```

#### Exposed Ports

| Port | Service | Description |
|------|---------|-------------|
| 80 | HTTP (internal) | Web server, accessible via Tor |
| 4242 | SSH | Remote management access |

[📖 Full Documentation →](tor-hidden-service/README.md)

---

## 🚀 Quick Start

### Clone Repository

```bash
git clone git@github.com:Alikoaikk/Spider.git
cd Spider
```

### Install Dependencies

#### For Spider & Scorpion
```bash
pip install requests beautifulsoup4 Pillow
```

#### For OTP Generator
```bash
pip install cryptography
```

#### For Tor Hidden Service
```bash
# Requires Docker
docker --version
```

---

## 📋 Requirements

### System Requirements
- **OS**: Linux, macOS, or Windows
- **Python**: 3.8 or higher
- **Docker**: Latest stable version (for Tor service)

### Python Dependencies

| Tool | Dependencies |
|------|-------------|
| Spider | `requests`, `beautifulsoup4` |
| Scorpion | `Pillow`, `tkinter` |
| OTP Generator | `cryptography` |
| Tor Service | Docker only |

---

## 🔒 Security Notice

### ⚠️ Important Warnings

- **Educational Use Only**: These tools are for learning and authorized testing
- **Legal Compliance**: Ensure compliance with local laws and regulations
- **Authorized Access**: Only use on systems you own or have permission to test
- **Responsible Usage**: Do not use for malicious purposes

### Best Practices

✅ **DO:**
- Use in controlled environments
- Obtain proper authorization
- Follow responsible disclosure
- Keep software updated
- Use strong passwords and encryption

❌ **DON'T:**
- Use on unauthorized systems
- Share sensitive credentials
- Host illegal content
- Violate terms of service
- Ignore privacy laws

---

## 📊 Project Structure

```
Spider/
├── spider/               # Web crawler
│   ├── main.py
│   ├── spider.py
│   ├── spider_cloud.py
│   └── parse.py
├── scorpion/             # Metadata viewer
│   ├── scorpion.py
│   └── gui.py
├── otp-generator/        # HOTP implementation
│   ├── ft_otp.py
│   ├── htop.py
│   ├── encryption.py
│   ├── key_manager.py
│   └── README.md
├── tor-hidden-service/   # .onion hosting
│   ├── Dockerfile
│   ├── nginx.conf
│   ├── torrc
│   ├── sshd_config
│   ├── index.html
│   └── README.md
├── Spiderscorpion.png
└── README.md             # This file
```

---

## 🤝 Contributing

This is an educational project. If you find issues or have improvements:

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

---

## 📖 Resources

### General Security
- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [Cybersecurity Best Practices](https://www.cisa.gov/cybersecurity-best-practices)

### Tool-Specific
- [RFC 4226 - HOTP](https://tools.ietf.org/html/rfc4226)
- [Tor Project](https://www.torproject.org/)
- [BeautifulSoup Documentation](https://www.crummy.com/software/BeautifulSoup/bs4/doc/)

---

## 📄 License

This project is for **educational purposes only**.

**Disclaimer**: The authors are not responsible for any misuse of these tools. Always ensure you have proper authorization before using any security tools.

---

## 🏗️ Development Status

| Project | Status | Version |
|---------|--------|---------|
| Spider | ✅ Stable | 1.0 |
| Scorpion | ✅ Stable | 1.0 |
| OTP Generator | ✅ Stable | 1.0 |
| Tor Hidden Service | ✅ Stable | 1.0 |

---

<div align="center">

### 🛡️ Built for Education • Used Responsibly

**⭐ If you found this helpful, consider starring the repository!**

</div>
