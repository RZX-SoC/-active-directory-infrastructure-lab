# Active Directory Infrastructure Lab

![Status](https://img.shields.io/badge/status-in%20progress-yellow)
![Windows Server](https://img.shields.io/badge/Windows%20Server-Lab-blue)
![Active Directory](https://img.shields.io/badge/Active%20Directory-AD%20DS-blue)
![DNS](https://img.shields.io/badge/DNS-Integrated-blue)
![Group Policy](https://img.shields.io/badge/Group%20Policy-GPO-blue)
![Virtualization](https://img.shields.io/badge/Virtualization-Hyper--V-blue)

## 📌 About the Project

This project is a hands-on laboratory designed to simulate a small corporate Windows infrastructure using Microsoft Active Directory.

The environment was built to practice and document fundamental concepts of IT infrastructure, identity management, authentication, authorization, DNS, Group Policy and access control.

The project is part of my technical portfolio and is intended to demonstrate practical knowledge through a reproducible laboratory environment.

---

## 🎯 Objectives

The main objectives of this project are:

* Deploy a Windows Server Domain Controller.
* Install and configure Active Directory Domain Services (AD DS).
* Configure Active Directory-integrated DNS.
* Create and organize Organizational Units (OUs).
* Create and manage domain users.
* Create security groups.
* Join Windows clients to the domain.
* Implement centralized policies using Group Policy Objects (GPOs).
* Apply basic access-control concepts.
* Document the infrastructure and configuration process.
* Develop practical troubleshooting skills.

---

## 🏢 Scenario

The laboratory simulates the IT infrastructure of a fictional company called:

**CyberLab Tecnologia**

The simulated environment contains different departments with separate users and access requirements.

### Departments

* IT
* Human Resources
* Finance
* Sales

The objective is to reproduce common administrative tasks performed by a Windows infrastructure administrator.

---

# 🏗️ Lab Architecture

```text
                         ┌──────────────────────┐
                         │      LAB-AD          │
                         │  Hyper-V Network     │
                         └──────────┬───────────┘
                                    │
                          ┌─────────▼─────────┐
                          │       DC01        │
                          │ Windows Server    │
                          │                   │
                          │ Active Directory  │
                          │ DNS               │
                          │ Domain Controller │
                          └─────────┬─────────┘
                                    │
                             Domain: cyberlab.local
                                    │
                          ┌─────────▼─────────┐
                          │     CLIENT01      │
                          │    Windows 11     │
                          │                   │
                          │ Domain Member     │
                          └───────────────────┘
```

---

# 🖥️ Virtual Machines

| Hostname | Operating System | Role                    | IP Address         |
| -------- | ---------------- | ----------------------- | ------------------ |
| DC01     | Windows Server   | Domain Controller / DNS | 192.168.100.10     |
| CLIENT01 | Windows 11       | Domain Member           | DHCP / Lab Network |

### Domain

```text
cyberlab.local
```

### NetBIOS Name

```text
CYBERLAB
```

### Virtual Network

```text
LAB-AD
```

---

# 🧰 Technologies Used

| Technology                       | Purpose                              |
| -------------------------------- | ------------------------------------ |
| Hyper-V                          | Virtualization                       |
| Windows Server                   | Server operating system              |
| Active Directory Domain Services | Identity and domain management       |
| DNS                              | Name resolution and AD functionality |
| Windows 11                       | Domain client                        |
| Group Policy                     | Centralized configuration            |
| NTFS Permissions                 | Resource access control              |
| CMD / PowerShell                 | Administration and troubleshooting   |

---

# 🔐 Active Directory Structure

The Active Directory environment is organized using Organizational Units to separate users, computers and administrative scopes.

```text
CyberLab
│
├── Users
│   ├── TI
│   ├── RH
│   ├── Financeiro
│   └── Comercial
│
├── Groups
│
├── Computers
│
└── Servers
```

---

# 👥 Users and Groups

Example users created in the laboratory:

| User         | Department | Security Group |
| ------------ | ---------- | -------------- |
| joao.silva   | IT         | GG-TI          |
| ana.souza    | HR         | GG-RH          |
| carlos.lima  | Finance    | GG-FINANCEIRO  |
| maria.santos | Sales      | GG-COMERCIAL   |

The project uses groups to organize access rather than assigning permissions individually whenever possible.

### Access model

```text
User
  │
  ▼
Security Group
  │
  ▼
Permission
  │
  ▼
Resource
```

This approach makes access management easier to maintain and audit.

---

# 🛡️ Group Policy

A baseline security policy is implemented through a Group Policy Object:

```text
GPO-Baseline-Security
```

The initial configuration covers concepts such as:

* Password requirements
* Password history
* Account lockout
* Password complexity
* Centralized policy management

The policy is tested on domain-joined clients using:

```cmd
gpupdate /force
```

and:

```cmd
gpresult /r
```

---

# 🌐 DNS

DNS is a fundamental component of the Active Directory environment.

The domain controller provides DNS services for the laboratory:

```text
DC01
192.168.100.10
```

The client uses the domain controller as its primary DNS server.

Example validation commands:

```cmd
ipconfig /all
```

```cmd
nslookup cyberlab.local
```

```cmd
nslookup dc01.cyberlab.local
```

This demonstrates the relationship between DNS and Active Directory domain services.

---

# 🔑 Domain Authentication

The Windows client is joined to:

```text
cyberlab.local
```

Domain authentication is tested using a domain account:

```text
CYBERLAB\joao.silva
```

The authentication process can be validated with:

```cmd
whoami
```

Expected result:

```text
cyberlab\joao.silva
```

---

# 📁 Access Control

The laboratory will simulate departmental file resources:

```text
D:\Empresa
│
├── Financeiro
├── RH
├── TI
└── Comercial
```

Access will be assigned through security groups.

Example:

```text
Carlos
   │
   ▼
GG-FINANCEIRO
   │
   ▼
Financeiro
```

This provides a practical demonstration of identity-based authorization using Active Directory groups and NTFS permissions.

---

# 📸 Evidence

Screenshots documenting the implementation will be stored in:

```text
/screenshots
```

Examples include:

* Windows Server installation
* Server hostname
* Static IP configuration
* AD DS installation
* Active Directory administrative tools
* DNS validation
* Domain users
* Client connectivity
* Domain join
* Domain authentication
* GPO application

The screenshots are intended to provide evidence of the implementation rather than replace the technical documentation.

---

# 📚 Documentation

Detailed documentation is available in the `docs/` directory.

| Document                                     | Description                      |
| -------------------------------------------- | -------------------------------- |
| [Architecture](docs/architecture.md)         | Infrastructure design            |
| [Installation](docs/installation.md)         | Environment deployment           |
| [Active Directory](docs/active-directory.md) | AD DS configuration              |
| [DNS](docs/dns.md)                           | DNS configuration and validation |
| [Group Policy](docs/group-policy.md)         | GPO configuration                |
| [Access Control](docs/access-control.md)     | Users, groups and permissions    |

---

# 🧪 Validation

The environment is validated through practical tests including:

```text
✔ Server hostname
✔ Static IP configuration
✔ DNS resolution
✔ Active Directory installation
✔ User creation
✔ Security group membership
✔ Domain connectivity
✔ Windows client domain join
✔ Domain authentication
✔ Group Policy application
```

Additional validation will be added as the laboratory evolves.

---

# 🚧 Project Status

**In Progress**

### Phase 1 — Core Infrastructure

* [x] Hyper-V laboratory network
* [x] Windows Server installation
* [x] DC01 configuration
* [x] Active Directory Domain Services
* [x] DNS
* [x] Domain creation
* [x] Initial users and groups
* [x] Windows client
* [x] Domain join
* [x] Initial GPO


---

# 🧠 Skills Demonstrated

This project demonstrates practical experience with:

* Windows Server administration
* Active Directory
* Identity and access management
* DNS
* Group Policy
* User and group administration
* Domain authentication
* NTFS permissions
* Network troubleshooting
* Virtualization
* Infrastructure documentation
* Security fundamentals

---

# ⚠️ Disclaimer

This laboratory is an isolated educational environment created for learning, experimentation and portfolio development.

All users, domains, credentials, hosts and company information used in this project are fictional.

No production credentials or confidential information should be committed to this repository.

---

# 👨‍💻 Author

**Marcio**

Cyber Defense student focused on:

* IT Infrastructure
* Networking
* Active Directory
* Cyber Defense
* SOC / Blue Team
* Offensive Security

GitHub: [raidenzx](https://github.com/RZX-SoC)
