
# Installation and Deployment

## 1. Prerequisites

The laboratory requires:

* Windows host
* Hyper-V
* Windows Server ISO
* Windows 11 ISO
* Sufficient RAM and storage
* Virtual network

Recommended initial allocation:

| VM       |  RAM | vCPU |  Disk |
| -------- | ---: | ---: | ----: |
| DC01     | 4 GB |    2 | 60 GB |
| CLIENT01 | 4 GB |    2 | 60 GB |

---

# 2. Hyper-V Network

Create an internal virtual switch:

```text
LAB-AD
```

The switch provides isolated communication between laboratory machines.

---

# 3. DC01

Create a Generation 2 virtual machine:

```text
Name: DC01
RAM: 4096 MB
CPU: 2 vCPU
Disk: 60 GB
Network: LAB-AD
```

Install Windows Server using:

```text
Windows Server Standard Evaluation
Desktop Experience
```

---

# 4. Hostname

Configure the server hostname:

```text
DC01
```

Verify:

```cmd
hostname
```

---

# 5. Static IP

Configure:

```text
IP Address: 192.168.100.10
Subnet Mask: 255.255.255.0
DNS: 192.168.100.10
```

The server will later provide DNS for the Active Directory domain.

---

# 6. Active Directory Domain Services

Install:

```text
Active Directory Domain Services
```

Then promote DC01 to a Domain Controller.

Create a new forest:

```text
cyberlab.local
```

NetBIOS name:

```text
CYBERLAB
```

Enable:

* DNS Server
* Global Catalog

---

# 7. Organizational Units

Create:

```text
CyberLab
│
├── Users
├── Groups
├── Computers
└── Servers
```

Under Users:

```text
TI
RH
Financeiro
Comercial
```

---

# 8. Validation

Verify:

```cmd
ipconfig /all
```

```cmd
nslookup cyberlab.local
```

```cmd
nslookup dc01.cyberlab.local
```

Verify Active Directory tools through:

```text
Server Manager → Tools
```

Expected tools include:

```text
Active Directory Users and Computers
DNS
Group Policy Management
```

---

# 9. Client Deployment

Create:

```text
CLIENT01
```

Install Windows 11 and connect it to:

```text
LAB-AD
```

Configure DNS:

```text
192.168.100.10
```

Validate connectivity:

```cmd
ping 192.168.100.10
```

Then join:

```text
cyberlab.local
```

---

# 10. Domain Authentication

After restarting CLIENT01, authenticate using a domain account.

Example:

```text
CYBERLAB\joao.silva
```

Validate:

```cmd
whoami
```

Expected:

```text
cyberlab\joao.silva
```
