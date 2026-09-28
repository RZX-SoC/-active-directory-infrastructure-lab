
# Infrastructure Architecture

## 1. Overview

The laboratory uses Hyper-V to create an isolated virtual infrastructure representing a small corporate Windows environment.

The design contains a Domain Controller and Windows client machines connected through a dedicated virtual network.

---

## 2. Network

The laboratory network is:

```text
LAB-AD
```

The environment uses:

```text
192.168.100.0/24
```

The Domain Controller uses:

```text
192.168.100.10
```

---

## 3. Components

### DC01

Operating System:

```text
Windows Server
```

Responsibilities:

* Active Directory Domain Services
* Domain Controller
* DNS
* Authentication
* Identity management
* Group Policy management

### CLIENT01

Operating System:

```text
Windows 11
```

Responsibilities:

* Domain workstation
* User authentication
* GPO testing
* Access-control testing

---

## 4. Logical Architecture

```text
CyberLab Tecnologia
│
├── Domain
│   └── cyberlab.local
│
├── Users
│   ├── TI
│   ├── RH
│   ├── Financeiro
│   └── Comercial
│
├── Groups
│   ├── GG-TI
│   ├── GG-RH
│   ├── GG-FINANCEIRO
│   └── GG-COMERCIAL
│
├── Computers
│
└── Servers
```

---

## 5. Design Principles

The environment was designed around several infrastructure and security principles:

### Centralized Identity

Users are managed through Active Directory instead of independently on each workstation.

### Group-Based Authorization

Permissions are assigned to groups whenever possible.

### Separation

Organizational Units are used to separate users, computers and administrative scopes.

### Centralized Policy

Group Policy is used to apply configuration consistently.

### Documentation

Each implementation step is documented to make the laboratory reproducible.

---

## 6. Security Considerations

The laboratory is isolated from production environments.

The project does not use real organizational credentials or confidential information.

The architecture is intentionally simplified for educational purposes.
