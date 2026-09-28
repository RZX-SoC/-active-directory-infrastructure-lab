
# Active Directory Implementation

## 1. Purpose

Active Directory Domain Services provides centralized identity and resource management for the laboratory.

The domain is:

```text
cyberlab.local
```

---

## 2. Domain Controller

The Domain Controller is:

```text
DC01
```

IP:

```text
192.168.100.10
```

---

## 3. Organizational Units

The following structure is used:

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

Organizational Units allow users and computers to be logically organized and provide a target for Group Policy.

---

# 4. Users

Example laboratory identities:

```text
joao.silva
ana.souza
carlos.lima
maria.santos
```

These identities are fictional and exist exclusively in the laboratory.

---

# 5. Security Groups

The environment uses:

```text
GG-TI
GG-RH
GG-FINANCEIRO
GG-COMERCIAL
```

Users are assigned to groups according to their simulated department.

---

# 6. Authentication

The client authenticates against the Active Directory domain.

Example:

```text
CYBERLAB\joao.silva
```

Validation:

```cmd
whoami
```

---

# 7. Administrative Tools

Active Directory can be managed using:

```text
Active Directory Users and Computers
```

```text
Active Directory Domains and Trusts
```

```text
Group Policy Management
```

```text
DNS
```

---

# 8. Management Model

The laboratory follows a centralized management model.

```text
Domain Controller
       │
       ├── Users
       ├── Groups
       ├── Computers
       ├── Policies
       └── Authentication
```

This reduces administrative fragmentation and allows centralized control.
