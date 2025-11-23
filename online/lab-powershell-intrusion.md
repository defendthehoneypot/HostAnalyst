# Lab 03 — PowerShell-Based Intrusion

---

## 1. Scenario

Suspicious PowerShell activity has been detected on a workstation, including encoded commands and outbound web requests. You are given live access to that host in the range to investigate.

---

## 2. Injects (Range Setup Notes)

Range operators should:

- Run a PowerShell-based dropper or loader, preferably with encoded commands.  
- Use PowerShell to download a payload from an HTTP or HTTPS endpoint.  
- Optionally establish persistence using a script or scheduled task.  

---

## 3. Allowed Tools

- PowerShell (including history where available).  
- Event Viewer (PowerShell logs, Security, Sysmon).  
- Sysinternals tools (Process Explorer, Autoruns).  
- Any available EDR/monitoring.

---

## 4. Analyst Tasks

1. Identify suspicious PowerShell executions, especially with encoded commands.  
2. Decode any Base64 or obfuscated command lines.  
3. Determine how PowerShell was launched (for example, from a macro, script, or console).  
4. Identify the payload that was downloaded or executed.  
5. Determine whether persistence was configured.  
6. Build a timeline of key events.  

---

## 5. Deliverables

- List of suspicious PowerShell commands (decoded where possible).  
- Description of any downloaded or executed payloads.  
- Timeline of relevant events.  
- Narrative (8–12 sentences) summarizing the intrusion and its impact.  
