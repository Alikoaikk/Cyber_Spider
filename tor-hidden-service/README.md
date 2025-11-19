# 🧅 Tor Hidden Service - Dockerized .onion Server

![Tor Hidden Service](Gemini_Generated_Image_c0c49lc0c49lc0c4.png)

A Docker-based Tor hidden service that hosts a custom HTML page accessible through the Tor network via a `.onion` address.

## 📋 Description

This project sets up a complete Tor hidden service infrastructure using Docker. It runs an NGINX web server behind Tor, making your website accessible only through the Tor network with an automatically generated `.onion` address. The setup includes SSH access for management and monitoring.

## ✨ Features

- 🧅 **Tor Hidden Service**: Automatic .onion address generation
- 🌐 **NGINX Web Server**: Fast and reliable HTTP serving
- 🐳 **Dockerized**: Easy deployment and portability
- 🔐 **SSH Access**: Secure remote management on port 4242
- 📝 **Custom HTML**: Fully customizable web content
- 🔒 **Anonymous Hosting**: Your service hidden in the Tor network

## 🚀 Installation & Setup

### Prerequisites

- Docker installed on your system
- Docker Compose (optional but recommended)
- Basic knowledge of Tor network

### Quick Start

1. **Build the Docker image:**

```bash
docker build -t tor-hidden-service .
```

2. **Run the container:**

```bash
docker run -d -p 4242:4242 --name my-hidden-service tor-hidden-service
```

3. **Get your .onion address:**

```bash
docker exec my-hidden-service cat /var/lib/tor/hidden_service/hostname
```

4. **Access via Tor Browser:**
   - Open Tor Browser
   - Navigate to your `.onion` address

## 🛠️ Configuration Files

### Project Structure

```
tor-hidden-service/
├── Dockerfile        # Container configuration
├── nginx.conf        # NGINX web server config
├── torrc            # Tor daemon configuration
├── sshd_config      # SSH server configuration
├── index.html       # Your website content
└── README.md        # This file
```

### Key Configuration

#### Tor Configuration (`torrc`)
- Hidden service directory: `/var/lib/tor/hidden_service`
- Service port: 80 (internal)
- Auto-generates .onion address on first run

#### NGINX Configuration
- Listens on port 80
- Serves content from `/var/www/html`
- Optimized for hidden service performance

#### SSH Access
- Port: 4242
- Default credentials: `root:cyber.onion123`
- **⚠️ Change default password immediately!**

## 🔧 Usage

### Access Your Hidden Service

```bash
# Get .onion address
docker exec my-hidden-service cat /var/lib/tor/hidden_service/hostname

# View Tor logs
docker exec my-hidden-service tail -f /var/log/tor/notices.log

# View NGINX logs
docker exec my-hidden-service tail -f /var/log/nginx/access.log
```

### SSH into Container

```bash
ssh root@localhost -p 4242
# Password: cyber.onion123
```

### Update Website Content

```bash
# Copy new HTML file
docker cp new-index.html my-hidden-service:/var/www/html/index.html

# Restart NGINX
docker exec my-hidden-service nginx -s reload
```

### Stop and Remove

```bash
docker stop my-hidden-service
docker rm my-hidden-service
```

## 📊 Architecture

```
┌─────────────────────────────────────────┐
│         Docker Container                │
│                                         │
│  ┌─────────────────────────────────┐   │
│  │      Tor Hidden Service         │   │
│  │  (Generates .onion address)     │   │
│  └──────────────┬──────────────────┘   │
│                 │                       │
│                 ▼                       │
│  ┌─────────────────────────────────┐   │
│  │      NGINX Web Server           │   │
│  │    Serves: /var/www/html        │   │
│  └─────────────────────────────────┘   │
│                                         │
│  ┌─────────────────────────────────┐   │
│  │      SSH Server (Port 4242)     │   │
│  └─────────────────────────────────┘   │
└─────────────────────────────────────────┘
              │
              ▼
        Tor Network (.onion)
```

## 🔐 Security Considerations

### ⚠️ Important Security Notes

1. **Change Default Password**
   ```bash
   docker exec -it my-hidden-service passwd root
   ```

2. **Backup Your Keys**
   - The .onion address is tied to cryptographic keys
   - Backup `/var/lib/tor/hidden_service/` directory
   ```bash
   docker cp my-hidden-service:/var/lib/tor/hidden_service ./backup/
   ```

3. **Monitor Logs**
   - Regularly check Tor and NGINX logs
   - Watch for unusual access patterns

4. **Update Regularly**
   - Keep base image updated
   - Monitor for security advisories

### Best Practices

- ✅ Use strong, unique passwords
- ✅ Enable firewall rules
- ✅ Limit SSH access
- ✅ Monitor resource usage
- ✅ Regular backups of hidden service keys
- ❌ Don't expose real identity in content
- ❌ Don't use for illegal activities
- ❌ Don't reuse .onion addresses across different purposes

## 🌐 Exposed Ports

| Port | Service | Description |
|------|---------|-------------|
| 80 | HTTP (internal) | Web server, accessible via Tor |
| 4242 | SSH | Remote management access |

## 📝 Customization

### Change Web Content

Edit `index.html` to customize your hidden service's webpage.

### Modify Tor Configuration

Edit `torrc` to change:
- Hidden service ports
- Directory locations
- Additional security settings

### NGINX Tuning

Modify `nginx.conf` for:
- Custom server blocks
- Performance optimization
- Security headers

## 🐛 Troubleshooting

### Service Not Starting

```bash
# Check Tor status
docker exec my-hidden-service service tor status

# Check NGINX status
docker exec my-hidden-service nginx -t
```

### Can't Access .onion Address

- Verify Tor service is running
- Check that hostname file exists
- Ensure Tor Browser is updated
- Wait 1-2 minutes for propagation

### Permission Issues

```bash
# Fix Tor directory permissions
docker exec my-hidden-service chown -R debian-tor:debian-tor /var/lib/tor
docker exec my-hidden-service chmod 700 /var/lib/tor/hidden_service
```

## 📖 Resources

- [Tor Project Documentation](https://www.torproject.org/docs/)
- [NGINX Documentation](https://nginx.org/en/docs/)
- [Hidden Service Best Practices](https://community.torproject.org/onion-services/)

## ⚖️ Legal Disclaimer

This tool is for **educational and legitimate purposes only**. Running a Tor hidden service is legal, but:

- Ensure compliance with local laws
- Do not host illegal content
- Respect terms of service
- Understand your legal responsibilities

The developers are not responsible for misuse of this software.

## 📄 License

This project is part of a cybersecurity toolkit for educational purposes.

---

**🧅 Stay anonymous, stay secure!**
