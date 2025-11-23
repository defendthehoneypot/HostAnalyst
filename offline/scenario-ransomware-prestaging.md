# Scenario 07 — Ransomware Pre-Staging and Execution

---

## 1. Description

A file server experienced a burst of file modifications and user reports of inaccessible documents. Early indicators suggest possible ransomware or destructive malware. You are provided with logs from the server.

---

## 2. Artifacts Provided

- `Security.evtx`  
- `Sysmon.evtx`  
- Optional: additional logs (for example, backup/Volume Shadow Copy logs)  

Use a ransomware or destructive malware sample from:

- https://github.com/sbousseaden/EVTX-ATTACK-SAMPLES  

---

## 3. Analyst Tasks

1. Identify the process or processes responsible for mass file modifications.  
2. Determine how the ransomware was launched and under which account.  
3. Look for evidence of pre-staging activities, such as:  
   - Shadow copy deletion  
   - Discovery commands  
   - Archive or staging of data  
4. Attempt to identify the earliest point in time the attacker had access.  
5. Build a timeline from initial foothold (if visible) to mass encryption.  

---

## 4. Key Questions

- What is the likely initial access vector (if visible in the logs)?  
- Which account(s) were used to execute the ransomware?  
- Were backups or shadow copies deleted prior to encryption?  
- Is there any sign of exfiltration before encryption?  

---

## 5. Suggested Event IDs

- **Security**  
  - 4688 (process creation)  
  - 4624 / 4625 (logon / failed logon)  

- **Sysmon**  
  - 1 (process create)  
  - 11 (file create)  
  - 13 (registry value set)  

---

## 6. Deliverables

- Identification of the ransomware or destructive process.  
- Timeline of pre-staging and execution.  
- Impact summary (scope of affected data, accounts, and systems).  
- Recommendations for containment, eradication, and recovery.
