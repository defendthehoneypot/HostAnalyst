# Live Triage Field Guide (Windows Hosts)

Quick reference for on-host investigations during incidents.

---

## 1. Initial Triage

1. Confirm host identity:  
   - Hostname, IP, OS version.  
2. Identify active users:  
   - `whoami`  
   - `query user` or Task Manager (Users tab).  
3. Capture quick context:  
   - Recent alerts.  
   - Business role of the host (server vs. workstation, critical vs. non-critical).  

---

## 2. Process Triage

### Built-in

- Task Manager → sort by CPU, memory, and user.  
- `tasklist /v` for a quick dump of running processes.  

### Sysinternals

- **Process Explorer**:  
  - Look for:  
    - Suspicious names.  
    - Unusual parent–child relationships.  
    - Unsigned binaries in unusual paths.  
  - Check command line, company name, and path.  

Key questions:

- Does this process belong here?  
- Is the parent process normal for this child?  
- Does the command line make sense?  

---

## 3. Persistence Triage

Check common persistence locations:

- Services:  
  - `services.msc`  
  - `sc query` and `Get-Service`  

- Scheduled Tasks:  
  - `Task Scheduler` GUI  
  - `schtasks /query /fo LIST /v`  

- Run / RunOnce Keys:  
  - Use Autoruns (Logon, Scheduled Tasks, Services, Drivers, WMI tabs).  

- WMI Subscriptions (advanced):  
  - Sysmon Events 19, 20, 21 (if available).  

Look for odd names, non-standard paths, or tasks/services running from user-writable directories.

---

## 4. Network Triage

- `netstat -ano`  
- PowerShell: `Get-NetTCPConnection`  

Questions:

- Which processes own long-lived connections?  
- Any connections to unusual external IPs or countries?  
- Any high-numbered ports or non-standard protocols in use?  

If PCAP capture is allowed, consider `pktmon` or other range-approved tools.

---

## 5. Log Quick-Wins

Focus on:

- **Security**: 4624, 4625, 4672, 4688, 4769  
- **Sysmon**: 1 (Process Create), 3 (Network), 7 (Image Load), 10 (Process Access)  
- **PowerShell Operational**: suspicious script blocks, encoded commands  

Use Event Viewer or exported EVTX with better tools (EvtxECmd, Chainsaw) when possible.

---

## 6. Decide: Contain, Observe, or Escalate

After initial triage, answer:

- Is there clear evidence of active compromise?  
- Is this host likely the initial entry, a lateral movement hop, or a target?  
- Do we need immediate containment (network isolation, account disable)?  

Document:

- What you saw.  
- What you did.  
- What you recommend next.
