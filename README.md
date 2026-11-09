# SOC L1 Alert Triage — TryHackMe

A hands-on SOC Level 1 alert triage exercise completed in the TryHackMe SIEM dashboard.

> **Purpose:** Document the investigation workflow, evidence reviewed, alert classifications, and lessons learned. This is a learning portfolio project, not a production incident report.

## Lab overview

The room introduces the alert lifecycle and the responsibilities of a SOC L1 analyst:

1. Review and prioritise incoming alerts.
2. Assign an alert and move it to **In Progress**.
3. Review the alert description and supporting fields.
4. Investigate the activity and validate its legitimacy.
5. Set a verdict, write an evidence-based analyst comment, and close or escalate the alert.

**Room:** [SOC L1 Alert Triage — TryHackMe](https://tryhackme.com/room/socl1alerttriage)

## Skills practised

- Alert prioritisation by severity and age
- Alert ownership and status management
- Reviewing endpoint, network, and identity-related alert fields
- Distinguishing True Positives from False Positives
- Identifying suspicious file naming and download patterns
- Documenting investigation findings and recommendations

## Investigation summary

| Priority | Alert | Severity | Recorded verdict | Key observation |
|---|---|---:|---|---|
| 1 | Potential Data Exfiltration | Critical | True Positive | 5.8 GB sent to `*.zoom.us` from a meeting-room network |
| 2 | Double-Extension File Creation | High | True Positive | Chrome downloaded `cats2025.mp4.exe` from an untrusted domain |
| 3 | Unusual VPN Login Location | Medium | False Positive | User confirmed legitimate VPN access while travelling in Japan |

See the detailed reports in [`investigations/`](investigations/).

## Screenshots

### SIEM queue and priority context
![SIEM alert queue](screenshots/01-siem-alert-queue.png)

### Potential Data Exfiltration
![Potential Data Exfiltration triage](screenshots/02-potential-data-exfiltration-triage.png)

### Double-Extension File Creation
![Double extension triage](screenshots/03-double-extension-triage.png)

![Double extension alert evidence](screenshots/04-double-extension-alert-evidence.png)

### Final dashboard state
![Triage dashboard results](screenshots/05-triage-dashboard-results.png)

### Unusual VPN Login Location
![VPN login evidence](screenshots/06-unusual-vpn-login-evidence.png)

## Important evidence-quality note

The saved dashboard records the **Potential Data Exfiltration** alert as **True Positive**, but the analyst comment visible in the screenshot says the traffic appeared consistent with legitimate Zoom video-conferencing activity and that there was no clear evidence of exfiltration. Those statements do not support the same conclusion.

A real SOC analyst should not close this alert as a True Positive based only on the volume threshold, nor call it benign solely because the destination is Zoom. Validate the meeting/session context, user and device ownership, destination details, data classification, and business justification. Update the verdict and comment so they agree with the evidence. This repository preserves the dashboard's recorded verdict while explicitly documenting the inconsistency.

## Repository structure

```text
SOC-L1-Alert-Triage/
├── README.md
├── LICENSE
├── screenshots/
├── investigations/
│   ├── 01-potential-data-exfiltration.md
│   ├── 02-double-extension-file-creation.md
│   └── 03-unusual-vpn-login-location.md
└── methodology/
    └── alert-triage-process.md
```

## Flags

The uploaded screenshots do not show the three flags for this SOC L1 Alert Triage room, so no flag values are included here. Add them only after confirming the exact values in the TryHackMe room.

## Disclaimer

All activity was performed in the authorised TryHackMe training environment. Indicators and scenarios are reproduced for educational documentation. Do not access, download, or execute suspicious files outside an authorised, isolated lab.
