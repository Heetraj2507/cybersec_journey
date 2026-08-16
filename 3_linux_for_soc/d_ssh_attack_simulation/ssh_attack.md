# SSH Attack Simulation

Today I am learning how to generate failed SSH login attempts in my own lab.

I have:

```text
Kali VM → Testing machine
```

## 1. Find  IP

On kali linux , run:

```bash
ip addr
```

Find the kali-linux IP address, for example:

```text
192.168.1.10
```

## 2. Test Connection from Kali

On Kali, run:

```bash
ping 192.168.1.10
```
* your ip

## 3. Try SSH Login

From Kali:

```bash
ssh username@192.168.1.10
```
* your username and ip

Enter an intentionally incorrect password several times.

This is only being done inside my own lab to generate failed authentication logs.

## 4. Check `auth.log` on Kali

Run:

```bash
sudo grep "Failed password" /var/log/auth.log
```

Now I should be able to see the failed SSH login attempts in the log.

Now you see source ip because this is ssh login attempt.

## SOC Understanding

I am deliberately creating failed authentication events in my own lab so I can learn how a SOC analyst detects and investigates them.

## End-of-Day Deliverable


Take screenshots of:

```text
1. SSH connection attempt
2. Failed authentication
3. Corresponding auth.log entry
```

## Complete Commands

```bash
# Ubuntu: Find IP address
ip addr

# Kali: Test connection
ping 192.168.1.10

# Kali: Try SSH login
ssh username@192.168.1.10

# Ubuntu: Check failed SSH attempts
sudo grep "Failed password" /var/log/auth.log
```
