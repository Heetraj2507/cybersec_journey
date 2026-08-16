# Processes and Services

> "What is currently running on this Linux machine?"

This is important in cybersecurity and SOC investigations because, during an incident, we may find a suspicious or unfamiliar process running on a system.

---

# 1. What Is a Process?

A **process** is a program that is currently running on a Linux system.

For example, when you open Firefox, the operating system creates a process for Firefox.

Processes can be:

* System processes
* User processes
* Background processes
* Network services
* Security-related processes

---

# 2. View Processes

Run:

```bash
ps aux
```

You will see information similar to:

```text
USER       PID  %CPU  %MEM  COMMAND
root         1   ...   ...  /sbin/init
kali      ...   ...   ...  firefox
```

### Important fields

```text
USER       → User who owns the process
PID        → Process ID
%CPU       → CPU usage
%MEM       → Memory usage
COMMAND    → Command/program that is running
```

### PID = Process ID

Every running process has a **PID (Process ID)**.

The PID is a unique number assigned to a running process.

---

# 3. Use `top`

Run:

```bash
top
```

`top` displays processes in real time.

Look at:

```text
CPU usage
Memory usage
Process ID
Process name
```

Press:

```text
q
```

to exit `top`.

---

# 4. Find a Specific Process

Run:

```bash
ps aux | grep ssh
```

You are essentially asking:

> "Show me processes related to SSH."

The `|` symbol is called a **pipe**. It sends the output of one command to another command.

In this example:

```bash
ps aux | grep ssh
```

`ps aux` lists the processes, and `grep ssh` searches that output for the word `ssh`.

---

# 5. Look at Services

Linux services are background programs that provide functionality to the system.

To list services:

```bash
systemctl --type=service
```

To check the SSH service:

```bash
systemctl status ssh
```

If SSH is not installed, update the package list:

```bash
sudo apt update
```

Then install the OpenSSH server:

```bash
sudo apt install openssh-server
```

After installation, check the SSH service:

```bash
sudo systemctl status ssh
```

---

# 6. What Is SSH?

**SSH (Secure Shell)** is a protocol used to securely connect to and manage a Linux computer remotely over a network.

For example:

```bash
ssh username@192.168.1.10  (your ip & username)
```

SSH is commonly used by system administrators to remotely access Linux servers.

From a SOC/security perspective, SSH is important because attackers may attempt unauthorized SSH logins or use compromised SSH credentials.

---

# 7. SOC Exercise

someone says:

> "I think an attacker is running something suspicious on this server."

Your first basic investigation could be:

```bash
ps aux
```

Then look for unfamiliar processes.

You can also search for a specific process:

```bash
ps aux | grep suspicious_name
```

You should investigate unfamiliar processes by checking:

```text
PID
USER
COMMAND
CPU usage
Memory usage
Process location
Network connections
```

---


---

# 8. Useful Symbols

```bash
#   → Used for comments in Bash/Shell

|   → Pipe; sends the output of one command to another command

~   → Represents the current user's home directory
```

---

# End-of-Day Deliverable


Document the following:

```text
1. What is a process?
2. What is PID?
3. How do you list processes?
4. How do you check services?
5. What is SSH?
6. What commands can be used to investigate suspicious processes?
```

---

# Complete Command Sequence

```bash
# View all running processes
ps aux

# View processes in real time
top

# Search for SSH-related processes
ps aux | grep ssh

# List services
systemctl --type=service

# Check SSH service
systemctl status ssh

# Update package information if SSH is not installed
sudo apt update

# Install OpenSSH server
sudo apt install openssh-server

# Check SSH service
sudo systemctl status ssh
```
