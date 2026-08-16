# Linux Hardening
Today I am learning:

> "How can we make the server safer?"

Linux hardening means making the system more secure and reducing unnecessary security risks.

---

# 1. Create a Normal User

Run:

```bash "
sudo adduser kali
```

This creates a normal user called `kali`.

---

# 2. Check Users

Run:

```bash id="4apj2m"
cat /etc/passwd
```

This shows the users configured on the Linux system.


---

# 3. Check SSH Configuration

Run:

```bash id="p4x5jz"
sudo nano /etc/ssh/sshd_config
```

Look for settings such as:

```text id="qf5xmi"
PermitRootLogin
PasswordAuthentication
```

These settings control how SSH users can authenticate and whether root can log in directly.

**Important:** I should not change settings blindly.

Today my goal is to understand what these settings control.

---

# 4. Check the Firewall

Run:

```bash id="m6n8vp"
sudo ufw status
```

`ufw` is a simple tool used to manage the Linux firewall.

If the firewall is inactive, I can learn how it works.

For example:

```bash id="4s5q3n"
sudo ufw enable
```

Then check the status:

```bash id="1l6t2w"
sudo ufw status
```

**Important:** If I am connected to the VM remotely, I should not enable or change firewall rules without understanding them first because I could lock myself out.

---

# What I Learned


### 1. What does SSH do?

SSH allows us to securely connect to and manage a Linux machine remotely.

### 2. What does a firewall do?

A firewall controls network traffic and can block unwanted or unauthorized connections.

### 3. What does `ufw` do?

`ufw` (Uncomplicated firewall) is a simple firewall management tool used to allow or block network connections.

### 4. Why is SSH security important?

SSH is commonly used for remote access to Linux servers. If it is not secured properly, attackers may try to gain unauthorized access.

---

# Useful Commands

```bash id="x6j4p8"
# Create a normal user
sudo adduser kali

# Check users
cat /etc/passwd

# Check SSH configuration
sudo nano /etc/ssh/sshd_config

# Check firewall status
sudo ufw status

# Enable firewall
sudo ufw enable

# Check firewall status again
sudo ufw status
```

---

# End-of-Day Deliverable


Answer:

```text

1. What does SSH do?

2. What does a firewall do?

3. What does ufw do?

4. Why is SSH security important?
```
