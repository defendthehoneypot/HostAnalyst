# Lab 05 — Multi-Host Enterprise Incident

---

## 1. Scenario

Multiple alerts have fired across several hosts in the enterprise: a workstation, an application server, and a domain controller. You are part of the incident response team and given access to each system in the range.

Your task is to reconstruct the full kill chain across all involved hosts.

---

## 2. Injects (Range Setup Notes)

Range operators should:

- Compromise an initial workstation via phishing or a simple dropper.  
- Perform privilege escalation and credential dumping on that host.  
- Use stolen credentials to move laterally to:  
  - An application or file server.  
  - A domain controller (for example, for DC discovery or persistence).  
- Place at least one persistence mechanism on a non-workstation host.  

---

## 3. Allowed Tools

Any tools available in previous labs, across multiple systems:

- Process Explorer, Autoruns, Task Manager.  
- PowerShell and CMD.  
- Event Viewer and EVTX exports.  
- Any EDR/monitoring dashboards provided in the range.

---

## 4. Analyst Tasks

1. Identify the initial point of compromise and initial vector (as best as logs allow).  
2. Track privilege escalation and credential theft on the first host.  
3. Map lateral movement from host to host.  
4. Identify any persistence mechanisms on high-value systems (servers, DCs).  
5. Determine the attacker’s likely objectives and whether they were achieved.  

---

## 5. Deliverables

- Per-host findings (workstation, server, DC).  
- End-to-end kill chain diagram or description.  
- List of compromised accounts, systems, and high-value assets touched.  
- Narrative (10–15 sentences) suitable for an executive incident summary.  
- Technical remediation and hardening recommendations.  
