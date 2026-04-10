# SIEM Threat Detection Project — LogPoint

## Overview
A hands-on cybersecurity project completed during my internship at **Monal Tech**.
Configured a LogPoint SIEM environment, forwarded real-time logs from Kali Linux
using rsyslog, built custom detection rules using LEQL, and simulated real attacks
to validate the detection pipeline.

## 🛠️ Skills Demonstrated
- SIEM Configuration & Administration (LogPoint)
- Log Forwarding via rsyslog (TCP/UDP port 514)
- Detection Engineering (LEQL query language)
- Attack Simulation (Hydra brute-force, Nmap scanning)
- Incident Analysis & Security Reporting
- Blue Team / SOC Analyst Workflow

## 🖥️ Lab Environment

| Machine | Role | IP |
|---|---|---|
| Kali Attacker | Threat Actor | 192.168.0.122 |
| Kali Defender | Victim / Log Source | 192.168.0.92 |
| LogPoint SIEM | Log Collector & Analyzer | 192.168.0.9 |

## ⚔️ Attacks Simulated & Detected

| # | Attack | Tool | MITRE ATT&CK | Alert Triggered | Result |
|---|---|---|---|---|---|
| 1 | SSH Brute Force | Hydra | T1110.001 | Authentication_Failure | 28 failed attempts detected |
| 2 | Network Port Scan | Nmap | T1046 | LP_Possible Port Scan Detected | 21,290 ports scanned — caught in 1 min |

## Repository Structure
├── report/                  # Full internship report (PDF)
├── detection-rules/         # Custom LEQL alert queries
│   ├── auth_failure.leql
│   └── high_requests.leql
├── configs/                 # rsyslog forwarding configuration
└── diagrams/                # Network topology diagram

## 🔍 Key Findings

**Finding 1 — SSH Brute Force (High Severity)**
- Tool: Hydra with rockyou.txt wordlist
- Result: 28 failed SSH login attempts from 192.168.0.115
- Detection: LogPoint triggered Authentication_Failure alert within 2 minutes
- Fix: Implement fail2ban, enforce key-based SSH auth, account lockout after 5 attempts

**Finding 2 — Network Port Scan (Medium Severity)**
- Tool: Nmap default scan
- Result: 135,288 log events generated in 5 minutes; 21,290 unique ports probed in 1 minute
- Detection: Both custom High Requests alert and built-in LP_Possible Port Scan alert triggered
- Fix: Enable port knocking, rate-limit connections, block unused ports

## 📄 Report
See `/report/logpoint_task_report.pdf` for the full technical report including
methodology, findings, and recommendations.

## ⚠️ Disclaimer
This project was conducted in a controlled, isolated lab environment for
educational purposes only. All testing was performed on machines I own and
operate. No unauthorized systems were accessed.
