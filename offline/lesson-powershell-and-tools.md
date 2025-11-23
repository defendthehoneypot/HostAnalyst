# Lesson — Querying Offline Windows Logs (PowerShell + Chainsaw + Hayabusa)

This lesson teaches analysts how to work with copied EVTX logs on an analysis workstation using:

- Native **PowerShell**
- **Chainsaw** (fast EVTX hunting, Sigma support)
- **Hayabusa** (Windows event log threat hunting)

Assumption: EVTX files are in a folder such as:

```text
C:\Cases\Scenario01\
  Security.evtx
  Sysmon.evtx
  PowerShell.evtx
  TaskScheduler.evtx
  Defender.evtx
```

---

## 1. PowerShell Against Offline EVTX

### 1.1 Basic: `Get-WinEvent -Path`

`Get-WinEvent` can read EVTX directly from disk using the `-Path` parameter:

```powershell
# List all events from Security log file
Get-WinEvent -Path "C:\Cases\Scenario01\Security.evtx"
```

This will be noisy. Add filters.

---

### 1.2 Filtering with `FilterHashtable`

Filter by event ID, provider, and time range:

```powershell
$path = "C:\Cases\Scenario01\Security.evtx"

# Example: process creation events (4688) in a specific time range
$start = Get-Date "2024-01-01T00:00:00"
$end   = Get-Date "2024-01-01T23:59:59"

Get-WinEvent -Path $path -FilterHashtable @{
    Id        = 4688
    StartTime = $start
    EndTime   = $end
} | Select-Object TimeCreated, Id, ProviderName, Message
```

Common filters:

- By **ID** only:

  ```powershell
  Get-WinEvent -Path $path -FilterHashtable @{ Id = 4624 }
  ```

- By **ProviderName**:

  ```powershell
  Get-WinEvent -Path "C:\Cases\Scenario01\Sysmon.evtx" `
    -FilterHashtable @{ ProviderName = "Microsoft-Windows-Sysmon" }
  ```

---

### 1.3 Quick Queries for Common Use Cases

#### a) Find RDP Logons (Security.evtx)

```powershell
$sec = "C:\Cases\Scenario01\Security.evtx"

Get-WinEvent -Path $sec -FilterHashtable @{ Id = 4624 } |
  Where-Object {
      $_.Properties[8].Value -eq 10   # LogonType = 10 (RDP)
  } |
  Select-Object TimeCreated,
                @{Name="TargetUser";Expression={$_.Properties[5].Value}},
                @{Name="IpAddress"; Expression={$_.Properties[18].Value}},
                Message
```

> Note: `Properties` indices depend on event schema; this is a common mapping for 4624.

---

#### b) Find LSASS Access (Sysmon.evtx, Event ID 10)

```powershell
$sys = "C:\Cases\Scenario01\Sysmon.evtx"

Get-WinEvent -Path $sys -FilterHashtable @{ Id = 10 } |
  Where-Object { $_.Message -like "*lsass.exe*" } |
  Select-Object TimeCreated, Id, Message
```

---

#### c) Find Encoded PowerShell (PowerShell.evtx)

```powershell
$pslog = "C:\Cases\Scenario01\PowerShell.evtx"

Get-WinEvent -Path $pslog |
  Where-Object { $_.Message -match "-enc " -or $_.Message -match "-EncodedCommand" } |
  Select-Object TimeCreated, Id, Message
```

---

### 1.4 Exporting to CSV for Further Analysis

```powershell
$sys = "C:\Cases\Scenario01\Sysmon.evtx"

Get-WinEvent -Path $sys -FilterHashtable @{ Id = 1 } |
  Select-Object TimeCreated, Id, ProviderName, Message |
  Export-Csv "C:\Cases\Scenario01\sysmon_1_process_create.csv" -NoTypeInformation
```

You can then analyze the CSV in Excel, Power BI, Jupyter, etc.

---

## 2. Chainsaw — Fast EVTX Hunting with Sigma

**Chainsaw** is a fast, open source EVTX hunting tool that can:

- Search EVTX with simple queries
- Apply **Sigma rules** to find known bad patterns
- Build quick timelines

(See the official Chainsaw GitHub repo for install instructions.)

Assume:

- Chainsaw is in `C:\Tools\chainsaw\chainsaw.exe`
- EVTX logs are in `C:\Cases\Scenario01\logs\`

---

### 2.1 Simple Search

```powershell
C:\Tools\chainsaw\chainsaw.exe search C:\Cases\Scenario01\logs `
  --term "lsass.exe"
```

This searches all EVTX in that directory for “lsass.exe” in event messages.

---

### 2.2 Timelining

```powershell
C:\Tools\chainsaw\chainsaw.exe timeline C:\Cases\Scenario01\logs `
  --output C:\Cases\Scenario01\chainsaw_timeline.csv
```

Open `chainsaw_timeline.csv` and sort/filter by time, event ID, etc.

---

### 2.3 Using Sigma Rules (If You Have Them)

If you have a Sigma ruleset and a mapping file:

```powershell
C:\Tools\chainsaw\chainsaw.exe hunt C:\Cases\Scenario01\logs `
  --rules   C:\Tools\chainsaw\rules\sigma `
  --mapping C:\Tools\chainsaw\mappings\sigma-windows-all.yml `
  --output  C:\Cases\Scenario01\chainsaw_hunt.csv
```

This flags events matching known attacker behaviors.

---

## 3. Hayabusa — Threat Hunting from EVTX

**Hayabusa** is an open source tool designed for hunting threats in Windows event logs. It:

- Parses logs and maps events to techniques
- Produces CSV output with severity and description
- Helps quickly triage what’s interesting

(See the official Hayabusa GitHub repo for install instructions.)

Assume:

- `hayabusa.exe` in `C:\Tools\hayabusa\`
- EVTX in `C:\Cases\Scenario01\logs\`

---

### 3.1 Basic CSV Output

```powershell
C:\Tools\hayabusa\hayabusa.exe csv `
  -d C:\Cases\Scenario01\logs `
  -o C:\Cases\Scenario01\hayabusa_results.csv
```

The CSV typically includes:

- Timestamp  
- Hostname  
- Event ID  
- Description  
- Severity / score  

You can quickly filter on high-severity hits.

---

### 3.2 Focused Time Window

If you know the compromise window:

```powershell
C:\Tools\hayabusa\hayabusa.exe csv `
  -d C:\Cases\Scenario01\logs `
  -o C:\Cases\Scenario01\hayabusa_window.csv `
  --start "2024-01-01T00:00:00" `
  --end   "2024-01-01T23:59:59"
```

---

## 4. Mini-Lab: Compare PowerShell vs Chainsaw vs Hayabusa

Pick any offline scenario (for example, `scenario-credential-dumping-mimikatz.md`):

1. **Using PowerShell**
   - Use `Get-WinEvent -Path` to:
     - Find the suspicious process.  
     - Identify user context and timestamps.  
   - Export relevant events to CSV.

2. **Using Chainsaw**
   - Run `timeline` to get a CSV of all events.  
   - Run `hunt` (if Sigma rules are available) to see what it flags.

3. **Using Hayabusa**
   - Run `csv` over the same EVTX set.  
   - Sort by severity in the output and see which events it prioritizes.

4. **Compare**
   - What did PowerShell show that the tools missed?  
   - What did Chainsaw/Hayabusa surface faster?  
   - How would you blend these approaches in a real incident?

Have the analyst document:

- Commands used  
- Top 5 most important events they found  
- A short reflection: *“If I only had one of these tools, which would I choose and why?”*
