# Spider & Scorpion - Web Crawler & Metadata Analysis Suite

![Spider & Scorpion](Spiderscorpion.png)

A comprehensive toolkit combining powerful web scraping and image metadata analysis capabilities.

---

## 📋 Table of Contents

- [Overview](#overview)
- [Spider - Web Image Crawler](#-spider---web-image-crawler)
- [Scorpion - Metadata Viewer](#-scorpion---metadata-viewer)
- [Installation](#installation)
- [Quick Start](#quick-start)
- [Security & Privacy](#security--privacy)

---

## 🎯 Overview

This suite contains two complementary tools for web reconnaissance and digital forensics:

1. **🕷️ Spider** - Recursively crawls websites and downloads images
2. **🦂 Scorpion** - Extracts and analyzes comprehensive image metadata

Perfect for OSINT (Open Source Intelligence), digital forensics, and security research.

---

## 🕷️ Spider - Web Image Crawler

### Description

Spider is a powerful Python-based web crawler that recursively downloads images from websites. It can operate in single-page or recursive mode, crawling through links to discover and download all images.

### Features

- 🔄 **Recursive Crawling** - Navigate through website links with configurable depth
- 📥 **Automatic Downloads** - Save all discovered images locally
- 🌐 **Multiple Formats** - Supports JPG, PNG, GIF, BMP, and more
- 🔗 **Smart Link Following** - Stays within the same domain
- ⚡ **Error Handling** - Robust request management and retry logic
- 📊 **Progress Tracking** - Monitor crawling progress in real-time

### Usage

#### Basic Usage (Single Page)

```bash
cd spider
python main.py <URL>
```

#### Recursive Mode

```bash
python main.py -r <URL>
```

#### With Custom Depth

```bash
python main.py -r -l <DEPTH> <URL>
```

### Arguments

| Argument | Description | Default |
|----------|-------------|---------|
| `URL` | Target website URL to crawl | Required |
| `-r` | Enable recursive crawling | Disabled |
| `-l LEVEL` | Maximum recursion depth | 5 |

### Output

Downloaded images are saved to the `./data/` directory by default.

### Example

```bash
# Download all images from a single page
python main.py https://example.com

# Recursively crawl website with depth of 3
python main.py -r -l 3 https://example.com
```

### Project Structure

```
spider/
├── main.py           # Entry point
├── spider.py         # Core spider logic
├── spider_cloud.py   # Cloud spider implementation
└── parse.py          # Argument parser
```

---

## 🦂 Scorpion - Metadata Viewer

### Description

Scorpion is a specialized metadata extraction tool that analyzes image files and displays detailed information including file properties, image specifications, and EXIF data. Features both CLI and GUI interfaces.

### Features

- 📊 **Complete Metadata Extraction** - File info, image properties, EXIF data
- 🖥️ **Dual Interface** - Command-line and graphical user interface
- 🎨 **Image Analysis** - Format, dimensions, color mode details
- 📁 **File Properties** - Size, creation date, modification date
- 🔍 **Batch Processing** - Analyze multiple images at once
- ✅ **Format Validation** - Automatic file type checking
- 📸 **EXIF Parsing** - Camera settings, GPS, timestamps, device info

### Usage

#### CLI Mode - Single Image

```bash
cd scorpion
python scorpion.py image.jpg
```

#### CLI Mode - Multiple Images

```bash
python scorpion.py image1.jpg image2.png image3.gif
```

#### GUI Mode

```bash
python scorpion.py -gui
```

The GUI provides:
- Visual file browser
- Formatted metadata display
- Easy navigation between multiple images

### Extracted Information

| Category | Information |
|----------|-------------|
| **File Info** | Size (bytes), Creation date, Modification date |
| **Image Info** | Format (JPG/PNG/GIF/etc.), Color mode, Dimensions (width × height) |
| **EXIF Data** | Camera settings, GPS coordinates, Timestamps, Device info, and more |

### Supported Formats

- ✅ JPEG / JPG
- ✅ PNG
- ✅ GIF
- ✅ BMP
- ✅ Other Pillow-supported formats

### Example Output

```
=== example.jpg ===
Size: 2,456,789 bytes
Created: 2024-11-19 10:30:45
Modified: 2024-11-19 10:35:12
Format: JPEG
Size: 1920 x 1080 pixels

EXIF Data:
  271: Apple
  272: iPhone 15 Pro
  306: 2024:11:19 10:30:45
  ...
```

### Project Structure

```
scorpion/
├── scorpion.py       # Main CLI entry point
└── gui.py            # GUI implementation
```

---

## 🚀 Installation

### Prerequisites

- Python 3.x
- pip (Python package installer)

### Install Dependencies

```bash
pip install requests beautifulsoup4 Pillow
```

> **Note**: `tkinter` for GUI mode usually comes pre-installed with Python. If not available, install it via your system package manager:
> - **Ubuntu/Debian**: `sudo apt-get install python3-tk`
> - **macOS**: Included with Python
> - **Windows**: Included with Python

---

## 💻 Quick Start

### Workflow Example

```bash
# Step 1: Crawl a website and download images
cd spider
python main.py -r -l 2 https://example.com

# Step 2: Analyze downloaded images
cd ../scorpion
python scorpion.py -gui

# Or analyze specific images from CLI
python scorpion.py ../spider/data/*.jpg
```

---

## 🔍 Use Cases

### Spider
- 🔐 Security reconnaissance
- 📦 Website backup and archival
- 🎨 Asset collection for research
- 📊 Content analysis and monitoring

### Scorpion
- 🔐 Digital forensics investigation
- 📸 Photography metadata analysis
- 🗺️ GPS location extraction
- 📝 Image cataloging and documentation
- 🔍 Verifying image authenticity and origin

---

## 🔒 Security & Privacy

### Important Notes

#### Spider Considerations
- ⚠️ **Respect robots.txt** - Always check website crawling policies
- ⚠️ **Terms of Service** - Ensure you have permission to scrape content
- ⚠️ **Rate Limiting** - Avoid overwhelming target servers
- ⚠️ **Legal Compliance** - Use only on authorized websites

#### Scorpion Privacy Warning

EXIF data may contain **sensitive information**:
- 📍 GPS coordinates (exact location where photo was taken)
- 📱 Camera/device serial numbers
- ⏰ Precise timestamps
- 👤 Device owner information

**Always handle metadata responsibly and respect privacy laws.**

### Best Practices

✅ **DO:**
- Obtain permission before crawling websites
- Use in controlled, authorized environments
- Respect privacy when analyzing images
- Follow responsible disclosure practices
- Keep software updated

❌ **DON'T:**
- Crawl websites without permission
- Share sensitive EXIF data without consent
- Use for malicious purposes
- Violate terms of service
- Ignore legal restrictions

---

## 🐛 Error Handling

### Spider
- Connection timeouts and retries
- Invalid URL detection
- HTTP error handling
- File system error management

### Scorpion
- Invalid file path detection
- Unsupported format validation
- Corrupted image handling
- Missing EXIF data gracefully handled
- Permission error management

---

## 📖 Additional Resources

- [BeautifulSoup Documentation](https://www.crummy.com/software/BeautifulSoup/bs4/doc/)
- [Pillow Documentation](https://pillow.readthedocs.io/)
- [EXIF Standard](https://www.exif.org/)
- [OSINT Framework](https://osintframework.com/)

---

## 📄 License

This project is part of a cybersecurity toolkit for educational purposes.

---

<div align="center">

**⚡ Crawl Smartly • Analyze Deeply • Stay Ethical**

</div>
