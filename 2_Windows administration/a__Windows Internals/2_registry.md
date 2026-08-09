# Windows Registry

The **Windows Registry** is a database that Windows uses to store configuration information.

The purpose of this section is to understand **where Windows stores configuration information and why the Registry matters in cybersecurity**.

## Open Registry Editor

Press:

```text
Win + R
```

Then type:

```text
regedit
```

Press **Enter**.

You will see major Registry hives such as:

```text
HKEY_LOCAL_MACHINE
HKEY_CURRENT_USER
HKEY_CLASSES_ROOT
HKEY_USERS
HKEY_CURRENT_CONFIG
```

## Important Registry Hives

### HKLM — HKEY_LOCAL_MACHINE

Contains configuration that affects the **entire computer**.

```text
HKEY_LOCAL_MACHINE
```

### HKCU — HKEY_CURRENT_USER

Contains configuration associated with the **currently logged-in user**.

```text
HKEY_CURRENT_USER
```

### What does HKEY mean?

**HKEY** stands for **Handle to a Key**.

A Registry key is similar to a **folder** that contains Windows configuration settings.

For example:

```text
HKEY_LOCAL_MACHINE
    └── SOFTWARE
        └── Microsoft
```

## Security Relevance

The Registry can contain information related to:

* Installed software
* System configuration
* User configuration
* Services
* Startup mechanisms
* Security settings

Some malware also abuses Registry locations for **persistence**.

### What is Persistence?

**Persistence** is a method that allows a program to continue executing or regain execution after a reboot or logoff.

## Common Registry Locations to Inspect

### 1. Installed Software

```text
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall
```

You can often find:

* Application names
* Versions
* Installation locations
* Uninstall information

### 2. System Configuration

```text
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet
```

Contains configuration related to:

* Windows components
* Drivers
* Services

### 3. User Configuration

```text
HKEY_CURRENT_USER\SOFTWARE
```

Contains settings for applications and the current Windows user.

### 4. Services

```text
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services
``` 

Contains configuration information for Windows services.

### 5. Startup Mechanisms

```text
HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run
```

This location is important when learning about **Windows startup behavior and malware persistence**.

### 6. Security Settings

```text
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Defender
```

Security-related configuration can exist in different Registry locations.

## Safe Practice

**Do not modify, delete, or create Registry values while exploring.**

Only navigate through the Registry and observe the information.

Explore:

```text
HKEY_CURRENT_USER
```

and:

```text
HKEY_LOCAL_MACHINE
```

## Objective

> Understand that Windows configuration is stored in the Registry and learn how to safely navigate and inspect it.
