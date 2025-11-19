# 🔐 OTP Generator - HOTP Implementation

![OTP Generator](otp-banner.png)

A secure One-Time Password (OTP) generator based on the HMAC-based One-Time Password (HOTP) algorithm following RFC 4226 specifications.

## 📋 Description

This OTP generator implements the HOTP algorithm with secure key management and encryption. It generates time-based one-time passwords that change every 30 seconds, providing an additional layer of security for authentication systems.

## ✨ Features

- 🔒 RFC 4226 compliant HOTP implementation
- 🔑 Secure key storage with encryption
- ⏱️ Counter-based OTP generation
- 🛡️ Hexadecimal key validation (64 characters)
- 💾 Persistent key and counter management
- 🔐 Cryptographic security using HMAC-SHA1

## 🚀 Installation

### Prerequisites

- Python 3.x
- pip (Python package installer)

### Required Dependencies

```bash
pip install cryptography
```

## 💻 Usage

### Generate and Store Key

First, create a file containing your 64-character hexadecimal key:

```bash
echo "your64characterhexadecimalkeyhere..." > key.hex
```

Then store it securely:

```bash
python ft_otp.py -g key.hex
```

### Generate OTP

Once the key is stored, generate a new OTP:

```bash
python ft_otp.py -k
```

The command outputs a 6-digit OTP code that increments with each generation.

## 📝 Commands

| Command | Description |
|---------|-------------|
| `-g <file>` / `--generate-key <file>` | Store a new encryption key from file |
| `-k` / `--get_otp` | Generate a new one-time password |

## 🔐 Security Features

### Key Requirements
- Must be exactly 64 hexadecimal characters
- Validated before storage
- Encrypted using strong cryptographic methods

### Counter Management
- Increments with each OTP generation
- Prevents OTP reuse
- Synchronized with authentication server

### Encryption
- Keys stored in encrypted format
- Uses industry-standard encryption algorithms
- Secure key derivation functions

## 🛠️ Project Structure

```
otp-generator/
├── ft_otp.py         # Main entry point
├── htop.py           # HOTP algorithm implementation
├── encryption.py     # Encryption utilities
├── key_manager.py    # Key storage and retrieval
└── README.md         # This file
```

## 🔍 How HOTP Works

1. **Key Generation**: A secret key is generated and stored securely
2. **Counter**: A counter value that increments with each OTP request
3. **HMAC**: Computes HMAC-SHA1(Key, Counter)
4. **Truncation**: Extracts dynamic 6-digit code from HMAC result
5. **Output**: Returns time-limited OTP code

```
┌─────────────┐
│ Secret Key  │
└──────┬──────┘
       │
       ├─────► HMAC-SHA1 ──► Truncate ──► 6-Digit OTP
       │
┌──────┴──────┐
│   Counter   │
└─────────────┘
```

## 📊 Example Workflow

```bash
# Step 1: Create a key file
echo "3132333435363738393031323334353637383930313233343536373839303132" > secret.hex

# Step 2: Store the key
python ft_otp.py -g secret.hex
# Output: Key was successfully saved.

# Step 3: Generate OTP codes
python ft_otp.py -k
# Output: 123456

python ft_otp.py -k
# Output: 789012

python ft_otp.py -k
# Output: 345678
```

## ⚠️ Security Warnings

- 🔒 **Never share your secret key**
- 💾 **Backup encrypted key file securely**
- 🚫 **Do not commit keys to version control**
- ⏱️ **Synchronize counter with authentication server**
- 🔐 **Store keys in secure, encrypted storage**

## 📖 RFC 4226 Compliance

This implementation follows the HOTP specification defined in [RFC 4226](https://tools.ietf.org/html/rfc4226):
- HMAC-SHA1 based algorithm
- 6-digit OTP codes
- Counter-based synchronization
- Dynamic truncation method

## 🎯 Use Cases

- 🔐 Two-factor authentication (2FA)
- 🏦 Banking and financial applications
- 🔑 Secure access control systems
- 🛡️ Multi-factor authentication (MFA)
- 💼 Enterprise security solutions

## 🐛 Error Handling

The system handles:
- Invalid key format errors
- File not found errors
- Encryption/decryption failures
- Counter synchronization issues
- Key length validation

## 📄 License

This project is part of a cybersecurity toolkit for educational purposes.

---

**🔐 Secure your access with OTP!**
