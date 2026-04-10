# LogPoint Device Configuration

## Device Details
| Field | Value |
|---|---|
| Device Name | prasiddhi-kali |
| Device Address | <DEFENDER-IP> |
| Device Group | Linux |
| Time Zone | GMT+05:45 Kathmandu |
| Inactivity Threshold | 60 minutes |

## Processing Policy
| Field | Value |
|---|---|
| Policy Name | prasiddhi_policy |
| Normalization Policy | kali_linux |
| Enrichment Policy | None |
| Routing Policy | prasi_policy |

## Routing Policy (prasi_policy)
| Field | Value |
|---|---|
| Catch All | prasiddhi |
| Type | KeyPresent |
| Operation | Store raw message |

## Normalization Policy
Selected normalization packages:
- Unix Systemd
- Unix Syslog
- Unix System
- Common Unix System

## Log Forwarding Protocol
- Protocol: TCP
- Port: 514 (standard syslog)
- Tool: rsyslog
- Direction: Defender machine → LogPoint SIEM
