# VPS 精选推荐指南

> 🌐 English version: [README_EN.md](./README_EN.md)
>
> 🔖 本指南持续更新，当前版本：**v2.0.0**
>
> ⚠️ **免责声明**：本指南仅供参考，不构成任何购买建议。

---

## 目录

- [一、前言：为什么需要 VPS？](#一前言为什么需要-vps)
- [二、VPS vs 传统虚拟主机 vs 云服务器](#二vps-vs-传统虚拟主机-vs-云服务器)
- [三、选择 VPS 的核心指标](#三选择-vps-的核心指标)
  - [1. CPU 性能](#1-cpu-性能)
  - [2. 内存与存储](#2-内存与存储)
  - [3. 带宽与流量](#3-带宽与流量)
  - [4. 机房位置与网络质量](#4-机房位置与网络质量)
  - [5. 付款方式与隐私保护](#5-付款方式与隐私保护)
- [四、主流 VPS 推荐](#四主流-vps-推荐)
  - [入门级（$2-5/月）](#入门级-2-5月)
  - [进阶型（$5-15/月）](#进阶型-5-15月)
  - [专业型（$15+/月）](#专业型-15月)
- [五、VPS 选购避坑指南](#五vps-选购避坑指南)
  - [常见套路](#常见套路)
  - [如何测试 VPS 性能](#如何测试-vps-性能)
  - [退款政策注意事项](#退款政策注意事项)
- [六、VPS 基础配置教程](#六vps-基础配置教程)
  - [系统选择](#系统选择)
  - [SSH 密钥配置](#ssh-密钥配置)
  - [基础安全加固](#基础安全加固)
- [七、高级应用场景](#七高级应用场景)
  - [科学上网（Clash/V2Ray）](#科学上网clashv2ray)
  - [搭建网站](#搭建网站)
  - [私有云盘](#私有云盘)
  - [开发测试环境](#开发测试环境)
- [八、推荐组合方案](#八推荐组合方案)
- [九、免责声明](#九免责声明)
- [十、许可证](#十许可证)

---

## 一、前言：为什么需要 VPS？

在这个数字化时代，个人网站、博客、技术博客、独立开发者作品集等需求越来越普遍。而虚拟专用服务器（VPS，Virtual Private Server）已经成为互联网基础设施中不可或缺的一环。那么，究竟什么时候你需要一台 VPS？

**VPS 的核心价值在于"独立"与"可控"**。与共享主机不同，VPS 给你分配独立的计算资源——独立的 CPU 核心、独立的内存、独立的磁盘空间，以及独立的操作系统环境。你拥有 root 管理员权限，可以自由安装任何软件、配置任何服务，不受他人干扰。

选择 VPS 的典型场景包括：

- **搭建个人网站或博客**：使用 WordPress、Hugo、Hexo 等框架搭建独立博客，完全掌控内容和数据
- **学习 Linux 系统管理**：在一个真实的生产级环境中练习服务器运维技能
- **部署 API 和后端服务**：运行 Node.js、Python、Go 等语言构建的 Web 服务
- **科学上网与网络探索**：部署代理工具实现自由访问互联网（需遵守当地法律法规）
- **开发测试环境**：隔离的开发测试环境，不影响本地开发机器
- **私有云盘与文件存储**：搭建 Nextcloud、Seafile 等私有云解决方案
- **科学计算与数据处理**：利用服务器的 CPU/GPU 资源进行数据分析、机器学习训练
- **游戏服务器**：搭建 Minecraft、Valheim 等游戏私服，与朋友联机

无论你是学生、开发者、创业者还是技术爱好者，VPS 都是一个值得掌握的技能。

---

## 二、VPS vs 传统虚拟主机 vs 云服务器

在购买服务器之前，你需要了解三种主流托管方式的区别，选择最适合自己的方案。

| 对比维度 | 传统虚拟主机 | VPS | 云服务器 |
|---------|-------------|-----|---------|
| **资源隔离** | 共享资源，受邻居影响大 | 独立资源，性能有保障 | 弹性伸缩，资源池化 |
| **root 权限** | ❌ 无 | ✅ 完全拥有 | ✅ 完全拥有 |
| **自定义程度** | 只能通过面板操作 | 完全自定义 | 完全自定义 |
| **价格区间** | $1-10/月 | $2-100+/月 | $5-500+/月 |
| **扩展性** | 受单台服务器限制 | 升级套餐或迁移 | 随时弹性扩容 |
| **管理难度** | 简单（cPanel/Plesk） | 中等（需 Linux 基础） | 中高（需一定经验） |
| **适用人群** | 纯小白、不需要技术 | 有一定技术基础 | 企业级/高流量场景 |
| **网络质量** | 一般共享带宽 | 独享带宽或共享优质带宽 | 可选优质 BGP 线路 |

**结论**：
- 纯新手、无技术背景 → 选择带面板的虚拟主机（如 Bluehost、HostGator）
- 有一定 Linux 基础，需要更多控制权 → VPS（性价比最高）
- 企业级、高可用、弹性伸缩需求 → 云服务器（AWS/GCP/阿里云等）

---

## 三、选择 VPS 的核心指标

在选购 VPS 时，以下几个核心指标直接决定了服务器的实际体验。建议在购买前仔细对比，避免踩坑。

### 1. CPU 性能

CPU 是服务器的大脑，决定了计算能力的上限。需要注意以下几点：

- **核心数 vs 单核性能**：不是核心数越多越好。对于 Web 服务，单核性能往往更关键；对于并行计算任务（如视频转码、数据处理），多核更重要。
- **CPU 型号是否标注**：优质商家会明确标注 CPU 型号（如 AMD EPYC 7543、Intel Xeon Gold）。如果只写"高性能 CPU"，往往是共享/虚标资源。
- **是否支持 SSE4.2/AVX**：如果你计划运行特定应用（如 WireGuard 需要 AES-NI），需要确认 CPU 特性支持。
- **CPU 积分/性能模式**：部分商家（如搬瓦工）采用积分制，低负载时积累积分，高负载时消耗积分。这是合理机制，但需要了解其规则。

**推荐关注**：AMD EPYC 系列、Intel Xeon Scalable 系列，通常性能更稳定。

### 2. 内存与存储

- **内存（RAM）**：至少 1GB 才能流畅运行基本 Linux 环境（含小型 Web 服务）。2GB 是舒适线，4GB+ 可以运行更复杂的服务。
- **存储类型**：
  - **NVMe SSD**：读写速度可达 3000-7000 MB/s，是目前最佳选择
  - **SATA SSD**：读写速度约 500 MB/s，性价比之选
  - **HDD（机械硬盘）**：速度慢，不推荐用于 VPS，除非大容量存储场景
- **存储容量**：根据实际需求选择。基础博客/代理 20-40GB 足够；需要存放大量数据则需要更大空间。

### 3. 带宽与流量

- **带宽（Bandwidth）**：指服务器端口速率，常见有 1Gbps、10Gbps。注意：独享带宽 > 共享带宽。
- **月流量（Traffic）**：每月允许的数据传输量。部分商家标注"无限流量"，实际是共享带宽限速（超过阈值后降至 1Mbps）。务必仔细阅读 TOS（服务条款）。
- **流量超额政策**：了解流量用尽后的处理方式（降速/停机/额外计费），选择对你最有利的方案。

**常见套路警示**：标称"无限流量"但实际限速至 128Kbps 的商家在市场上并不少见，请务必核实。

### 4. 机房位置与网络质量

机房位置直接影响访问延迟和稳定性。不同用途应选择不同机房：

| 用途 | 推荐机房 | 典型延迟（国内） |
|-----|---------|---------------|
| 面向国内用户的网站 | 香港、新加坡、日本 | 30-80ms |
| 面向海外用户的网站 | 美国洛杉矶、西雅图 | 150-200ms |
| 科学上网/代理节点 | 香港、日本、美国西海岸 | 40-180ms |
| 欧洲用户服务 | 荷兰、法兰克福、伦敦 | 200ms+ |
| 游戏服务器 | 选择目标玩家群体所在地 | 视情况 |

**线路类型优先级**：
1. 优化 CN2 GIA 线路（国内访问最优）
2. 优化 CN2 线路
3. 优质 BGP 混合线路
4. 普通国际线路

**网络测试建议**：购买前使用 Looking Glass 或试用机会测试实际网络质量，不要只看商家宣传。

### 5. 付款方式与隐私保护

- **付款方式**：信用卡、PayPal、加密货币（如 BTC、USDT）等。匿名性需求高的用户建议选择支持加密货币支付的商家。
- **隐私保护**：部分商家（如 Proton VPN 的 hosting 服务）提供无日志政策，尊重用户隐私。
- **退款政策**：大多数商家提供 7-30 天退款保证。确认退款条款（是否要求理由、是否扣除域名费等）。
- **支付宝/微信**：国内用户友好的商家通常支持支付宝，降低购买门槛。

---

## 四、主流 VPS 推荐

以下推荐基于市场口碑、性价比、网络质量等综合因素评估。各档推荐均有详细参数对比，帮助你快速做出选择。

> 📝 **提示**：价格和配置可能随时变化，建议前往各商家官网确认最新信息。

### 入门级（$2-5/月）

适合：轻量级网站、Linux 学习、科学上网基础需求

| 商家 | CPU | 内存 | 硬盘 | 带宽 | 月流量 | 价格 | 机房 | 推荐指数 |
|-----|-----|-----|-----|-----|-------|-----|-----|---------|
| RackNerd | 1 vCPU | 1 GB | 18 GB NVMe | 1 Gbps | 2 TB | $2.99/月 | 美国多机房 | ⭐⭐⭐⭐ |
| GreenGeeks | 1 vCPU | 1 GB | 50 GB SSD | 不限 | 无限 | $2.95/月 | 美/欧/亚 | ⭐⭐⭐⭐ |
| Hostinger | 1 vCPU | 0.5 GB | 10 GB SSD | 100 Mbps | 1 TB | $2.69/月 | 美/欧/亚 | ⭐⭐⭐ |
| Contabo | 1 vCPU | 2 GB | 20 GB SSD | 1 Gbps | 无限 | €3.99/月 | 德/美/新 | ⭐⭐⭐⭐ |

### 进阶型（$5-15/月）

适合：个人开发者、小型网站、中等流量服务

| 商家 | CPU | 内存 | 硬盘 | 带宽 | 月流量 | 价格 | 机房 | 推荐指数 |
|-----|-----|-----|-----|-----|-------|-----|-----|---------|
| 搬瓦工（BandwagonHost） | 1-2 vCPU | 1-2 GB | 20-40 GB SSD | 1-2.5 Gbps | 1-2 TB | $5.99/月起 | HK/CN2 GIA | ⭐⭐⭐⭐⭐ |
| RackNerd（高配） | 2 vCPU | 3 GB | 45 GB NVMe | 1 Gbps | 3 TB | $10.99/月 | 美国多机房 | ⭐⭐⭐⭐ |
| Vultr | 2 vCPU | 2 GB | 55 GB SSD | 1 Gbps | 2 TB | $6/月 | 全球25+机房 | ⭐⭐⭐⭐ |
| 腾讯云轻量应用服务器 | 2 vCPU | 4 GB | 80 GB SSD | 30 Mbps | 1200 GB | ¥30/月 | 中国大陆 | ⭐⭐⭐⭐ |
| 阿里云轻量应用服务器 | 1 vCPU | 2 GB | 50 GB SSD | 30 Mbps | 2 TB | ¥24/月 | 中国大陆 | ⭐⭐⭐⭐ |

### 专业型（$15+/月）

适合：高流量网站、开发测试环境、商业应用

| 商家 | CPU | 内存 | 硬盘 | 带宽 | 月流量 | 价格 | 机房 | 推荐指数 |
|-----|-----|-----|-----|-----|-------|-----|-----|---------|
| 搬瓦工（CN2 GIA 高级） | 2-4 vCPU | 2-4 GB | 40-80 GB SSD | 1-10 Gbps | 1-2 TB | $19.99/月起 | HK/CN2 GIA | ⭐⭐⭐⭐⭐ |
| Vultr（高配） | 4 vCPU | 8 GB | 160 GB NVMe | 1 Gbps | 3 TB | $40/月 | 全球25+机房 | ⭐⭐⭐⭐ |
| 腾讯云标准型 | 2 vCPU | 4 GB | 高性能云盘 | 弹性公网 | 按量计费 | ¥0.2/时起 | 中国大陆 | ⭐⭐⭐⭐⭐ |
| DigitalOcean | 4 vCPU | 8 GB | 160 GB SSD | 1 Gbps | 5 TB | $48/月 | 全球10机房 | ⭐⭐⭐⭐ |
| AWS Lightsail | 2 vCPU | 4 GB | 80 GB SSD | 弹性 | 3 TB | $20/月 | 全球多机房 | ⭐⭐⭐⭐ |

> ⚠️ **价格备注**：以上价格为参考价，实际价格可能因促销、配置升级、货币汇率等因素有所不同。

---

## 五、VPS 选购避坑指南

### 常见套路

在 VPS 市场上，存在着不少套路和陷阱。以下是经验总结，帮助你避坑：

**套路一：虚假无限流量**
部分商家标注"无限流量"，但实际在服务条款中规定：超过某个阈值（如 10TB）后将限速至极低速率（128Kbps-1Mbps），或直接断开连接。真正无限流量的商家凤毛麟角。

**套路二：超售严重**
部分低价 VPS 提供商为了盈利，会在同一物理服务器上超量销售 VPS 资源（overcommit），导致所有 VPS 性能下降。表现为：测试时性能优秀，实际使用时卡顿严重。辨别方法：查看商家的口碑和用户评价，尤其是长期用户的使用体验。

**套路三：CPU 型号不透明**
如果商家不标注具体 CPU 型号，而只写"高性能 vCPU"，很可能是在共享资源或使用了性能较差的 CPU。优质商家通常会明确标注 AMD EPYC、Intel Xeon 等型号。

**套路四：低价套路**
某些商家用极低价格吸引用户（如 $1/月），但续费价格可能是原价的 3-5 倍（$5/月变为 $25/月续费）。购买前务必查看续费价格。

**套路五：数据中心位置误导**
部分商家标注"亚洲优化线路"，但实际机房在美洲，只是接入了某些优化路由。务必核实机房的真实地理位置。

**套路六：退款套路**
一些商家虽然承诺"30天退款"，但实际操作中设置重重障碍：要求提供设备序列号截图、扣除域名费/附加服务费、审批流程漫长（30天+）等。选择退款政策透明、无套路的商家。

### 如何测试 VPS 性能

购买 VPS 后，建议按以下步骤进行全面测试：

**1. 基础配置检查**
```bash
# 查看系统信息
cat /etc/os-release
uname -a

# 查看 CPU 型号和核心数
cat /proc/cpuinfo | grep "model name" | head -1
nproc

# 查看内存
free -h

# 查看磁盘空间
df -h
```

**2. 磁盘 I/O 性能测试**
```bash
# 使用 dd 测试顺序写入速度（不是专业测试，但可参考）
dd if=/dev/zero of=testfile bs=1M count=1024 oflag=direct

# 使用 fio 进行更专业的测试（需安装）
sudo apt update && sudo apt install fio -y
fio --name=randread --ioengine=libaio --rw=randread --bs=4k --numjobs=4 --size=1G --runtime=60
```

**3. 网络速度测试**
```bash
# 使用 Bench.sh 脚本进行综合测试（包含国内节点）
wget -qO- bench.sh | bash

# 单独测试特定节点的延迟和速度
curl -s https://raw.githubusercontent.com/ernisn/supervps/main/tools/tes

# iperf3 测试（需要两台机器配合）
# 服务器端
iperf3 -s
# 客户端
iperf3 -c 服务器IP -p 5201
```

**4. CPU 性能测试**
```bash
# 使用 sysbench 进行 CPU 压力测试
sudo apt install sysbench -y
sysbench cpu --cpu-max-prime=20000 run
```

**5. 路由追踪（国内访问质量）**
```bash
# 查看路由走向
traceroute -I 目标地址

# 使用 mtr 进行持续路由监控
sudo apt install mtr -y
mtr 目标地址
```

### 退款政策注意事项

- **时长确认**：大多数商家提供 7-30 天退款保证，以付款日期起算，不是以激活日期起算
- **退款范围**：部分商家会扣除域名、附加服务费用，实际退款金额可能低于预期
- **退款方式**：确认退款原路返回（退至原支付方式）还是退至账户余额
- **特殊情况**：部分支付渠道（如 PayPal）有独立的争议解决机制，如果商家退款拖延，可以通过 PayPal 争议解决
- **证据保留**：保留所有沟通记录、截图等证据，以备退款纠纷时使用

---

## 六、VPS 基础配置教程

### 系统选择

主流 VPS 默认提供多种 Linux 发行版可选。以下是各系统的特点分析：

| 发行版 | 适合人群 | 特点 | 包管理器 |
|-------|---------|-----|---------|
| **Ubuntu LTS** | 新手首选 | 文档最全，社区活跃，兼容性最好 | apt |
| **Debian** | 追求稳定 | 极其稳定，软件包保守，适合服务器 | apt |
| **CentOS/Rocky Linux/AlmaLinux** | 企业用户 | 企业级稳定，RHEL 兼容，推荐 Rocky/Alma | dnf |
| **Fedora** | 喜欢新特性 | 尝鲜首选，软件较新，适合桌面 | dnf |
| **Arch Linux** | 高级用户 | 滚动更新，完全自定义，学习曲线陡峭 | pacman |

**推荐**：新手从 **Ubuntu 22.04 LTS** 或 **Debian 12** 开始。

### SSH 密钥配置

SSH 密钥认证比密码登录更安全，可以有效防止暴力破解。

**1. 在本地生成密钥对（Windows PowerShell / Linux/macOS）**
```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```
默认保存在 `~/.ssh/id_ed25519.pub`

**2. 将公钥复制到 VPS（方法一：ssh-copy-id）**
```bash
ssh-copy-id -i ~/.ssh/id_ed25519.pub root@你的VPS_IP
```

**3. 将公钥复制到 VPS（方法二：手动复制）**
```bash
# 在本地查看公钥
cat ~/.ssh/id_ed25519.pub

# 在 VPS 上执行
mkdir -p ~/.ssh
echo "你复制的公钥内容" >> ~/.ssh/authorized_keys
chmod 600 ~/.ssh/authorized_keys
chmod 700 ~/.ssh
```

**4. 修改 SSH 配置禁用密码登录（可选但推荐）**
```bash
sudo nano /etc/ssh/sshd_config
```
修改以下内容：
```ini
PasswordAuthentication no
PermitRootLogin without-password
PubkeyAuthentication yes
```
```bash
sudo systemctl restart sshd
```

### 基础安全加固

**1. 修改 SSH 默认端口**
```bash
sudo nano /etc/ssh/sshd_config
# 将 Port 22 改为其他端口（如 2222）
sudo systemctl restart sshd
```

**2. 配置防火墙（UFW）**
```bash
# 安装 UFW（如未安装）
sudo apt update && sudo apt install ufw -y

# 允许 SSH（修改后的端口）
sudo ufw allow 2222/tcp

# 允许 HTTP/HTTPS
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp

# 启用防火墙
sudo ufw enable

# 查看状态
sudo ufw status verbose
```

**3. 安装 Fail2Ban 防暴力破解**
```bash
sudo apt update && sudo apt install fail2ban -y
sudo systemctl enable fail2ban
sudo systemctl start fail2ban
```

**4. 系统自动更新**
```bash
# Ubuntu/Debian
sudo apt install unattended-upgrades -y
sudo dpkg-reconfigure -plow unattended-upgrades
```

**5. 创建普通用户（不使用 root 登录日常操作）**
```bash
# 创建用户
sudo adduser username

# 赋予 sudo 权限
sudo usermod -aG sudo username

# 复制 SSH 公钥到新用户
sudo mkdir -p /home/username/.ssh
sudo cp ~/.ssh/authorized_keys /home/username/.ssh/
sudo chown -R username:username /home/username/.ssh
```

---

## 七、高级应用场景

### 科学上网（Clash/V2Ray）

> ⚠️ **注意**：使用代理工具需遵守当地法律法规，本节仅供技术学习参考。

**方案一：使用 X-ui（基于 V2Ray/Xray）**

X-ui 是一款功能强大的 Xray 面板，支持多种协议（VLESS、VMess、Trojan 等），提供可视化 Web 管理界面。

```bash
# 安装 X-ui
bash <(curl -sL https://raw.githubusercontent.com/mhsanaei/3x-ui/master/install.sh)

# 安装后访问 https://你的IP:2053 进入管理面板
# 默认用户名/密码：admin / admin
```

**方案二：使用 Clash（Meta 内核）**

```bash
# 安装 Clash Meta
wget -O /usr/local/bin/clash-meta https://github.com/MetaCubeX/Clash.Meta/releases/latest/download/clash-meta-linux-amd64-v2firmware.tar.gz
tar -xzf clash-meta-linux-amd64-v2firmware.tar.gz -C /usr/local/bin/
chmod +x /usr/local/bin/clash-meta

# 创建配置目录
mkdir -p /etc/clash
# 下载配置或使用订阅链接
# 运行
clash-meta -f /etc/clash/config.yaml -d /etc/clash
```

**方案三：使用 WireGuard（轻量级 VPN）**

WireGuard 是一种现代化的 VPN 协议，性能优秀且配置简单。

```bash
# 安装 WireGuard
sudo apt update && sudo apt install wireguard -y

# 生成密钥对
wg genkey | tee privatekey | wg pubkey > publickey

# 服务端配置
sudo nano /etc/wireguard/wg0.conf
```
服务端配置示例：
```ini
[Interface]
PrivateKey = <服务器私钥>
Address = 10.0.0.1/24
ListenPort = 51820
PostUp = iptables -A FORWARD -i wg0 -j ACCEPT; iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
PostDown = iptables -D FORWARD -i wg0 -j ACCEPT; iptables -t nat -D POSTROUTING -o eth0 -j MASQUERADE

[Peer]
PublicKey = <客户端公钥>
AllowedIPs = 10.0.0.2/32
```
```bash
# 启动
sudo wg-quick up wg0
sudo systemctl enable wg-quick@wg0
```

### 搭建网站

**方案一：使用 Nginx + PHP + MySQL（传统 LEMP 架构）**

```bash
# 安装 Nginx
sudo apt update && sudo apt install nginx -y
sudo systemctl start nginx
sudo systemctl enable nginx

# 安装 MySQL
sudo apt install mysql-server -y
sudo mysql_secure_installation

# 安装 PHP
sudo apt install php-fpm php-mysql php-curl php-gd php-mbstring -y

# 配置 Nginx 站点
sudo nano /etc/nginx/sites-available/default
```
配置示例：
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

**方案二：使用 Docker 快速部署**

```bash
# 安装 Docker
curl -fsSL https://get.docker.com | sh
sudo systemctl start docker
sudo systemctl enable docker

# 使用 Docker Compose 部署 WordPress
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

### 私有云盘

**方案一：Nextcloud（推荐）**

Nextcloud 是开源的私有云解决方案，功能丰富，支持文件同步、协作办公、日历、联系人等。

```bash
# 使用 Docker 部署 Nextcloud
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
# 访问 http://your_ip:8080 完成初始化
```

**方案二：Alist（支持多种网盘聚合）**

Alist 是一款支持聚合多种网盘（阿里云盘、百度网盘、Google Drive 等）的文件列表程序。

```bash
# 一键安装
curl -fsSL https://alist.nn.ci妖安装.sh | bash -s install

# 启动
systemctl start alist
# 默认密码在日志中
journalctl -u alist --no-pager | grep password
```

### 开发测试环境

**方案一：使用 Caddy 作为反向代理 + Docker**

```bash
# 安装 Docker
curl -fsSL https://get.docker.com | sh

# 安装 Caddy（自动 HTTPS，反向代理）
echo "deb [trusted=yes] https://apt.fury.io/caddy/ /" | sudo tee /etc/apt/sources.list.d/caddy.list
sudo apt update && sudo apt install caddy -y

# Caddyfile 配置示例
sudo nano /etc/caddy/Caddyfile
```
```Caddyfile
example.com {
    reverse_proxy localhost:3000  # Node.js 应用
}

api.example.com {
    reverse_proxy localhost:8080  # API 服务
}

# 自动 HTTPS
tls admin@example.com
```

**方案二：使用 Portainer 管理 Docker**

```bash
# 安装 Portainer（Docker 可视化管理界面）
docker volume create portainer_data
docker run -d \
  --name portainer \
  -p 9000:9000 \
  -p 8000:8000 \
  --restart=always \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -v portainer_data:/data \
  portainer/portainer-ce
# 访问 http://your_ip:9000 设置管理员账号
```

---

## 八、推荐组合方案

根据不同用途和预算，以下是推荐的配置组合方案：

| 用途场景 | 推荐配置 | 月预算 | 推荐商家 |
|---------|---------|-------|---------|
| 轻量代理/学习 | 1核/1GB/20GB SSD | $3-5 | RackNerd / 搬瓦工 |
| 个人博客/作品集 | 1核/2GB/40GB SSD | $5-10 | 搬瓦工 / Vultr |
| Node.js 后端服务 | 2核/2GB/60GB NVMe | $10-15 | Vultr / 搬瓦工 |
| Nextcloud 私有云 | 2核/4GB/80GB SSD | $15-20 | Vultr / DigitalOcean |
| 小型电商网站 | 2核/4GB/100GB NVMe | $20-30 | 腾讯云 / 阿里云 |
| 开发测试集群 | 4核/8GB/160GB NVMe | $40-50 | DigitalOcean / Vultr |
| 生产环境高可用 | 4核/8GB/高IO云盘 | ¥200+ | 腾讯云 / 阿里云 |

**特殊需求推荐**：

- **国内访问为主**：优先选择香港、日本、新加坡机房，推荐腾讯云轻量、阿里云轻量、搬瓦工 HK 机房
- **海外访问为主**：选择美国西海岸机房（洛杉矶、西雅图），推荐 Vultr、DigitalOcean、RackNerd
- **追求最高性价比**：搬瓦工 CN2 GIA 系列，综合网络质量与价格最优
- **企业级可靠性**：AWS Lightsail、Google Cloud Compute Engine、腾讯云标准型

---

## 九、免责声明

1. **信息时效性**：本指南中的价格、配置、推荐信息可能随时间变化，建议在购买前前往商家官网核实最新信息。

2. **购买建议**：本指南仅提供客观的技术分析和经验分享，不构成任何购买建议或投资建议。用户应根据自身需求独立判断并承担购买决策的后果。

3. **使用合规性**：使用 VPS 过程中，请严格遵守当地法律法规以及所购买商家的服务条款（Terms of Service）。任何违法使用行为由使用者自行承担责任。

4. **服务可用性**：商家名称、价格、产品信息均来源于公开资料，我们不对商家的服务质量、稳定性、数据安全做任何承诺或保证。

5. **第三方链接**：本指南中可能包含指向第三方网站的链接，这些链接仅供方便参考，我们不对第三方网站的内容或服务负责。

6. **性能测试数据**：性能测试结果受网络环境、测试时间、被测商家资源使用情况等多种因素影响，仅供参考，不代表最终实际体验。

---

## 十、许可证

本项目采用 [MIT 许可证](./LICENSE) 进行开源。

---

<p align="center">
  <strong>如果本指南对你有帮助，欢迎 Star ⭐ 支持一下！</strong>
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
  <sub>Made with ❤️ by CG-spring · Last updated: 2026-08</sub>
</p>
