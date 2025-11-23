# Offline Analysis Track (EVTX-Based)

This directory contains offline scenarios built around Windows event logs, using samples from:

- https://github.com/sbousseaden/EVTX-ATTACK-SAMPLES

Analysts receive only logs and artifacts — no live access to hosts.

---

## Workflow

For each scenario:

1. Read the scenario file (for example, `scenario-credential-dumping-mimikatz.md`).  
2. Load the indicated EVTX logs into your preferred tools.  
3. Answer the questions and produce the requested deliverables.  
4. Grade the results using `../rubrics/scenario-rubric.md`.  

---

## Lessons

- [Using PowerShell, Chainsaw, and Hayabusa](lesson-powershell-and-tools.md)

---

## Scenarios Included

- `scenario-credential-dumping-mimikatz.md`  
- `scenario-rdp-hijacking.md`  
- `scenario-wmi-persistence.md`  
- `scenario-scheduled-task-backdoor.md`  
- `scenario-powershell-malicious-execution.md`  
- `scenario-lolbins-abuse.md`  
- `scenario-ransomware-prestaging.md`  

You can add more scenarios by copying `scenario-template.md`.
