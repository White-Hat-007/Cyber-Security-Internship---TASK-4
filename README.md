# Cyber-Security-Internship---TASK-4

# 🔥 Linux Firewall Configuration using UFW (Uncomplicated Firewall)

This documents how to install, configure, and test firewall rules on a Kali Linux system using **UFW (Uncomplicated Firewall)**. The task covers installing UFW, adding and removing rules, and understanding how firewalls control traffic.

---


## 📌 Steps Performed

### 1. Install UFW

```bash
sudo apt install ufw
````

> This installs UFW along with any dependencies.

---

### 2. Enable the Firewall

```bash
sudo ufw enable
```

> Output:

```
Firewall is active and enabled on system startup
```

---

### 3. Check UFW Status

```bash
sudo ufw status verbose
```

> Output:

```
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), disabled (routed)
New profiles: skip
```

---

### 4. Add Firewall Rules

#### Block incoming traffic on port 23 (Telnet)

```bash
sudo ufw deny 23
```

#### Allow incoming traffic on port 22 (SSH)

```bash
sudo ufw allow 22
```

> Output for each:

```
Rule added
Rule added (v6)
```

---

### 5. View Numbered Rules

```bash
sudo ufw status numbered
```

> Example output:

```
Status: active

     To                         Action      From
     --                         ------      ----
[ 1] 23                         DENY IN     Anywhere
[ 2] 23 (v6)                    DENY IN     Anywhere (v6)
[ 3] 22                         ALLOW IN    Anywhere
[ 4] 22 (v6)                    ALLOW IN    Anywhere (v6)
```

---

### 6. Delete Rules by Number

To delete a rule, use:

```bash
sudo ufw delete [rule_number]
```

#### Example:

```bash
sudo ufw delete 1
```

> You’ll be prompted:

```
Deleting:
 deny 23
Proceed with operation (y|n)? y
Rule deleted
```

Repeat as needed (e.g., for rule 2).

---

### 7. Final Rule Status

```bash
sudo ufw status numbered
```

> Output:

```
Status: active

     To                         Action      From
     --                         ------      ----
[ 1] 22                         ALLOW IN    Anywhere
[ 2] 22 (v6)                    ALLOW IN    Anywhere (v6)
```

---

## 🔍 How UFW Filters Traffic

* **Default Policy**: Blocks all incoming traffic unless explicitly allowed.
* **Outgoing Traffic**: Allowed by default to ensure internet functionality.
* **Rule-Based**: UFW processes rules in the order added (numbered).
* **IPv6 Support**: Automatically adds rules for IPv6 unless disabled.

---

## 🧪 Testing the Rules

* To test blocked port (e.g., 23), use:

  ```bash
  telnet localhost 23
  ```
* You should see a **Connection refused** message.
* Ensure SSH is still functional on port 22.

---

## 📷 Screenshots

The screenshots are attached to visualise the working/steps followed.

---

## ✅ Outcome & Learning

* 🔐 Configured UFW firewall on Kali Linux
* ➕ Added and removed inbound traffic rules
* 📊 Understood how UFW filters traffic based on defined policies
* 🧠 Gained hands-on experience managing Linux network security

---

## 🧰 Tools Used

* **Kali Linux (in VirtualBox)**
* **UFW (Uncomplicated Firewall)**

---
