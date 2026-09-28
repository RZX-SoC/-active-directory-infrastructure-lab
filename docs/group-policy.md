# Group Policy

## 1. Purpose

Group Policy provides centralized management of Windows users and computers in the Active Directory environment.

---

# 2. Baseline Policy

The initial policy is:

```text
GPO-Baseline-Security
```

The policy is intended to establish basic security requirements.

---

# 3. Initial Controls

The baseline may include:

* Password complexity
* Minimum password length
* Password history
* Account lockout
* Security-related Windows configuration

The exact values are documented when implemented in the laboratory.

---

# 4. GPO Management

Open:

```text
Server Manager
    ↓
Tools
    ↓
Group Policy Management
```

Create:

```text
GPO-Baseline-Security
```

Link the GPO to the appropriate Organizational Unit.

---

# 5. Client Validation

On CLIENT01:

```cmd
gpupdate /force
```

Then:

```cmd
gpresult /r
```

The output should show the applicable Group Policy Objects.

---

# 6. Troubleshooting

If a GPO does not apply, verify:

1. The client is joined to the correct domain.
2. DNS is functioning.
3. The GPO is linked to the correct OU.
4. The computer/user is located in the intended OU.
5. Security filtering is correct.
6. The policy has replicated.
7. `gpupdate /force` was executed.

---

# 7. Security Principle

Group Policy allows security controls to be managed centrally instead of configuring every workstation individually.

This improves consistency and reduces configuration drift.
