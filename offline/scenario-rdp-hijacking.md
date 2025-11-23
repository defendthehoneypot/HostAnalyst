# Scenario 02 — RDP Hijacking and Lateral Movement

---

## 1. Description

Unusual remote desktop activity was observed targeting an internal workstation and an internal server. There are concerns that an attacker may have hijacked an existing RDP session or used stolen credentials for lateral movement.

You are given event logs from one affected host.

---

## 2. Artifacts Provided

- `Security.evtx`  
- `Sysmon.evtx`  

Use an appropriate RDP-related sample from:

- https://github.com/sbousseaden/EVTX-ATTACK-SAMPLES  

---

## 3. Analyst Tasks

1. Identify suspicious RDP logons and sessions.  
2. Determine which accounts were used and from which source addresses.  
3. Identify any signs of privilege escalation on the host.  
4. Correlate RDP activity with process creation and service creation, if any.  
5. Determine whether this host appears to be:  
   - The initial victim  
   - A lateral movement hop  
   - A high-value target reached later in the chain  
6. Build a timeline of key events.  
7. Provide a narrative explaining likely attacker goals and next steps.

---

## 4. Key Questions

- Which logon events appear suspicious, and why?  
- Are there signs of session hijacking or re-use of an existing session?  
- Did the attacker create new local users, services, or scheduled tasks?  
- What other hosts appear in the RDP source or destination fields?

---

## 5. Suggested Event IDs

- **Security**  
  - 4624 / 4625 (logon / failed logon)  
  - Focus on LogonType 10 (RDP)  

- **Sysmon**  
  - 1 (process create)  
  - 3 (network connections)  
  - 7 (image loaded, if relevant)  

---

## 6. Deliverables

- Annotated list of suspicious logon events.  
- Timeline of events tying RDP sessions to other activity.  
- Narrative summary (5–10 sentences).  
- Remediation recommendations (for example, RDP restrictions, MFA, monitoring).
