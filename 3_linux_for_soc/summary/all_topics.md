# Linux SOC Investigation Summary

## 1. Check Users

```bash
# List users on the Kali Linux system
cat /etc/passwd
```

Check for:

* Unusual users
* Users other than my normal Kali Linux username
* Users that need further investigation

---

# 2. Check Running Processes

```bash
# Display running processes
ps aux
```

Check for:

* check user other than your kali-linux username
* Unusual running processes
* Processes using a lot of CPU
* Strange or suspicious process paths

Example of a suspicious-looking path:

```text
/usr/local/bin/any_suspicious_file
```

---
# Check for any unsual running ?
 ## a) Check a Specific PID

```bash
# Get information about a specific process
ps -fp 1034
```

Replace `1034` with the PID you want to investigate.

```text
ps  → Display information about running processes
-f  → Full-format listing
-p  → Select a specific PID
```

---

## b) Sort Processes by CPU Usage

```bash
# Show the top 20 processes using the most CPU
ps aux --sort=-%cpu | head -20
```

This lists the first 20 processes with the highest CPU usage.

---

##  c) Sort Processes by Memory Usage

```bash
# Show the top 20 processes using the most memory
ps aux --sort=-%mem | head -20
```

This lists the first 20 processes with the highest memory usage.

---

## Important

If you find a suspicious process, **do not terminate it immediately**.

First collect information about it.

```bash
# Get more information about the process
ps -fp 1034
```

Only terminate a process when you understand what it is and why it should be stopped.

If you need to terminate a process:

```bash
sudo kill -9 1034
```

---

## d) Find the Actual Program Behind a PID

```bash
# Find the full path of the program running for a PID
sudo readlink -f /proc/1034/exe
```

### Meaning

```text
readlink → Shows where a link points

-f       → Follows the link and shows the complete path

/proc    → A special Linux filesystem containing information about
           running processes

/proc/1034/exe → The executable associated with PID 1034
```

This helps me understand which actual program is running for that PID.

---

## e) Check Network Connections

```bash
# Show listening network connections and the processes using them
sudo ss -tulpn
```

### Meaning

```text
-t → TCP
-u → UDP
-l → Listening sockets
-p → Show the process/program
-n → Show numbers instead of resolving names
```

This helps me identify which programs are listening for network connections.

---

# 3. Check Services

```bash
# List services
systemctl --type=service
```

Look for:

* Running services
* Failed services
* Unusual services
* Services that I do not recognize

---

## Check Failed Login Attempts

On Kali Linux, run:

```bash
sudo grep "Failed password" /var/log/auth.log
```

This searches for failed password authentication attempts.

---

## Check Successful Login Attempts

```bash
sudo grep "Accepted" /var/log/auth.log
```

This searches for successful authentication attempts.

For SSH investigations:

```bash
sudo grep "sshd.*Accepted" /var/log/auth.log
```

and:

```bash
sudo grep "sshd.*Failed password" /var/log/auth.log
```

---

# SOC Investigation Report

My report should contain:

```text
Timeline:

Source IP:

Target Username:

Failed Login Attempts:

Successful Login:

Suspicious Activity:

Evidence:
What logs, processes, PIDs, IP addresses.

Conclusion:

Recommended Action:

```

---

# Simple Investigation Flow

```text
1. Check users
       ↓
2. Check running processes
       ↓
3. Investigate suspicious PIDs
       ↓
4. Find the actual executable
       ↓
5. Check network connections
       ↓
6. Check services
       ↓
7. Check failed and successful logins
       ↓
8. Collect evidence
       ↓
9. Write timeline and conclusion
       ↓
10. Recommend an action
```

# Important Commands

```bash
# Check users
cat /etc/passwd

# Check running processes
ps aux

# Check a specific PID
ps -fp 1034

# Sort by CPU usage
ps aux --sort=-%cpu | head -20

# Sort by memory usage
ps aux --sort=-%mem | head -20

# Find the actual executable for a PID
sudo readlink -f /proc/1034/exe

# Check network connections
sudo ss -tulpn

# Check services
systemctl --type=service

# Check failed login attempts
sudo grep "Failed password" /var/log/auth.log

# Check successful login attempts
sudo grep "Accepted" /var/log/auth.log
```
