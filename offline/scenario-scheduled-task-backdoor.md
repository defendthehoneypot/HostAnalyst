# Scenario 04 — Scheduled Task Backdoor

---

## 1. Description

Routine monitoring has discovered an unusual scheduled task on a Windows system. It appears to execute an unapproved binary at regular intervals. You are asked to determine whether this represents malicious persistence and, if so, what else the attacker has done.

---

## 2. Artifacts Provided

- `Security.evtx`  
- `Sysmon.evtx`  
- `Microsoft-Windows-TaskScheduler/Operational.evtx`  

Use a scheduled-task-based attack sample from:

- https://github.com/sbousseaden/EVTX-ATTACK-SAMPLES  

---

## 3. Analyst Tasks

1. Identify all scheduled tasks created or modified in the timeframe of interest.  
2. Determine which task(s) appear suspicious, and why.  
3. Trace the executable or script launched by the task:  
   - Parent process  
   - Command line  
   - User context  
4. Identify any follow-on activity:  
   - Network connections  
   - Additional processes  
   - File modifications  

---

## 4. Key Questions

- Which scheduled task appears to be the backdoor, and how can you tell?  
- How frequently does it run, and under which account?  
- What payload does it execute?  
- Does it establish C2 or perform local actions only?  

---

## 5. Suggested Event IDs

- **TaskScheduler Operational**  
  - 106 (task registered)  
  - 140 (task updated)  
  - 200 / 201 (task started or completed)  

- **Sysmon**  
  - 1 (process create)  
  - 3 (network connections)  

---

## 6. Deliverables

- Description of suspicious scheduled tasks and their configuration.  
- Timeline showing task creation and execution events.  
- Narrative summary (5–10 sentences).  
- Recommended remediation and hardening steps.
