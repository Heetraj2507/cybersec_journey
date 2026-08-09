#  Windows Services

## What I Will Learn

* How Windows services work in the background.
* How to check the status of a service.
* How services start and stop.
* How to identify the executable used by a service.
* How services run under different Windows accounts.
* How to inspect services safely.
* Basic knowledge of Windows internals and security.


### What is a Windows Service?

A **Windows service** is a program that runs quietly in the background without needing you to open it manually.

Windows uses services to handle many important tasks, such as:

* Windows Update
* Network connections
* Security features
* System logging
* Printing
* Other background system functions

You can view and manage Windows services using the **Services** window.

### How to open Windows Services

Press: **Win + R**

A small **Run** window will appear.

Type:  ```services.msc```

Then press **Enter**.

You'll see a list of services with information such as:

* **Name** – The name of the service
* **Description** – What the service does
* **Status** – Whether it is currently running
* **Startup Type** – When and how Windows starts the service
* **Log On As** – The account the service runs under

### Understanding the basics

**Running**
The service is currently active and working in the background.

**Stopped**
The service is not currently running.

**Automatic**
Windows normally starts the service automatically, usually when the system starts.

**Manual**
The service isn't started automatically. Windows or another program can start it when it is needed.

**Disabled**
The service has been prevented from starting normally.

---

## Practice

Let's take a quick look at one real Windows service.

Open:

```text
services.msc
```

Find:

**Windows Update**

Right-click it and select **Properties**.

Take a look at the following information:

**1) Service Name:** The internal name Windows uses to identify a service.  
**Example:** `wuauserv`

**2) Display Name:** The user-friendly name shown for the service.  
**Example:** `Windows Update`

**3) Description:** A brief explanation of what the service does.  
**Example:** `Manages Windows updates.`

**4) Path to Executable:** The location of the program that runs the service.  
**Example:** `C:\Windows\System32\svchost.exe`

**5) Startup Type:** Defines how and when Windows starts the service.  
**Example:** `Automatic`

**6) Service Status:** Shows whether the service is currently running or stopped.  
**Example:** `Running`

**7) Log On Account:** Shows which Windows account the service runs under.  
**Example:** `Local System`




 **don't change any settings**. We're just observing and learning what each option means.

Take a screenshot of the Properties window and keep it for your notes. This will help you remember what a Windows service looks like and what information is available about it.
