# Service Activity

**do not modify or stop an important Windows service**.
observe existing services and investigate the events that Windows records when service activity occurs.

## 1. Open Event Viewer

Press **Win + R**, type:

```text
eventvwr.msc
```

and press **Enter**.

Navigate to:

```text
Event Viewer
→ Windows Logs
→ System
```

Look for events with the source:

```text
Service Control Manager
```

The **Service Control Manager (SCM)** manages Windows services.

You may find events showing that a service:

* Started
* Stopped
* Failed to start
* Changed state

---

## 2. Investigate Event ID 7045

Event ID **7045** is an important service-related event.

To search for it:

```text
Event Viewer
→ Windows Logs
→ System
→ Filter Current Log
```

Enter:

```text
7045
```

Event ID **7045** means:

```text
A service was installed in the system.
```

If you find a 7045 event, open it and record useful information such as:

```text
Event ID:
Date/Time:
Service Name:
Service File Name / Image Path:
Service Type:
Service Start Type:
Service Account:
```

### Important

Event ID 7045 is normally found in the **System** log, not the Security log.

If your lab does not generate Event ID 7045, **do not install a service just to create the event**.

Instead, document that the event was not generated during your lab activity and explain its expected meaning.

For example:

```text
Event ID 7045 was not observed during this lab because no new Windows service was installed. Event ID 7045 normally indicates that a service was installed.
```

This is also an important investigation lesson: **you should investigate the evidence that actually exists rather than creating activity just to produce a specific event.**
