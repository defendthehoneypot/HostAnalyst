# Lab 01 — Basic Foothold Discovery

---

## 1. Scenario

Blue team has received an alert that a single workstation may have been compromised by malware. No additional context is provided. You are given remote access to this host in the training range.

Your goal is to identify whether there is an active foothold, and if so, characterize it.

---

## 2. Injects (Range Setup Notes)

Range operators should:

- Deploy a suspicious binary or script.  
- Create a persistence mechanism (for example, scheduled task or service).  
- Optionally simulate outbound C2 via a periodic network connection.  

Details of the implementation are hidden from the analyst.

---

## 3. Allowed Tools

- Built-in:  
  - Task Manager  
  - Event Viewer  
  - PowerShell, CMD  

- Sysinternals:  
  - Process Explorer  
  - Autoruns  
  - TCPView (optional)  

- Other:  
  - Any internal EDR or monitoring tools available in the range  

---

## 4. Analyst Tasks

1. Identify suspicious processes:  
   - Unusual names  
   - Suspicious parent or child relationships  
   - Odd command lines  

2. Identify persistence mechanisms:  
   - Services  
   - Scheduled tasks  
   - Run or RunOnce registry keys  
   - WMI subscriptions (if applicable)  

3. Identify outbound network connections that may be C2:  
   - Long-lived or periodic connections  
   - Destinations outside normal ranges  

4. Capture:  
   - Relevant process details (name, PID, PPID, hash if possible)  
   - Persistence configuration  
   - Network endpoints  

5. Provide a short narrative:  
   - What is the foothold?  
   - How is it started?  
   - How does it communicate?  

---

## 5. Deliverables

- List of suspicious processes and why they are suspicious.  
- Description of discovered persistence.  
- Description of suspicious network connections.  
- A 5–10 sentence narrative summarizing the compromise.  

Use `../rubrics/scenario-rubric.md` to evaluate.
