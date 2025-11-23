# Windows Host Analyst Training

This repository contains a complete training program for Windows host analysts, focused on:

- **Offline analysis** of exported logs and artifacts using public EVTX samples  
- **Online analysis** of live systems in an enterprise-like cyber range  

It is designed for incident response, threat hunting, and DFIR teams.

---

## Contents

- `docs/`  
  High-level curriculum overview and week-by-week plan  

- `offline/`  
  EVTX-based scenarios built using:  
  - https://github.com/sbousseaden/EVTX-ATTACK-SAMPLES  

- `online/`  
  Live range lab scenarios for host triage and multi-host incidents  

- `field-guides/`  
  Analyst pocket references for triage, EVTX analysis, and timelines  

- `rubrics/`  
  Scoring rubrics for labs and overall program evaluation  

---

## Training Tracks

### 1. Offline Analysis Track (Logs Only)

Analysts work only with exported logs and artifacts:

- EVTX (Security, Sysmon, PowerShell, TaskScheduler, Defender)
- Optional: MFT, registry hives, prefetch, Amcache

They learn to:

- Recognize attacker TTPs in logs  
- Correlate across channels  
- Build timelines and narratives  
- Write IR-style findings  

See: `offline/`

---

### 2. Online Analysis Track (Live Systems)

Analysts work in a simulated enterprise network (cyber range) and:

- Perform live triage (processes, services, tasks, WMI, network)  
- Identify persistence and C2  
- Track credential theft and lateral movement  
- Handle multi-host incident reconstruction  

See: `online/`

---

## Offline Log Query Lesson

The offline track includes a dedicated lesson on working with exported logs:

- Native **PowerShell** (`Get-WinEvent -Path`)  
- **Chainsaw** for fast EVTX hunting and Sigma-based detection  
- **Hayabusa** for threat hunting from Windows event logs  

See: `offline/lesson-powershell-and-tools.md`

---

## Intended Audience

- SOC analysts moving into IR/DFIR  
- Junior incident responders  
- Threat hunters needing stronger host-level skills  
- Red teamers who want to understand blue POV better  

---

## Getting Started

1. **Offline track**  
   - Read `offline/README.md`  
   - Clone or reference:  
     - https://github.com/sbousseaden/EVTX-ATTACK-SAMPLES  
   - Start with:  
     - `offline/lesson-powershell-and-tools.md`  
     - then `offline/scenario-credential-dumping-mimikatz.md`  

2. **Online track**  
   - Read `online/README.md`  
   - Adapt labs to your own range and tooling  

3. **Field guides**  
   - Print or keep handy:  
     - `field-guides/live-triage.md`  
     - `field-guides/evtx-analysis.md`  
     - `field-guides/timelines.md`  

4. **Evaluation**  
   - Use `rubrics/scenario-rubric.md` for individual labs  
   - Use `rubrics/program-evaluation.md` for course completion  

---

## License and Attribution

- EVTX attack samples are from:  
  - https://github.com/sbousseaden/EVTX-ATTACK-SAMPLES  

Adapt and extend this curriculum as needed for your org.
