# Identity and Access Control

## 1. Objective

This laboratory demonstrates basic identity and access-control concepts using Active Directory.

The objective is to simulate how users can receive access to organizational resources through security groups.

---

# 2. Access Model

The laboratory uses:

```text
User
  ↓
Security Group
  ↓
Permission
  ↓
Resource
```

Example:

```text
Carlos
  ↓
GG-FINANCEIRO
  ↓
Modify
  ↓
Financeiro
```

---

# 3. Security Groups

The following groups are planned:

```text
GG-TI
GG-RH
GG-FINANCEIRO
GG-COMERCIAL
```

---

# 4. File Resources

The simulated file server structure is:

```text
D:\Empresa
│
├── Financeiro
├── RH
├── TI
└── Comercial
```

---

# 5. Authorization

Permissions should preferably be assigned to security groups instead of individual users.

Example:

```text
GG-FINANCEIRO
       │
       ▼
Financeiro Share
       │
       └── Modify
```

Users receive the corresponding permissions through group membership.

---

# 6. Least Privilege

The laboratory follows the principle of least privilege.

Users should receive only the permissions required for their simulated responsibilities.

For example:

```text
Finance user
    ↓
Finance resources
```

rather than:

```text
Finance user
    ↓
All company resources
```

---

# 7. Validation

Access should be tested using both:

### Expected access

The user can access resources assigned to their group.

### Expected denial

The same user should not be able to access resources belonging to another department.

This demonstrates both authorization and access restriction.

---

# 8. Security Relevance

Identity and access management is an important component of defensive security.

Poorly managed permissions can contribute to:

* Unauthorized access
* Excessive privileges
* Data exposure
* Lateral movement
* Account abuse

The laboratory provides a controlled environment for studying these concepts.
