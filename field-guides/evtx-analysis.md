# EVTX Analysis Field Guide

Quick reference for analyzing Windows event logs during incidents.

---

## 1. High-Value Log Channels

- **Security** (`Security.evtx`)  
- **Sysmon** (`Microsoft-Windows-Sysmon/Operational`)  
- **PowerShell** (`Microsoft-Windows-PowerShell/Operational`, `Windows PowerShell`)  
- **Task Scheduler** (`Microsoft-Windows-TaskScheduler/Operational`)  
- **Windows Defender** / other AV or EDR logs  

---

## 2. Key Event IDs

### Security

- 4624 — Successful logon  
- 4625 — Failed logon  
- 4634 — Logoff  
- 4672 — Special privileges assigned  
- 4688 — Process creation  
- 4697 — Service installation  
- 4768 / 4769 — Kerberos TGT / TGS  
- 4776 — NTLM authentication  

### Sysmon

- 1 — Process creation  
- 2 — File creation time changed  
- 3 — Network connection  
- 7 — Image loaded  
- 10 — Process access (for example, LSASS access)  
- 11 — File create  
- 13 — Registry value set  
- 22 / 23 — DNS query / response  

### PowerShell

- 4103, 4104 — Script block logging (if enabled)  

### Task Scheduler

- 106 — Task registered  
- 140 — Task updated  
- 200 / 201 — Task started / completed  

---

## 3. Typical Attack Patterns in Logs

### Credential Dumping

- Sysmon 10 showing access to `lsass.exe`.  
- Security 4673 / 4674 with SeDebugPrivilege.  

### Persistence

- New services: Security 4697, Sysmon 1 (service binary).  
- Scheduled tasks: Task Scheduler 106/140 with suspicious commands.  
- WMI: Sysmon 19/20/21, WMI-Activity logs.  

### Lateral Movement

- RDP: Security 4624 LogonType 10 from unexpected sources.  
- SMB / admin share use: Security and Sysmon 3.  
- Remote services or PsExec-like behavior: process creation from `services.exe` or `psexesvc.exe`.  

### Ransomware

- Sudden spike in Sysmon 11 (file create) events on a file server.  
- Shadow copy deletion commands in Security 4688 / Sysmon 1.  

---

## 4. Workflow

1. Identify timeframe of interest (from alert, user report, or first suspicious log).  
2. Filter events to that window and expand as needed.  
3. Start with process creation and logon activity (Security + Sysmon).  
4. Follow suspicious processes to related network connections, file, and registry activity.  
5. Build a timeline of key events.  

---

## 5. Pitfalls

- Log rollover / gaps (short retention).  
- Missing channels (Sysmon not installed, PowerShell logging disabled).  
- Time sync issues between hosts.  

Note gaps explicitly in your findings; they matter for response and future hardening.
