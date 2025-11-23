# Timeline Building Field Guide

---

## 1. Why Timelines Matter

Timelines turn individual events into a coherent story:

- How the attacker got in.  
- What they did.  
- When and how far they progressed.  

They are essential for scoping, communication, and remediation.

---

## 2. Common Timeline Sources

- MFT (file system metadata)  
- Registry hives (user activity, persistence)  
- EVTX logs (Security, Sysmon, PowerShell, TaskScheduler, Defender)  
- Prefetch (recently executed binaries)  
- Amcache (program execution artifacts)  

Tools like Plaso, Timesketch, KAPE, MFTECmd, and RECmd can help automate extraction.

---

## 3. Basic Manual Timeline Approach

1. Extract relevant artifacts (MFT, EVTX, registry) from the host.  
2. Convert logs into a common format (for example, CSV) with timestamps.  
3. Sort by time, then group events by:  
   - Host  
   - User  
   - Process  

4. Highlight key pivot points:  
   - First execution of malicious binary or script.  
   - Creation of persistence.  
   - First lateral movement.  
   - First data access or exfiltration.  

---

## 4. Questions to Answer

- When did the attacker first gain execution?  
- When did they first gain elevated privileges?  
- When did they first move laterally?  
- When did they first access or modify sensitive data?  
- When was the activity detected (if at all)?  

---

## 5. Output Format

A simple, effective format:

| Time (UTC) | Host | User | Event Type | Details |
|-----------|------|------|------------|---------|

Or a structured bullet list grouped by day and hour.

---

## 6. Common Issues

- Inconsistent time zones between hosts.  
- Clock skew or incorrect system time.  
- Missing data for critical periods.  

Document these issues and adjust or annotate your timeline accordingly.
