# Task Scheduler

* The purpose of Task Scheduler is to automatically run programs or perform tasks when a specific condition or time is reached.

Open:

```text
Win + R
```

Then:

```text
taskschd.msc
```

Task Scheduler allows Windows to execute programs automatically based on triggers.

For example:

```text
At startup
At logon
At a specific time
When an event occurs
```

This is important for security because legitimate administrators use scheduled tasks, but attackers can also abuse scheduled tasks for persistence.

## Explore Task Scheduler

Look at:

```text
Task Scheduler Library
```

Click several tasks.

Look at:

* Name
* Status
* Triggers
* Actions
* Conditions
* History

Don't delete or modify system tasks.
