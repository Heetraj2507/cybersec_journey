# Create a Scheduled Task

For this lab, we are going to create a simple scheduled task that opens **Calculator**. This is a harmless example that can be used to understand how scheduled tasks work and what evidence Windows records.

> **Important:** Only perform this on a computer that you own or have permission to administer.

## 1. Create the Scheduled Task

Open **PowerShell as Administrator**.

Run the following command:

```powershell
schtasks /Create /TN "LabTask" /TR "calc.exe" /SC ONLOGON
```

This creates a scheduled task named `LabTask`.

The task is configured as follows:

* **Task name:** `LabTask`
* **Action:** `calc.exe`
* **Trigger:** `ONLOGON` — the task runs when a user logs on

If the command runs successfully, PowerShell will display a message confirming that the task was created.

## 2. Check That the Task Was Created

To verify the task, run:

```powershell
schtasks /Query /TN "LabTask" /V /FO LIST
```

Look through the output and make sure the task name, trigger, and action are correct.

## 3. Check the Task in Task Scheduler

Press **Win + R**, type:

```text
taskschd.msc
```

and press **Enter**.

In Task Scheduler, go to:

**Task Scheduler Library → LabTask**

Check the task details, including:

* Task name
* Trigger
* Action
* Author
* Creation or registration information, if available

## 4. Test the Task

To test the task without logging out and back in, run:

```powershell
schtasks /Run /TN "LabTask"
```

Calculator should open.


You can also sign out and sign back in to see whether the **ONLOGON** trigger starts Calculator automatically.

## Important Note

Q. If Calculator is not visible after running the scheduled task, **does that mean there was an error?**

**No.** A scheduled task can run successfully without a GUI window appearing on your current desktop.

`calc.exe` is a graphical application. Task Scheduler can start the process, but the window may not appear in your current interactive desktop depending on how the task is configured and how Calculator works on your version of Windows.



If you want to check whether Calculator was started, open PowerShell and run:

```powershell
Get-Process | Where-Object {$_.ProcessName -like "*calc*"}
```

If Calculator is running, PowerShell will return information about the process, such as:

* **Process Name**
* **Process ID (Id)**
* **CPU usage**
* **Memory usage**
* Other process-related information

For example, you may see a process with a name similar to:

```text
CalculatorApp
```
This means the Calculator process was started, even if its graphical window is not visible on your desktop.

## 5. Check the Event Logs

Now we want to see what evidence Windows generated when the task was created or run.

Open **Event Viewer** and go to:

**Event Viewer → Applications and Services Logs → Microsoft → Windows → TaskScheduler → Operational**

Look for events around the time you created, modified, or ran `LabTask`.

For each relevant event, record:

```text
Event ID:
Date/Time:
Task Name:
Action:
User/Account:
Result/Status:
```

The exact events you see can depend on your Windows version and logging configuration, so don't worry if your Event Viewer does not show every possible event.

The main goal of this step is to connect the activity you performed with the evidence Windows recorded.

## 6. Remove the Test Task

After finishing the lab, remove the scheduled task:

```powershell
schtasks /Delete /TN "LabTask" /F
```

Then check that it has been removed:

```powershell
schtasks /Query /TN "LabTask"
```

If the task no longer exists, the cleanup was successful.

## Lab Summary

The overall process is:

**Create → Verify → Investigate → Test → Remove**

This lab demonstrates how a scheduled task can be created, how it behaves when triggered, and how to investigate the Windows event logs for evidence of that activity.


