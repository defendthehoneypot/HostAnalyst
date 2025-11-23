# Scenario 06 — Living-Off-the-Land Binaries (LOLBins) Abuse

---

## 1. Description

A host has shown signs of suspicious activity without obvious malware binaries. Logs suggest abuse of built-in Windows tools (LOLBins) such as `certutil`, `mshta`, or `rundll32`.

You are given logs to confirm and reconstruct the activity.

---

## 2. Artifacts Provided

- `Security.evtx`  
- `Sysmon.evtx`  

Use a LOLBins-based attack sample from:

- https://github.com/sbousseaden/EVTX-ATTACK-SAMPLES  

---

## 3. Analyst Tasks

1. Identify executions of common LOLBins (for example, `certutil.exe`, `mshta.exe`, `rundll32.exe`, `powershell.exe`).  
2. Examine command lines for signs of:  
   - Remote downloads  
   - Embedded scripts  
   - Suspicious DLLs or script arguments  
3. Correlate LOLBin executions to any network connections and file creations.  
4. Determine whether the activity indicates:  
   - Initial access  
   - Execution of malicious payloads  
   - Persistence or lateral movement  

---

## 4. Key Questions

- Which LOLBins were abused, and how?  
- What payload or script did they ultimately execute?  
- Is this activity clearly malicious or ambiguous admin behavior?  
- What detections or controls could reduce this risk?  

---

## 5. Suggested Event IDs

- **Security**  
  - 4688 (process creation)  

- **Sysmon**  
  - 1 (process create)  
  - 3 (network connections)  
  - 11 (file create)  

---

## 6. Deliverables

- List of LOLBin executions with suspicious command lines.  
- Timeline of activity, including related network or file events.  
- Narrative (5–10 sentences).  
- Recommendations for detection and hardening.
