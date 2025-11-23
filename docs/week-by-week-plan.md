# Week-by-Week Training Plan

This plan assumes a 4-week program with flexibility to compress or extend.

---

## Week 1 — Foundations + Offline EVTX Skills

**Goals**

- Understand Windows logging and key channels  
- Start recognizing basic attacker patterns in EVTX  

**Topics**

- Windows architecture basics (processes, services, registry, tasks)  
- Event log structure and channels:  
  - Security, Sysmon, PowerShell, TaskScheduler, Defender  
- Intro to EVTX tools:  
  - EvtxECmd, Chainsaw, Event Viewer, etc.  

**Labs**

- Offline:  
  - Walkthrough using a simple EVTX sample from the attack repo  
- Homework:  
  - One small scenario using `offline/scenario-credential-dumping-mimikatz.md`  

---

## Week 2 — Full Offline Reconstruction

**Goals**

- Correlate across log channels  
- Build incident timelines and narratives  

**Topics**

- Multi-channel correlation patterns  
- Common TTP patterns in logs:  
  - Credential dumping, persistence, lateral movement, ransomware  
- Introduction to timeline tools (optional):  
  - Plaso, Timesketch, MFTECmd, etc.  

**Labs**

- Offline:  
  - `offline/scenario-rdp-hijacking.md`  
  - `offline/scenario-wmi-persistence.md`  
  - `offline/scenario-scheduled-task-backdoor.md`  
- Evaluation:  
  - Use `rubrics/scenario-rubric.md` for at least one graded scenario  

---

## Week 3 — Live System Triage

**Goals**

- Build confidence in on-host investigations under time pressure  

**Topics**

- Process and memory inspection  
- Services, scheduled tasks, and WMI persistence  
- Network connection triage  
- When and how to capture memory or additional artifacts  

**Labs**

- Online (range):  
  - `online/lab-basic-foothold.md`  
  - `online/lab-privesc-cred-dump-lateral.md`  

---

## Week 4 — Full Enterprise Incident

**Goals**

- Combine live triage and offline analysis  
- Handle multi-host incidents  

**Topics**

- Multi-host kill chain reconstruction  
- Coordinating findings across analysts  
- Final reporting and recommendations  

**Labs**

- Online:  
  - `online/lab-powershell-intrusion.md`  
  - `online/lab-data-exfiltration.md`  
  - `online/lab-multihost-investigation.md`  
- Capstone:  
  - Choose one online lab and extract logs for offline reconstruction  
  - Grade using `rubrics/program-evaluation.md`
