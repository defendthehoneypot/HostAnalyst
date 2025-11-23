# Scenario 03 — WMI Persistence

---

## 1. Description

A host has shown intermittent suspicious behavior without an obvious malware process. EDR telemetry suggests possible WMI-based persistence. You have exported logs from the affected system.

---

## 2. Artifacts Provided

- `Security.evtx`  
- `Sysmon.evtx`  
- `Microsoft-Windows-WMI-Activity/Operational.evtx` (if available)  

Use a WMI persistence or WMI-based attack sample from:

- https://github.com/sbousseaden/EVTX-ATTACK-SAMPLES  

---

## 3. Analyst Tasks

1. Identify suspicious WMI event consumers, filters, and bindings.  
2. Map any WMI subscriptions to processes or commands they launch.  
3. Identify which user or account created or modified the WMI persistence.  
4. Determine whether WMI persistence is being used for:  
   - Initial execution  
   - Re-execution on schedule or trigger  
   - Lateral movement  
5. Build a timeline of:  
   - Creation of WMI artifacts  
   - First execution  
   - Any follow-on activity (network, process, or logon events).  

---

## 4. Key Questions

- Which WMI artifacts appear malicious or unnecessary?  
- What triggers their execution (for example, logon, time, specific event)?  
- What payload or command do they execute?  
- Does this persistence appear to have been used successfully, or is it dormant?  

---

## 5. Suggested Event IDs

- **Sysmon**  
  - 19 (WMI event filter activity)  
  - 20 (WMI event consumer activity)  
  - 21 (WMI binding activity)  
  - 1 (process create)  

- **WMI-Activity Operational**  
  - 5857–5861 (WMI provider and consumer activity)  

---

## 6. Deliverables

- List of suspicious WMI filters, consumers, and bindings.  
- Description of their triggers and payloads.  
- Timeline of WMI-related events.  
- Narrative (5–10 sentences) explaining how WMI was used by the attacker.  
