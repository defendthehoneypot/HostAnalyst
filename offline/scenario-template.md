# Scenario X — Title

> Template for offline EVTX-based scenarios.

---

## 1. Description

Provide a brief narrative of suspected activity, for example:

> A user reported suspicious behavior on their workstation. EDR alerts suggest possible credential theft and lateral movement. You have been given exported Windows event logs from the affected host.

---

## 2. Artifacts Provided

List the EVTX and any other artifacts:

- `Security.evtx`  
- `Sysmon.evtx`  
- `PowerShell.evtx`  
- `TaskScheduler.evtx`  
- `Defender.evtx`  
- (Optional) MFT, registry hives, prefetch, Amcache, etc.  

---

## 3. Analyst Tasks

1. Determine the most likely **initial access method**.  
2. Identify **suspicious processes**, including parent/child relationships.  
3. Identify any **persistence mechanisms**.  
4. Identify signs of **credential theft**.  
5. Identify any **lateral movement** attempts or successes.  
6. Build a **timeline** of key events.  
7. Write a **5–10 sentence narrative** describing what happened.  

---

## 4. Key Questions

- What is the initial compromise vector?  
- Which user accounts appear to be compromised or misused?  
- What persistence mechanisms are present, if any?  
- Are there signs of credential dumping or token abuse?  
- Did the attacker move laterally? If so, how and where?  
- What data access or exfiltration activity can you infer from the logs?  
- What remediation steps would you recommend?  

---

## 5. Deliverables

- A short written summary (1–2 pages).  
- A timeline of events (table or bullet list).  
- A list of key indicators (file paths, hashes, command lines, IPs, domains, etc.).  

Use `../rubrics/scenario-rubric.md` to evaluate the results.
