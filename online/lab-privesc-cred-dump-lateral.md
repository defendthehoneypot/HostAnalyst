# Lab 02 — Privilege Escalation, Credential Dumping, and Lateral Movement

---

## 1. Scenario

EDR has alerted on possible credential dumping and unusual administrative logons from a workstation. You are given access to that host in the range.

Your task is to determine whether the alerts represent a true compromise, and if so, how far the attacker has gone.

---

## 2. Injects (Range Setup Notes)

Range operators should:

- Execute a tool or technique that accesses LSASS (for example, Mimikatz-like behavior).  
- Perform at least one lateral movement action from this host to another:  
  - RDP, PsExec, WMI, or remote service creation.  
- Optionally create a persistence mechanism as part of the attack.  

---

## 3. Allowed Tools

Same as Lab 01, plus any internal log or EDR consoles the environment provides.

---

## 4. Analyst Tasks

1. Identify processes that attempted to access LSASS.  
2. Determine the user context and privileges under which they ran.  
3. Identify any new services, tasks, or WMI subscriptions.  
4. Identify lateral movement:  
   - Outbound RDP connections  
   - Remote service creation  
   - Other remote management tools  
5. Build a multi-step narrative:  
   - Initial foothold (if visible from this host)  
   - Privilege escalation  
   - Credential dumping  
   - Lateral movement  

---

## 5. Deliverables

- List of key processes and events (with timestamps).  
- Identification of any compromised accounts.  
- Mapping of any lateral movement (source → destination hosts).  
- Short narrative (8–12 sentences).  
- Remediation recommendations.  

Evaluate using `../rubrics/scenario-rubric.md`.
