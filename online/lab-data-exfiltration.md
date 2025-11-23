# Lab 04 — Data Exfiltration Simulation

---

## 1. Scenario

Network monitoring has flagged a workstation for possible data exfiltration over HTTPS. You are given access to that host in the range.

Your job is to determine whether data exfiltration occurred, and if so, how.

---

## 2. Injects (Range Setup Notes)

Range operators should:

- Use a script or tool on the host to:  
  - Archive data into a file (for example, with 7zip or `rar.exe`).  
  - Transmit that archive to a remote HTTP or HTTPS endpoint at a realistic rate.  
- Optionally leave artifacts in temporary or staging directories.  

---

## 3. Allowed Tools

- File system inspection (Explorer, PowerShell, CMD).  
- Process and network inspection (Task Manager, Process Explorer, TCPView, `Get-NetTCPConnection`).  
- Event Viewer and any available EDR.

---

## 4. Analyst Tasks

1. Identify processes that accessed large volumes of files or created archive files.  
2. Locate any staged archives or temporary data stores.  
3. Identify outbound connections associated with the suspected exfiltration.  
4. Estimate (from logs and artifacts) what kind of data was likely taken.  
5. Link exfiltration activity to specific user accounts and processes.  

---

## 5. Deliverables

- Identification of the exfiltration tool or process.  
- Description of how data was staged and transmitted.  
- Approximate scope of affected data (types, locations, sensitivity where known).  
- Narrative (8–12 sentences) and recommendations for detection and prevention.  
