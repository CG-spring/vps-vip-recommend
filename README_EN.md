# VPS Curated Recommendation Guide

> 🌐 中文版本：[README.md](./README.md)
>
> 🔖 Current version: **v2.0.0**
>
> ⚠️ **Disclaimer**: This guide is for reference only and does not constitute any purchase advice.

---

## Table of Contents

- [1. Introduction: Why Do You Need a VPS?](#1-introduction-why-do-you-need-a-vps)
- [2. VPS vs Traditional Shared Hosting vs Cloud Server](#2-vps-vs-traditional-shared-hosting-vs-cloud-server)
- [3. Core Metrics for Choosing a VPS](#3-core-metrics-for-choosing-a-vps)
  - [3.1 CPU Performance](#31-cpu-performance)
  - [3.2 Memory & Storage](#32-memory--storage)
  - [3.3 Bandwidth & Traffic](#33-bandwidth--traffic)
  - [3.4 Data Center Location & Network Quality](#34-data-center-location--network-quality)
  - [3.5 Payment Methods & Privacy Protection](#35-payment-methods--privacy-protection)
- [4. Popular VPS Recommendations](#4-popular-vps-recommendations)
  - [Budget Tier ($2–5/month)](#budget-tier-2-5month)
  - [Mid-Range Tier ($5–15/month)](#mid-range-tier-5-15month)
  - [Professional Tier ($15+/month)](#professional-tier-15month)
- [5. VPS Purchase Pitfall Guide](#5-vps-purchase-pitfall-guide)
  - [Common Scams & Tricks](#common-scams--tricks)
  - [How to Test VPS Performance](#how-to-test-vps-performance)
  - [Refund Policy Notes](#refund-policy-notes)
- [6. VPS Basic Setup Tutorial](#6-vps-basic-setup-tutorial)
  - [Choosing an OS](#choosing-an-os)
  - [SSH Key Configuration](#ssh-key-configuration)
  - [Basic Security Hardening](#basic-security-hardening)
- [7. Advanced Use Cases](#7-advanced-use-cases)
  - [Proxy & VPN Tools (Clash/V2Ray/WireGuard)](#proxy--vpn-tools-clashv2raywireguard)
  - [Website Hosting](#website-hosting)
  - [Private Cloud Storage](#private-cloud-storage)
  - [Dev/Test Environment](#devtest-environment)
- [8. Recommended Configuration Combos](#8-recommended-configuration-combos)
- [9. Disclaimer](#9-disclaimer)
- [10. License](#10-license)

---

## 1. Introduction: Why Do You Need a VPS?

In this digital age, personal websites, blogs, developer portfolios, and independent online presences have become increasingly common. The Virtual Private Server (VPS) has emerged as an indispensable piece of internet infrastructure. But when exactly do you need a VPS?

**The core value of a VPS lies in "independence" and "control."** Unlike shared hosting, a VPS allocates you dedicated computing resources — dedicated CPU cores, dedicated RAM, dedicated disk space, and a dedicated OS environment. You get root/admin access, free to install any software and configure any service without interference from others.

Typical scenarios where a VPS makes sense:

- **Host a personal website or blog**: Use WordPress, Hugo, Hexo, or other frameworks to build an independent blog with full control over content and data
- **Learn Linux system administration**: Practice server operations in a real production-grade environment
- **Deploy APIs and backend services**: Run Web services built with Node.js, Python, Go, Rust, and other languages
- **Networking & connectivity tools**: Deploy proxy tools to access the open internet (must comply with local laws and regulations)
- **Development and testing environments**: Isolated dev/test environments that don't affect your local machine
- **Private cloud storage**: Build self-hosted solutions like Nextcloud, Seafile, or Alist
- **Scientific computing & data processing**: Leverage server CPU/GPU resources for data analysis and ML training
- **Game servers**: Host Minecraft, Valheim, and other game servers for multiplayer sessions with friends

Whether you're a student, developer, entrepreneur, or tech enthusiast, a VPS is a skill worth mastering.

---

## 2. VPS vs Traditional Shared Hosting vs Cloud Server

Before purchasing a server, understand the differences between the three main hosting types to choose the one that fits your needs.

| Comparison | Shared Hosting | VPS | Cloud Server |
|-----------|---------------|-----|--------------|
| **Resource isolation** | Shared, affected by "noisy neighbors" | Dedicated resources, guaranteed performance | Elastic, pooled resources |
| **Root access** | ❌ None | ✅ Full control | ✅ Full control |
| **Customization** | Control panel only | Fully customizable | Fully customizable |
| **Price range** | $1–10/month | $2–100+/month | $5–500+/month |
| **Scalability** | Limited by single server | Upgrade plan or migrate | Elastic scaling on demand |
| **Management difficulty** | Easy (cPanel/Plesk) | Medium (Linux basics required) | Medium-high (some experience needed) |
| **Best for** | Complete beginners, no tech background | Users with some technical foundation | Enterprise / high-traffic scenarios |
| **Network quality** | Generally shared bandwidth | Dedicated or quality-shared bandwidth | Optional premium BGP routes |

**Verdict**:
- Complete beginners, no technical background → Shared hosting with a control panel (e.g., Bluehost, HostGator)
- Some Linux experience, need more control → VPS (best value for money)
- Enterprise-grade, high availability, elastic scaling → Cloud server (AWS/GCP/Alibaba Cloud/etc.)

---

## 3. Core Metrics for Choosing a VPS

When selecting a VPS, these core metrics directly determine your actual server experience. Review them carefully before purchasing to avoid pitfalls.

### 3.1 CPU Performance

The CPU is the server's brain, determining the upper limit of computational power. Key points to note:

- **Core count vs. single-core performance**: More cores isn't always better. For web serving, single-core performance is often more critical. For parallel computing tasks (video transcoding, data processing), multi-core matters more.
- **Is the CPU model disclosed?**: Quality providers explicitly state the CPU model (e.g., AMD EPYC 7543, Intel Xeon Gold). If they only say "high-performance CPU," resources are likely shared or oversold.
- **AES-NI / instruction set support**: If you plan to run specific applications (e.g., WireGuard requires AES-NI), confirm the CPU supports the required instruction sets.
- **Credit/performance mode**: Some providers (like BandwagonHost) use a credit system — accumulate credits under low load, consume them under high load. This is a reasonable mechanism, but understand its rules.

**Recommended focus**: AMD EPYC series, Intel Xeon Scalable series — typically more stable and predictable performance.

### 3.2 Memory & Storage

- **RAM**: At least 1GB to smoothly run a basic Linux environment (with a small web service). 2GB is the comfort zone; 4GB+ handles more complex workloads.
- **Storage type**:
  - **NVMe SSD**: Read/write speeds of 3,000–7,000 MB/s, the current best choice
  - **SATA SSD**: Read/write speeds ~500 MB/s, the value champion
  - **HDD**: Slow, not recommended for VPS unless large-capacity storage is the sole priority
- **Storage capacity**: Choose based on actual needs. 20–40GB is sufficient for basic blogging/proxy use; larger data needs more space.

### 3.3 Bandwidth & Traffic

- **Bandwidth**: The server port rate, commonly 1 Gbps or 10 Gbps. Note: dedicated bandwidth > shared bandwidth.
- **Monthly traffic**: The monthly data transfer allowance. Some providers advertise "unlimited traffic" but actually throttle to very low speeds after a threshold (e.g.,降至 128Kbps). Always read the TOS (Terms of Service) carefully.
- **Overage policy**: Understand what happens when traffic is exhausted (throttle/disable/extra charges), and choose the policy most favorable to you.

**Red flag warning**: Providers advertising "unlimited traffic" but actually throttling to 128Kbps are not uncommon. Verify before purchasing.

### 3.4 Data Center Location & Network Quality

Data center location directly affects latency and stability. Choose different locations based on your use case:

| Use Case | Recommended Data Centers | Typical Latency (from China) |
|---------|-------------------------|------------------------------|
| Websites targeting Chinese users | Hong Kong, Singapore, Japan | 30–80ms |
| Websites targeting overseas users | Los Angeles, Seattle, USA | 150–200ms |
| Proxy nodes / connectivity tools | Hong Kong, Japan, US West Coast | 40–180ms |
| European user services | Amsterdam, Frankfurt, London | 200ms+ |
| Game servers | Choose near your target player base | Varies |

**Network route priority**:
1. Optimized CN2 GIA routes (best for China access)
2. Optimized CN2 routes
3. Premium BGP mixed routes
4. Regular international routes

**Testing advice**: Use Looking Glass or trial opportunities to test actual network quality before committing. Don't rely solely on provider marketing.

### 3.5 Payment Methods & Privacy Protection

- **Payment methods**: Credit card, PayPal, cryptocurrency (BTC, USDT, etc.). Users with high anonymity needs should choose providers accepting crypto.
- **Privacy policy**: Some providers (e.g., Proton VPN's hosting service) offer a no-log policy, respecting user privacy.
- **Refund policy**: Most providers offer a 7–30 day money-back guarantee. Confirm the refund terms (whether a reason is required, whether domain fees are deducted, etc.).
- **Alipay / WeChat Pay**: China-friendly providers typically support Alipay, lowering the barrier to purchase.

---

## 4. Popular VPS Recommendations

The following recommendations are based on market reputation, value for money, and network quality. Each tier includes a detailed parameter comparison to help you decide quickly.

> 📝 **Note**: Prices and configurations may change at any time. Check each provider's official website for the latest information.

### Budget Tier ($2–5/month)

Best for: lightweight websites, Linux learning, basic proxy needs

| Provider | CPU | RAM | Storage | Bandwidth | Monthly Traffic | Price | Locations | Rating |
|----------|-----|-----|---------|-----------|----------------|-------|-----------|--------|
| RackNerd | 1 vCPU | 1 GB | 18 GB NVMe | 1 Gbps | 2 TB | $2.99/mo | US (multi) | ⭐⭐⭐⭐ |
| GreenGeeks | 1 vCPU | 1 GB | 50 GB SSD | Unlimited | Unlimited | $2.95/mo | US/EU/Asia | ⭐⭐⭐⭐ |
| Hostinger | 1 vCPU | 0.5 GB | 10 GB SSD | 100 Mbps | 1 TB | $2.69/mo | US/EU/Asia | ⭐⭐⭐ |
| Contabo | 1 vCPU | 2 GB | 20 GB SSD | 1 Gbps | Unlimited | €3.99/mo | DE/US/SG | ⭐⭐⭐⭐ |

### Mid-Range Tier ($5–15/month)

Best for: indie developers, small websites, moderate-traffic services

| Provider | CPU | RAM | Storage | Bandwidth | Monthly Traffic | Price | Locations | Rating |
|----------|-----|-----|---------|-----------|----------------|-------|-----------|--------|
| BandwagonHost | 1–2 vCPU | 1–2 GB | 20–40 GB SSD | 1–2.5 Gbps | 1–2 TB | $5.99/mo+ | HK/CN2 GIA | ⭐⭐⭐⭐⭐ |
| RackNerd (high-spec) | 2 vCPU | 3 GB | 45 GB NVMe | 1 Gbps | 3 TB | $10.99/mo | US (multi) | ⭐⭐⭐⭐ |
| Vultr | 2 vCPU | 2 GB | 55 GB SSD | 1 Gbps | 2 TB | $6/mo | 25+ global | ⭐⭐⭐⭐ |
| Tencent Cloud LH | 2 vCPU | 4 GB | 80 GB SSD | 30 Mbps | 1200 GB | ¥30/mo | China | ⭐⭐⭐⭐ |
| Alibaba Cloud LH | 1 vCPU | 2 GB | 50 GB SSD | 30 Mbps | 2 TB | ¥24/mo | China | ⭐⭐⭐⭐ |

### Professional Tier ($15+/month)

Best for: high-traffic websites, dev/test environments, commercial applications

| Provider | CPU | RAM | Storage | Bandwidth | Monthly Traffic | Price | Locations | Rating |
|----------|-----|-----|---------|-----------|----------------|-------|-----------|--------|
| BandwagonHost (CN2 GIA Pro) | 2–4 vCPU | 2–4 GB | 40–80 GB SSD | 1–10 Gbps | 1–2 TB | $19.99/mo+ | HK/CN2 GIA | ⭐⭐⭐⭐⭐ |
| Vultr (high-spec) | 4 vCPU | 8 GB | 160 GB NVMe | 1 Gbps | 3 TB | $40/mo | 25+ global | ⭐⭐⭐⭐ |
| Tencent Cloud Standard | 2 vCPU | 4 GB | Performance cloud disk | Elastic | Pay-as-you-go | ¥0.2/hr+ | China | ⭐⭐⭐⭐⭐ |
| DigitalOcean | 4 vCPU | 8 GB | 160 GB SSD | 1 Gbps | 5 TB | $48/mo | 10 global | ⭐⭐⭐⭐ |
| AWS Lightsail | 2 vCPU | 4 GB | 80 GB SSD | Elastic | 3 TB | $20/mo | Global | ⭐⭐⭐⭐ |

> ⚠️ **Price disclaimer**: Prices above are reference values. Actual prices may vary due to promotions, configuration upgrades, and currency exchange rates.

---

## 5. VPS Purchase Pitfall Guide

### Common Scams & Tricks

The VPS market has no shortage of tricks and traps. Here is accumulated wisdom to help you avoid them:

**Trick 1: Fake Unlimited Traffic**
Some providers advertise "unlimited traffic" but actually include throttling clauses in their TOS — after exceeding a threshold (e.g., 10TB), speeds drop to extremely low rates (128Kbps–1Mbps) or the connection is cut. Truly unlimited providers are extremely rare.

**Trick 2: Severe Overselling**
Some low-cost VPS providers oversell resources on the same physical server to maximize profit, causing all VPS instances to degrade. Symptom: excellent benchmark scores during testing, but severe lag in actual use. How to identify: check long-term user reviews, especially from users who have been with the provider for a year or more.

**Trick 3: Opaque CPU Models**
If a provider doesn't disclose the specific CPU model and only says "high-performance vCPU," they're likely running on shared or low-quality resources. Quality providers typically explicitly state models like AMD EPYC or Intel Xeon.

**Trick 4: Bait-and-Switch Pricing**
Some providers use extremely low prices to attract users (e.g., $1/month), but renewal prices are 3–5× the initial rate ($5/month becomes $25/month on renewal). Always check the renewal price before purchasing.

**Trick 5: Misleading Data Center Location**
Some providers label a location as "Asia-optimized" but the actual data center is in the Americas, only with some optimized routing. Always verify the real geographic location of the data center.

**Trick 6: Refund Traps**
Although some providers promise "30-day refunds," the actual process has many obstacles: requiring device serial number screenshots, deducting domain fees or add-on service fees, lengthy approval processes (30+ days), etc. Choose providers with transparent, straightforward refund policies.

### How to Test VPS Performance

After purchasing a VPS, run these comprehensive tests:

**1. Basic Configuration Check**
```bash
# View system info
cat /etc/os-release
uname -a

# View CPU model and core count
cat /proc/cpuinfo | grep "model name" | head -1
nproc

# View memory
free -h

# View disk space
df -h
```

**2. Disk I/O Performance Test**
```bash
# Sequential write test with dd (not professional, but a quick reference)
dd if=/dev/zero of=testfile bs=1M count=1024 oflag=direct

# More professional test with fio (needs installation)
sudo apt update && sudo apt install fio -y
fio --name=randread --ioengine=libaio --rw=randread --bs=4k --numjobs=4 --size=1G --runtime=60
```

**3. Network Speed Test**
```bash
# Comprehensive test including China nodes via Bench.sh
wget -qO- bench.sh | bash

# Test latency and speed to specific nodes
curl -s https://raw.githubusercontent.com/ernisn/supervps/main/tools/tes

# iperf3 test (requires two machines)
# Server side
iperf3 -s
# Client side
iperf3 -c server_ip -p 5201
```

**4. CPU Performance Test**
```bash
# CPU stress test with sysbench
sudo apt install sysbench -y
sysbench cpu --cpu-max-prime=20000 run
```

**5. Route Tracing (China Access Quality)**
```bash
# Check route path
traceroute -I target_address

# Continuous route monitoring with mtr
sudo apt install mtr -y
mtr target_address
```

### Refund Policy Notes

- **Timing**: Most providers offer 7–30 day money-back guarantees starting from the payment date, not the activation date
- **Refund scope**: Some providers deduct domain or add-on service fees, so the actual refund may be less than expected
- **Refund method**: Confirm whether the refund goes back to the original payment method or as account credit
- **Special cases**: Payment channels like PayPal have independent dispute resolution. If a provider delays a refund, you can open a PayPal dispute
- **Evidence preservation**: Keep all communication records and screenshots as evidence in case of refund disputes

---

## 6. VPS Basic Setup Tutorial

### Choosing an OS

Major VPS providers offer multiple Linux distributions. Here is an analysis of each:

| Distribution | Best For | Characteristics | Package Manager |
|-------------|---------|----------------|-----------------|
| **Ubuntu LTS** | Beginners | Best documentation, largest community, best compatibility | apt |
| **Debian** | Stability seekers | Extremely stable, conservative packages, server-perfect | apt |
| **CentOS/Rocky Linux/AlmaLinux** | Enterprise users | Enterprise-grade stable, RHEL-compatible, Rocky/Alma recommended | dnf |
| **Fedora** | Early adopters | Latest features, newer packages, also great for desktops | dnf |
| **Arch Linux** | Advanced users | Rolling release, fully customizable, steep learning curve | pacman |

**Recommendation**: Beginners should start with **Ubuntu 22.04 LTS** or **Debian 12**.

### SSH Key Configuration

SSH key authentication is more secure than password login and effectively prevents brute-force attacks.

**1. Generate a key pair locally (Windows PowerShell / Linux / macOS)**
```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```
Saved to `~/.ssh/id_ed25519.pub` by default.

**2. Copy the public key to your VPS (Method 1: ssh-copy-id)**
```bash
ssh-copy-id -i ~/.ssh/id_ed25519.pub root@your_vps_ip
```

**3. Copy the public key to your VPS (Method 2: Manual)**
```bash
# View your public key locally
cat ~/.ssh/id_ed25519.pub

# On the VPS
mkdir -p ~/.ssh
echo "your_public_key_content" >> ~/.ssh/authorized_keys
chmod 600 ~/.ssh/authorized_keys
chmod 700 ~/.ssh
```

**4. Modify SSH config to disable password login (optional but recommended)**
```bash
sudo nano /etc/ssh/sshd_config
```
Modify these settings:
```ini
PasswordAuthentication no
PermitRootLogin without-password
PubkeyAuthentication yes
```
```bash
sudo systemctl restart sshd
```

### Basic Security Hardening

**1. Change the default SSH port**
```bash
sudo nano /etc/ssh/sshd_config
# Change Port 22 to another port (e.g., 2222)
sudo systemctl restart sshd
```

**2. Configure firewall (UFW)**
```bash
# Install UFW (if not installed)
sudo apt update && sudo apt install ufw -y

# Allow SSH (on your new port)
sudo ufw allow 2222/tcp

# Allow HTTP/HTTPS
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp

# Enable firewall
sudo ufw enable

# Check status
sudo ufw status verbose
```

**3. Install Fail2Ban to prevent brute-force attacks**
```bash
sudo apt update && sudo apt install fail2ban -y
sudo systemctl enable fail2ban
sudo systemctl start fail2ban
```

**4. Enable automatic system updates**
```bash
# Ubuntu/Debian
sudo apt install unattended-upgrades -y
sudo dpkg-reconfigure -plow unattended-upgrades
```

**5. Create a regular user (avoid daily root usage)**
```bash
# Create user
sudo adduser username

# Grant sudo privileges
sudo usermod -aG sudo username

# Copy SSH public key to new user
sudo mkdir -p /home/username/.ssh
sudo cp ~/.ssh/authorized_keys /home/username/.ssh/
sudo chown -R username:username /home/username/.ssh
```

---

## 7. Advanced Use Cases

### Proxy & VPN Tools (Clash/V2Ray/WireGuard)

> ⚠️ **Note**: Using proxy tools must comply with local laws and regulations. This section is for technical learning reference only.

**Option 1: X-ui (based on V2Ray/Xray)**

X-ui is a powerful Xray panel supporting multiple protocols (VLESS, VMess, Trojan, etc.) with a visual web management interface.

```bash
# Install X-ui
bash <(curl -sL https://raw.githubusercontent.com/mhsanaei/3x-ui/master/install.sh)

# After installation, access https://your_ip:2053 to enter the admin panel
# Default username/password: admin / admin
```

**Option 2: Clash (Meta kernel)**

```bash
# Install Clash Meta
wget -O /usr/local/bin/clash-meta \
  https://github.com/MetaCubeX/Clash.Meta/releases/latest/download/clash-meta-linux-amd64-v2firmware.tar.gz
tar -xzf clash-meta-linux-amd64-v2firmware.tar.gz -C /usr/local/bin/
chmod +x /usr/local/bin/clash-meta

# Create config directory
mkdir -p /etc/clash
# Download config or use subscription URL
# Run
clash-meta -f /etc/clash/config.yaml -d /etc/clash
```

**Option 3: WireGuard (lightweight VPN)**

WireGuard is a modern VPN protocol with excellent performance and simple configuration.

```bash
# Install WireGuard
sudo apt update && sudo apt install wireguard -y

# Generate key pair
wg genkey | tee privatekey | wg pubkey > publickey

# Server configuration
sudo nano /etc/wireguard/wg0.conf
```
Server config example:
```ini
[Interface]
PrivateKey = <server_private_key>
Address = 10.0.0.1/24
ListenPort = 51820
PostUp = iptables -A FORWARD -i wg0 -j ACCEPT; iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
PostDown = iptables -D FORWARD -i wg0 -j ACCEPT; iptables -t nat -D POSTROUTING -o eth0 -j MASQUERADE

[Peer]
PublicKey = <client_public_key>
AllowedIPs = 10.0.0.2/32
```
```bash
# Start
sudo wg-quick up wg0
sudo systemctl enable wg-quick@wg0
```

### Website Hosting

**Option 1: Nginx + PHP + MySQL (traditional LEMP stack)**

```bash
# Install Nginx
sudo apt update && sudo apt install nginx -y
sudo systemctl start nginx
sudo systemctl enable nginx

# Install MySQL
sudo apt install mysql-server -y
sudo mysql_secure_installation

# Install PHP
sudo apt install php-fpm php-mysql php-curl php-gd php-mbstring -y

# Configure Nginx site
sudo nano /etc/nginx/sites-available/default
```
Config example:
```nginx
server {
    listen 80;
    server_name yourdomain.com;
    root /var/www/html;
    index index.php index.html;

    location / {
        try_files $uri $uri/ =404;
    }

    location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/var/run/php/php8.1-fpm.sock;
    }
}
```
```bash
sudo nginx -t
sudo systemctl reload nginx
```

**Option 2: Docker quick deployment**

```bash
# Install Docker
curl -fsSL https://get.docker.com | sh
sudo systemctl start docker
sudo systemctl enable docker

# Deploy WordPress with Docker Compose
mkdir wordpress && cd wordpress
nano docker-compose.yml
```
```yaml
version: '3.8'
services:
  db:
    image: mysql:8.0
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: your_password
      MYSQL_DATABASE: wordpress
      MYSQL_USER: wordpress
      MYSQL_PASSWORD: your_password
  wordpress:
    image: wordpress:latest
    restart: always
    ports:
      - "80:80"
    environment:
      WORDPRESS_DB_HOST: db
      WORDPRESS_DB_USER: wordpress
      WORDPRESS_DB_PASSWORD: your_password
      WORDPRESS_DB_NAME: wordpress
    volumes:
      - ./wp-data:/var/www/html
```
```bash
docker-compose up -d
```

### Private Cloud Storage

**Option 1: Nextcloud (recommended)**

Nextcloud is an open-source private cloud solution with rich features — file sync, collaborative tools, calendar, contacts, and more.

```bash
# Deploy Nextcloud with Docker
mkdir nextcloud && cd nextcloud
nano docker-compose.yml
```
```yaml
version: '3'
services:
  app:
    image: nextcloud
    restart: always
    ports:
      - 8080:80
    volumes:
      - ./nextcloud_data:/var/www/html
    environment:
      - MYSQL_HOST=db
      - MYSQL_DATABASE=nextcloud
      - MYSQL_USER=nextcloud
      - MYSQL_PASSWORD=your_password
    depends_on:
      - db
  db:
    image: mysql:8
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: root_password
      MYSQL_DATABASE: nextcloud
      MYSQL_USER: nextcloud
      MYSQL_PASSWORD: your_password
    volumes:
      - ./db_data:/var/lib/mysql
```
```bash
docker-compose up -d
# Access http://your_ip:8080 to complete initialization
```

**Option 2: Alist (multi-cloud aggregation)**

Alist is a file listing program that aggregates multiple cloud drives (Aliyun Drive, Baidu Netdisk, Google Drive, etc.).

```bash
# Quick install
curl -fsSL "https://alist.nn.ci妖安装.sh" | bash -s install

# Start
systemctl start alist
# Default password is in the logs
journalctl -u alist --no-pager | grep password
```

### Dev/Test Environment

**Option 1: Caddy as reverse proxy + Docker**

```bash
# Install Docker
curl -fsSL https://get.docker.com | sh

# Install Caddy (auto HTTPS, reverse proxy)
echo "deb [trusted=yes] https://apt.fury.io/caddy/ /" | sudo tee /etc/apt/sources.list.d/caddy.list
sudo apt update && sudo apt install caddy -y

# Caddyfile example
sudo nano /etc/caddy/Caddyfile
```
```Caddyfile
example.com {
    reverse_proxy localhost:3000  # Node.js app
}

api.example.com {
    reverse_proxy localhost:8080  # API service
}

# Auto HTTPS
tls admin@example.com
```

**Option 2: Portainer for Docker management**

```bash
# Install Portainer (Docker visual management UI)
docker volume create portainer_data
docker run -d \
  --name portainer \
  -p 9000:9000 \
  -p 8000:8000 \
  --restart=always \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -v portainer_data:/data \
  portainer/portainer-ce
# Access http://your_ip:9000 to set up the admin account
```

---

## 8. Recommended Configuration Combos

Based on different use cases and budgets, here are recommended configuration combinations:

| Use Case | Recommended Config | Monthly Budget | Recommended Providers |
|---------|-------------------|---------------|----------------------|
| Light proxy / learning | 1 core / 1 GB / 20 GB SSD | $3–5 | RackNerd / BandwagonHost |
| Personal blog / portfolio | 1 core / 2 GB / 40 GB SSD | $5–10 | BandwagonHost / Vultr |
| Node.js backend service | 2 cores / 2 GB / 60 GB NVMe | $10–15 | Vultr / BandwagonHost |
| Nextcloud private cloud | 2 cores / 4 GB / 80 GB SSD | $15–20 | Vultr / DigitalOcean |
| Small e-commerce site | 2 cores / 4 GB / 100 GB NVMe | $20–30 | Tencent Cloud / Alibaba Cloud |
| Dev/test cluster | 4 cores / 8 GB / 160 GB NVMe | $40–50 | DigitalOcean / Vultr |
| Production HA environment | 4 cores / 8 GB / High-IO cloud disk | ¥200+ | Tencent Cloud / Alibaba Cloud |

**Special use case recommendations**:

- **Primarily accessed from China**: Prioritize Hong Kong, Japan, Singapore data centers — recommended: Tencent Cloud LH, Alibaba Cloud LH, BandwagonHost HK
- **Primarily accessed from overseas**: Choose US West Coast (Los Angeles, Seattle) — recommended: Vultr, DigitalOcean, RackNerd
- **Best overall value**: BandwagonHost CN2 GIA series — optimal balance of network quality and price
- **Enterprise-grade reliability**: AWS Lightsail, Google Cloud Compute Engine, Tencent Cloud Standard

---

## 9. Disclaimer

1. **Information timeliness**: Prices, configurations, and recommendations in this guide may change over time. Please verify the latest information on each provider's official website before purchasing.

2. **Purchase advice**: This guide provides only objective technical analysis and shared experience. It does not constitute any purchase or investment advice. Users should make independent judgments based on their own needs and bear the consequences of their purchasing decisions.

3. **Legal compliance**: During use of your VPS, please strictly comply with local laws and regulations as well as the Terms of Service of your chosen provider. Any illegal use is the sole responsibility of the user.

4. **Service availability**: Provider names, prices, and product information are sourced from publicly available information. We make no promises or guarantees regarding provider service quality, stability, or data security.

5. **Third-party links**: This guide may contain links to third-party websites for convenience of reference only. We are not responsible for the content or services of third-party websites.

6. **Performance test data**: Performance test results are influenced by multiple factors including network environment, test timing, and the provider's current resource utilization. Figures are for reference only and do not represent actual final experience.

---

## 10. License

This project is open source under the [MIT License](./LICENSE).

---

<p align="center">
  <strong>If this guide helped you, please give it a Star ⭐!</strong>
</p>

<p align="center">
  <a href="https://github.com/CG-spring/vps-vip-recommend/stargazers">
    <img src="https://img.shields.io/github/stars/CG-spring/vps-vip-recommend?style=flat-square&logo=github" alt="GitHub stars">
  </a>
  <a href="https://github.com/CG-spring/vps-vip-recommend/issues">
    <img src="https://img.shields.io/github/issues/CG-spring/vps-vip-recommend?style=flat-square&logo=github" alt="GitHub issues">
  </a>
  <a href="./LICENSE">
    <img src="https://img.shields.io/github/license/CG-spring/vps-vip-recommend?style=flat-square" alt="License">
  </a>
</p>

<p align="center">
  <sub>Made with ❤️ by CG-spring · Last updated: August 2026</sub>
</p>
