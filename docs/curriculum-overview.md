# Curriculum Overview

This curriculum prepares Windows host analysts to:

- Distinguish normal vs. abnormal behavior on Windows hosts  
- Detect credential theft, persistence, and lateral movement  
- Work both with live systems and exported logs/artifacts  
- Build clear, defensible incident narratives  

---

## Learning Objectives

By the end of the program, analysts should be able to:

### 1. Live System Triage

- Identify suspicious processes, services, tasks, and WMI subscriptions  
- Use built-in Windows tools and Sysinternals to investigate quickly  
- Identify and confirm suspected C2 and data exfiltration activity  

### 2. Offline Log and Artifact Analysis

- Parse Windows Security, Sysmon, PowerShell, TaskScheduler, and Defender logs  
- Recognize patterns associated with common TTPs  
- Correlate events across hosts and log sources  
- Build detailed timelines using MFT, registry, prefetch, etc.  

### 3. Narrative Building and Reporting

- Turn raw events into a clear “what happened” story  
- Identify compromised accounts and systems  
- Propose concrete remediation and hardening actions  

---

## Training Tracks

- **Offline Track**  
  Scenarios based on EVTX attack samples. Emphasis on logs and artifacts, no live host access.

- **Online Track**  
  Live cyber range scenarios. Emphasis on triage, speed, and decision-making.

Each track includes labs, guided exercises, and graded scenarios.

---

## Prerequisites

- Basic familiarity with:  
  - Windows operating system concepts  
  - Command line and PowerShell  
  - Networking fundamentals (TCP/IP, ports, protocols)  

- Optional but helpful:  
  - Prior SOC experience  
  - Exposure to SIEM/EDR tools  

---

## Materials

- This repository (curriculum, labs, guides, rubrics)  
- EVTX samples:  
  - https://github.com/sbousseaden/EVTX-ATTACK-SAMPLES  
- A Windows-based cyber range (for the online track)
