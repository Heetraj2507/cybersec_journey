# Create a New User

Open **PowerShell as Administrator**.

You can create a test account with:

```powershell
New-LocalUser -Name "NewUser"
```

Windows may require additional password-related parameters depending on your configuration.


---

# What Are You Trying to Learn?

You're trying to answer:

> **“When I create an account, what evidence does Windows generate?”**

Open:

**Event Viewer**
→ **Windows Logs**
→ **Security**

Filter for **account-management events**.

* On the right side of the page, there is a **Filter** option. Click on it and set the **Event ID** to **4720**. It will display the event generated when a new user account is created.


One commonly relevant event is: `4720`

### Event ID 4720 — A user account was created

When you create the account, examine the event details and record:

* **Time**
* **Account created**
* **Subject account**
* **Target account**
* **Computer**
* **Event ID**
* **Other relevant fields**

This gives you a basic view of the Windows security evidence generated when a local user account is created.
