# Incident Investigation Using the Splunk BOTS Dataset

## Objective
Investigate suspicious activity against a web server in the BOTS v1 dataset
using Splunk, correlate events across log sources, and document the attack
sequence, findings, and indicators of compromise (IOCs).

## Tools
Splunk Enterprise, SPL, BOTS v1 dataset (Suricata, stream:http, IIS,
FortiGate, Sysmon logs)

## Investigation Evidence Screenshots

### 1. Shellshock Investigation
![Shellshock Investigation](screenshots/ShellShock-investigation.png)

### 2. Brute-Force Investigation
![Brute-Force Investigation](screenshots/brute-force-investigation.png)

### 3. Incident Timeline
![Incident Timeline](screenshots/incident-timeline.png)

## What I did
- Scoped the dataset (955,807 events, 22 sourcetypes)
- Identified high-priority Suricata alerts and the suspicious source IP
- Confirmed an Acunetix vulnerability scan and CVE-2014-6271 (Shellshock)
  exploit attempts from 40.80.148.42
- Found a second IP (23.22.63.114) sending 412 POST requests to the Joomla
  admin login, indicating a brute-force attempt
- Correlated the attacker IP across 8 log sources and built an incident
  timeline and IOC list

## Key findings
- Scanning, exploit attempts, and brute-force attempts: confirmed
- Successful compromise: not confirmed by the evidence reviewed

## Limitations
Sysmon events mentioning the attacker IP were not analysed. HTTP status
codes alone could not show whether any login succeeded.

## Report
See the PDF in this repository for the full investigation with screenshots.
