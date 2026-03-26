

<img width="1536" height="1024" alt="B5761A75-3454-4D18-A81D-AF7846A9CED3" src="https://github.com/user-attachments/assets/0bc712d8-eac2-4dd6-ae2e-3d978a528077" />



## 🔐 Ansible SSH Hardening Architecture

![SSH Hardening Architecture](./ssh-hardening-architecture.png)

---

## 🧠 Architecture Overview

This project demonstrates a role-based Ansible automation approach to harden SSH configuration on Linux servers.

The architecture follows a modular and reusable design, where each component of the role is responsible for a specific task.

---

## ⚙️ Workflow Explanation

### 1️⃣ Role Initialization
- Execution starts from the Ansible Playbook
- The playbook calls the ssh_hardening role

---

### 2️⃣ Tasks Execution (tasks/main.yml)
- Defines SSH hardening steps:
  - Disable root login
  - Disable password authentication
  - Enable key-based authentication
  - Configure secure SSH settings

---

### 3️⃣ Template Rendering (templates/sshd_config.j2)
- Uses a Jinja2 template to generate a secure SSH configuration
- Allows dynamic configuration using variables

---

### 4️⃣ Configuration Deployment
- The configuration is applied to:
```
/etc/ssh/sshd_config
```

---

### 5️⃣ Handlers Execution (handlers/main.yml)
- Triggered only when changes occur
- Restarts SSH service:
```
systemctl restart sshd
```

---

### 6️⃣ Final Outcome
- SSH is secured and hardened
- Only key-based authentication is allowed
- Protects against:
  - Brute-force attacks
  - Unauthorized access

---

## 🔑 Key Features

- Role-based modular design
- Idempotent automation (safe to run multiple times)
- Secure SSH configuration
- Template-driven approach
- Automated restart using handlers

---

## 🔐 Security Best Practices

- Disable root login (PermitRootLogin no)
- Disable password authentication (PasswordAuthentication no)
- Enforce secure SSH protocol
- Limit login attempts
- Use strong encryption settings

---

## 📌 Interview Explanation

"I built an Ansible role for SSH hardening using tasks, templates, and handlers. The configuration is dynamically generated using Jinja2 and applied in an idempotent way. Handlers ensure services restart only when needed, making the system efficient and production-ready."

---

## 🚀 How to Run

```
ansible-playbook -i inventory main.yml
```

---

## 🧪 Tested On

- Ubuntu 22.04
- Ansible 2.10+
- OpenSSH

---

## 📁 Role Structure

```
roles/
└── ssh_hardening/
    ├── tasks/main.yml
    ├── handlers/main.yml
    └── templates/sshd_config.j2
```

---
