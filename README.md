# Process Execution → Network Activity Correlation

## Overview
This lab demonstrates correlating endpoint execution telemetry with network activity to evaluate behavioral intent.  
Rather than analyzing a single event in isolation, the objective is to determine whether execution led to external communication.

The focus is investigative reasoning — identifying relationships between events and explaining why combined activity increases scrutiny.

---

## Data Sources
- Windows process creation logs (Sysmon Event ID 1)
- Windows DNS Client operational log

---

## Observed Activity
A PowerShell process executed and was followed by DNS resolution and outbound HTTP communication to the same domain.

### Timeline
1. Process execution initiated
2. DNS query performed
3. Web request executed

### Process Lineage
The network activity originated from an interpreter process rather than a browser session.

---

## Analysis
Individually, each action may represent normal system behavior.  
However, the temporal sequence of execution followed by DNS resolution and web communication indicates scripted retrieval activity rather than interactive use.

Correlation increases investigative confidence because it demonstrates intent instead of isolated behavior.

---

## MITRE ATT&CK Mapping

| Behavior | Technique |
|------|------|
PowerShell execution | T1059.001
DNS communication | T1071.004
Web communication | T1071.001

---

## Detection Takeaway
Single events often produce low-confidence alerts.  
Linking execution telemetry to network behavior significantly improves signal quality and helps differentiate automation from normal user activity.

---

## Artifacts
Screenshots included:
- DNS query event
- Web request execution event
