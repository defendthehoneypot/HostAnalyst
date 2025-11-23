# Scenario 01 — Credential Dumping (Mimikatz)

---

## 1. Description

Security operations detected unusual behavior on a Windows workstation assigned to a domain user. Alerts indicate potential access to LSASS and possible credential theft.

You have been provided with event logs exported from that host.

---

## 2. Artifacts Provided

From the EVTX attack samples repository:

- `Security.evtx`  
- `Sysmon.evtx`  
- `PowerShell.evtx` (if available for the sample)  
- `Defender.evtx` (if applicable)  

Recommended source:

- https://github.com/sbousseaden/EVTX-ATTACK-SAMPLES  

Use the Mimikatz or credential dumping sample that best fits your lab environment.

---

## 3. Analyst Tasks

1. Identify the process or processes that attempted to access `lsass.exe`.  
2. Determine how that process was started (parent process, command line).  
3. Identify the user account under which the process ran.  
4. Determine whether the attempt appears successful or not, based on logs.  
5. Look for evidence of follow-on activity (for example, lateral movement, service creation, logons from new hosts).  
6. Build a timeline of key events, from initial execution through any subsequent activity.  
7. Write a concise narrative (5–10 sentences) describing what happened and why it matters.

---

## 4. Key Questions

- Which process accessed LSASS, and how was it launched?  
- What privileges did the account have?  
- Are there signs of token theft or re-use?  
- Did the attacker attempt to connect to other systems using stolen credentials?  
- What gaps in logging, if any, made this harder to investigate?

---

## 5. Suggested Event IDs to Review

- **Security**  
  - 4688 (process creation)  
  - 4673 / 4674 (privileged service calls)  
  - 4624 / 4625 (logon / failed logon)  

- **Sysmon**  
  - 1 (process create)  
  - 10 (process access – LSASS access events)  

- **Defender**  
  - Any detection events that name credential dumping tools or behavior  

---

## 6. Deliverables

- Timeline of events (with timestamps).  
- Short narrative (5–10 sentences).  
- Key indicators:  
  - File paths  
  - Hashes  
  - Command lines  
  - User accounts  
  - Hosts or IPs involved  

Evaluate the analyst’s output using `../rubrics/scenario-rubric.md`.
