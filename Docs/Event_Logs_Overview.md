# Event Log Overview

## Event Log Fundamentals

### Location: Where to Find Event Logs?

**In NT/Win2000/XP/Server 2003:**
- `.evt` file type
- `%systemroot%\System32\config` [file:1]

**In Vista/Win7/Win8/Win10/Win11:**
- `.evtx` file type
- `%systemroot%\System32\winevt\Logs`
- Remote log server
- Filenames: `Security.evtx`, `Application.evtx`, `System.evtx`, etc. [file:1]

>!Note
>These are default locations only. Administrators can customize log locations via registry keys:

```bash

HKLM\SYSTEM\CurrentControlSet\Services\EventLog\Application
HKLM\SYSTEM\CurrentControlSet\Services\EventLog\System
HKLM\SYSTEM\CurrentControlSet\Services\EventLog\Security

```
---

### Types of Event Logs

1. **Security**

2. **System**

3. **Application**

4. **Custom Application and Services** 

Check this for Complete Info : [Types_OF_Events_Logs]()
---

## Security Logs

Most reviewed log in Windows forensics.

- User authentication and logon
- User behavior and actions
- File/Folder/Share access
- Security settings modifications

**Key Features:**

- Audits failures and successes
- Detailed logging can be enabled on specific user accounts
- Only updated by the LSASS process
- Third-party applications cannot insert events 

[Here]() is the additional file for what is recorded in security logs ?

## Analysis Scenarios

1. **Tracking Account Usage** 

- [General Information]()

- [Practical Approach]()

2. **Tracking Lateral Movement**
3. **Event Log Clearing**
4. **Malware Execution and Process Tracking**
5. **Capturing Command Lines and Scripts**



