# Scenario 05 — Malicious PowerShell Execution

---

## 1. Description

Alerts indicate that PowerShell may have been used to download and execute malicious code on a workstation. You are provided with PowerShell and related Windows logs from that host.

---

## 2. Artifacts Provided

- `Security.evtx`  
- `Sysmon.evtx`  
- `Microsoft-Windows-PowerShell/Operational.evtx`  
- `Windows PowerShell.evtx` (classic log, if available)  

Use a PowerShell-based attack sample from:

- https://github.com/sbousseaden/EVTX-ATTACK-SAMPLES  

---

## 3. Analyst Tasks

1. Identify suspicious PowerShell executions, especially:  
   - Encoded commands  
   - Download or web requests  
   - AMSI bypass patterns  
2. Decode any Base64-encoded command lines.  
3. Determine which user ran the malicious PowerShell and how it was launched.  
4. Identify any payload drops or follow-on processes.  
5. Build a timeline from initial PowerShell execution through payload activity.  

---

## 4. Key Questions

- Which PowerShell commands appear malicious, and why?  
- What payload or script was ultimately executed?  
- How was the attack launched (for example, from a macro, script, or console)?  
- Did the attack establish persistence or lateral movement?  

---

## 5. Suggested Event IDs

- **PowerShell Operational**  
  - 4103, 4104 (script block logging, if enabled)  

- **Security / Sysmon**  
  - 4688 / Sysmon 1 (process creation)  
  - Sysmon 3 (network connections)  

---

## 6. Deliverables

- List of suspicious PowerShell command lines (decoded where possible).  
- Timeline of related activity.  
- Short narrative (5–10 sentences).  
- Recommendations for PowerShell logging and policy.
