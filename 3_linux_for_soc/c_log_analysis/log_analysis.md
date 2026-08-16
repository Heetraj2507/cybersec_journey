# Linux Log Analysis


Today i learned how to investigate **authentication logs** in Linux.

This is very important for a **SOC analyst** because authentication logs can help us find:

* Failed login attempts
* Successful logins
* Usernames
* Source IP addresses
* Login times
* Possible brute-force attacks

---

# 1. Open `auth.log`

Run:

```bash
sudo less /var/log/auth.log
```

The `auth.log` file contains authentication-related information.

Inside `less`, we can search for failed login attempts.

Type:

```text
/Failed password
```

Then press **Enter**.

To exit `less`, press:

```text
q
```

---

# 2. Search for Failed Logins Directly

Instead of reading the whole file, we can use `grep`.

Run:

```bash
sudo grep "Failed password" /var/log/auth.log
```

This shows log entries containing **Failed password**.

This can help us find unsuccessful login attempts.

---

# 3. Search for Successful Logins

Run:

```bash
sudo grep "Accepted" /var/log/auth.log
```

This searches for successful authentication events.

For example, we may see:

```text
Accepted password for user from 192.168.1.20
```

This tells us that a login was successful.

---

# 4. Count Failed Login Attempts

Run:

```bash
sudo grep "Failed password" /var/log/auth.log | wc -l
```

This counts the number of lines containing **Failed password**.

### Meaning of the commands:

```text
grep → Searches for specific text

| → Sends the output of one command to another command

wc -l → Counts the number of lines
```

means:

> Find failed password entries and count them.

---

# 5. Find Source IP Addresses

Run:

```bash
sudo grep "Failed password" /var/log/auth.log
```

The output may contain an IP address.

Example:

```text
Failed password for user from 192.168.1.20
```

We need to identify the important information from the log.

Look for:

```text
Username → Who was targeted?

Source IP → Where did the login attempt come from?

Time → When did it happen?

Success/Failure → Was the login successful?
```
### `Source IP is normally shown in actual SSH login attempts`



---

# 6. SOC Thinking

Suppose we find these events:

```text
21:01 Failed password from 10.0.0.5
21:02 Failed password from 10.0.0.5
21:02 Failed password from 10.0.0.5
21:03 Accepted password from 10.0.0.5
```

As a student learning SOC, I understand this as:

> There were several failed login attempts from the same IP address, and then a successful login happened.

This **could be a sign of a brute-force attack**, where someone tries different passwords until one works.

But we should **not immediately say it was an attack**. We need to investigate more.

We should check:

```text
Who was trying to log in?
Which username was targeted?
What was the source IP address?
Was the successful login expected?
Was the user authorized to log in?
What happened after the successful login?
```

## Simple SOC Thinking

```text
Multiple failed logins
        ↓
Same IP address
        ↓
Successful login
        ↓
Investigate further
        ↓
Decide if it is suspicious
```

---

# End-of-Day Deliverable


Document the following:

```text
Number of failed attempts:

Source IP:

Username targeted:

Successful login observed?:

Timestamp:

My conclusion:
```

---

# Complete Command Sequence

```bash
# 1. Open auth.log
sudo less /var/log/auth.log

# Press "q" to exit less

# 2. Search for failed login attempts
sudo grep "Failed password" /var/log/auth.log

# 3. Search for successful logins
sudo grep "Accepted" /var/log/auth.log

# 4. Count failed login attempts
sudo grep "Failed password" /var/log/auth.log | wc -l

# 5. View failed login entries and investigate source IPs
sudo grep "Failed password" /var/log/auth.log
```

