# Your Windows Investigation Project

Now combine everything you have learned and use the available evidence to investigate the Windows machine.

Your project should answer:

> **“What happened on this Windows machine?”**

## What Is Evidence?

Evidence is the actual information you collect from Windows that supports and shows that an activity happened.

---

# How to Find Evidence

## 1. New User Created

### Step 1 — Check the Security Log

Open:

**Event Viewer → Windows Logs → Security**

Select **Filter Current Log...** and enter:

```text
4720
```

Event ID **4720** indicates that a user account was created.

### Step 2 — Open the Event

Double-click the event and record:

```text
Account Name:
Account Domain:
New Account:
Date and Time:
```

### Example Evidence

```text
Event ID: 4720
New Account: LabUser
Created By: Administrator
Date/Time: 09-08-2026 20:15:32
```

Take a screenshot of the event for your report.

---

# 2. Scheduled Task Created

For `LabTask`, open:

**Event Viewer → Applications and Services Logs → Microsoft → Windows → TaskScheduler → Operational**

Look for events related to the task being **registered, modified, or executed**.

You can also verify the task with:

```powershell
Get-ScheduledTask -TaskName "LabTask"
```

For more detailed information, run:

```powershell
schtasks /Query /TN "LabTask" /V /FO LIST
```

### Example Evidence

```text
Task Name: LabTask
Action: calc.exe
Trigger: At log on
Status: Ready
Author: <your computer\username>
```

Take a screenshot of the task information for your report.

---

# 3. Service Activity

Open:

**Event Viewer → Windows Logs → System**

Look for events with the source:

```text
Service Control Manager
```

Relevant Event IDs include:

```text
7035
7036
7040
7045
```

For example, **Event ID 7036** can indicate that a service changed state.

Record:

```text
Event ID:
Service Name:
Date/Time:
Description:
```

### Example Evidence

```text
Event ID: 7036
Source: Service Control Manager
Service: Example Service
Date/Time: 09-08-2026 20:20:15
Description: The service entered the running state.
```

---

# 4. What Counts as Evidence?

Your investigation should follow this process:

```text
Activity
    ↓
Windows records the activity
    ↓
Check Event Viewer or PowerShell
    ↓
Find the relevant information
    ↓
Record the Event ID, time, and details
    ↓
Take a screenshot if needed
    ↓
Add the evidence to your report
```

The goal is to show **what happened, when it happened, and what evidence Windows recorded**.

---

# Simple Report Format

## Evidence 1 — New User

```text
Event ID: 4720
Account: LabUser
Created By: Administrator
Date/Time: [Your timestamp]
```
**Take Screenshot:**


---

## Evidence 2 — Scheduled Task

```text
Task Name: LabTask
Action: calc.exe
Trigger: At log on
Date/Time: [Your timestamp]
```

**Take Screenshot:**


---

## Evidence 3 — Service Activity

```text
Event ID: 7036
Source: Service Control Manager
Service: [Service name]
Event: Service entered the running state
Date/Time: [Your timestamp]
```

**Take Screenshot:**


> **Note:** The information above is only an example and has been sanitized. Use the actual information and evidence from your own Windows machine when creating your report.
