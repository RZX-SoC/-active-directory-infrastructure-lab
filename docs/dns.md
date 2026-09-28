# DNS Configuration

## 1. Overview

DNS is a critical component of the Active Directory environment.

Active Directory uses DNS for service discovery and domain-related communication.

---

## 2. DNS Server

The DNS service runs on:

```text
DC01
```

IP:

```text
192.168.100.10
```

---

## 3. Client Configuration

Domain clients should use the Domain Controller as their DNS server.

Example:

```text
CLIENT01
    │
    │ DNS query
    ▼
192.168.100.10
    │
    ▼
DC01
```

---

# 4. Validation

Check network configuration:

```cmd
ipconfig /all
```

Test domain resolution:

```cmd
nslookup cyberlab.local
```

Test Domain Controller resolution:

```cmd
nslookup dc01.cyberlab.local
```

Test connectivity:

```cmd
ping dc01.cyberlab.local
```

---

# 5. Troubleshooting

Common problems include:

### Incorrect DNS

If the client points to an external DNS server instead of the domain DNS server, Active Directory domain discovery may fail.

### Incorrect IP

Validate:

```cmd
ipconfig /all
```

### DNS cache

The local DNS cache can be cleared with:

```cmd
ipconfig /flushdns
```

### Domain discovery

Validate:

```cmd
nslookup cyberlab.local
```

DNS should be validated before troubleshooting domain-join problems.
