# 🚀 Ansible Linux Administration Automation

![Ansible](https://img.shields.io/badge/Automation-Ansible-red?style=for-the-badge&logo=ansible)
![Linux](https://img.shields.io/badge/Linux-Ubuntu-orange?style=for-the-badge&logo=ubuntu)
![AWS](https://img.shields.io/badge/Cloud-AWS%20EC2-yellow?style=for-the-badge&logo=amazonaws)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

## 📖 Overview

This project demonstrates how **Ansible** can automate common **Linux administration tasks** across multiple Ubuntu servers hosted on **AWS EC2**. Instead of manually configuring each server, a single Ansible playbook provisions and configures all managed nodes consistently.

The project follows industry best practices by organizing automation into reusable **Ansible Roles**, making it scalable and easy to maintain.

---

# 🎯 Objectives

- Automate repetitive Linux administration tasks.
- Manage multiple servers from a single control node.
- Use Infrastructure as Code (IaC) principles.
- Improve server consistency and reduce manual errors.
- Build a production-style Ansible project suitable for a Linux Administrator portfolio.

---

# 🏗 Architecture

```text
                     +-----------------------+
                     |   WSL Ubuntu          |
                     |  Ansible Control Node |
                     +-----------+-----------+
                                 |
                           SSH Authentication
                                 |
               +-----------------+-----------------+
               |                                   |
      +--------+--------+                 +--------+--------+
      | Ubuntu EC2 #1   |                 | Ubuntu EC2 #2   |
      |    server1      |                 |    server2      |
      +-----------------+                 +-----------------+
```

---

# 📂 Project Structure

```text
ansible-linux-admin/
│
├── inventory/
│   └── hosts
│
├── playbooks/
│   └── site.yml
│
├── roles/
│   ├── common/
│   │   └── tasks/main.yml
│   ├── users/
│   │   └── tasks/main.yml
│   ├── services/
│   │   └── tasks/main.yml
│   ├── ssh/
│   │   └── tasks/main.yml
│   └── security/
│       └── tasks/main.yml
│
├── screenshots/
├── ansible.cfg
└── README.md
```

---

# ⚙️ Technologies Used

- Ansible
- Ubuntu Linux
- AWS EC2
- SSH
- YAML
- WSL Ubuntu
- Git & GitHub

---

# ✨ Features

- Multi-server configuration management
- Package installation automation
- Linux user management
- Apache web server deployment
- SSH configuration
- UFW firewall configuration
- System package updates
- Idempotent playbooks
- Modular Ansible Roles

---

# 📦 Automated Tasks

### ✅ Package Management

Installs:

- Git
- Curl
- Vim
- Htop
- Tree
- Unzip
- Net-tools

---

### ✅ User Management

Creates:

- adminuser
- developer

---

### ✅ Service Management

- Install Apache2
- Enable Apache service
- Start Apache automatically

---

### ✅ SSH Hardening

- Disable root login
- Restart SSH service

---

### ✅ Security Hardening

- Install UFW Firewall
- Allow SSH access
- Enable firewall
- Upgrade installed packages

---

# 📋 Inventory Example

```ini
[linux_servers]
server1 ansible_host=<EC2_PUBLIC_IP_1>
server2 ansible_host=<EC2_PUBLIC_IP_2>

[linux_servers:vars]
ansible_user=ubuntu
ansible_ssh_private_key_file=~/.ssh/ansible-key.pem
```

---

# 🚀 Getting Started

## Clone Repository

```bash
git clone https://github.com/<your-username>/ansible-linux-admin.git
cd ansible-linux-admin
```

---

## Verify Connectivity

```bash
ansible all -m ping
```

Expected Output

```text
server1 | SUCCESS => {
    "ping": "pong"
}

server2 | SUCCESS => {
    "ping": "pong"
}
```

---

## Execute Playbook

```bash
ansible-playbook playbooks/site.yml
```

---

# 🔍 Verification

### Check Installed Packages

```bash
ansible linux_servers -m shell -a "git --version"
```

### Verify Users

```bash
ansible linux_servers -m shell -a "id adminuser"
```

### Verify Apache

```bash
ansible linux_servers -m shell -a "systemctl is-active apache2"
```

### Verify Firewall

```bash
ansible linux_servers -m shell -a "ufw status"
```

---

# 📊 Example Play Recap

```text
PLAY RECAP *********************************************************************

server1 : ok=18  changed=0  unreachable=0  failed=0

server2 : ok=18  changed=0  unreachable=0  failed=0
```

Running the playbook multiple times produces no unnecessary changes, demonstrating **Ansible idempotency**.

---

# 📚 Skills Demonstrated

- Linux Administration
- Ansible Automation
- Configuration Management
- Infrastructure as Code (IaC)
- AWS EC2 Management
- SSH Authentication
- Linux Security
- Service Management
- YAML
- Git & GitHub

---

# 💡 Key Learning Outcomes

- Automated Linux administration using Ansible
- Managed multiple remote Linux servers
- Created reusable Ansible Roles
- Applied Infrastructure as Code principles
- Improved deployment consistency across servers
- Reduced manual configuration effort

---

# 🔮 Future Improvements

- Dynamic AWS Inventory
- Nginx Role
- Docker Deployment Role
- Monitoring with Prometheus & Node Exporter
- Log Management
- CI/CD with GitHub Actions
- Ansible Vault for Secrets Management

---
