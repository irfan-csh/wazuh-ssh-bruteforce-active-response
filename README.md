# Wazuh SSH Brute Force Detection & Automated Response

## Project Overview

This project demonstrates the design and implementation of a Security Information and Event Management (SIEM) use case using Wazuh for detecting and responding to SSH brute-force attacks in a Linux environment.

The lab simulates a real-world attack scenario where repeated SSH authentication failures are generated from an attacker machine and monitored by Wazuh. A custom detection rule correlates multiple failed authentication events within a specified timeframe, generates a high-severity security alert, maps the activity to the MITRE ATT&CK framework, and automatically initiates an Active Response action to block the attacker's IP address.

This project showcases key Security Operations Center (SOC) functions including log analysis, detection engineering, threat detection, alert correlation, incident investigation, and automated containment.

---

## Objectives

- Monitor SSH authentication activity on a Linux endpoint.
- Detect repeated failed authentication attempts indicative of brute-force attacks.
- Develop a custom Wazuh correlation rule for enhanced threat detection.
- Map detected activity to the MITRE ATT&CK framework.
- Implement automated incident response using Wazuh Active Response.
- Validate endpoint containment through firewall-based IP blocking.
- Simulate a realistic SOC detection and response workflow.

---

## Lab Architecture

```text
Kali Linux (Attacker)
        │
        ▼
Ubuntu Server (Wazuh Agent)
        │
        ▼
Wazuh Manager (Docker Deployment)
        │
        ▼
Custom Detection Rule
        │
        ▼
Security Alert (MITRE ATT&CK T1110)
        │
        ▼
Active Response (firewall-drop)
        │
        ▼
Attacker IP Blocked
```

---

## Technologies Used

### Operating Systems
- Ubuntu Linux
- Kali Linux

### Security Platform
- Wazuh SIEM

### Security Concepts
- Log Analysis
- Threat Detection
- Detection Engineering
- Security Monitoring
- Incident Response
- Active Response
- MITRE ATT&CK Mapping

### Network Services
- OpenSSH

### Firewall Technology
- iptables

---

## Attack Simulation

The attack scenario consisted of generating repeated SSH authentication failures from a Kali Linux system targeting an Ubuntu server.

Wazuh collected authentication logs from the endpoint and analyzed the events using built-in and custom detection rules. Once the predefined threshold was exceeded, Wazuh generated a high-severity alert and automatically executed an Active Response action to block the attack source.

---

## Detection Logic

### Built-in Detection

Wazuh monitored SSH authentication logs and identified repeated failed login attempts through its native SSH authentication rules.

### Custom Correlation Rule

A custom rule was developed to identify potential brute-force attacks by correlating multiple authentication failure events within a defined timeframe.

**Detection Criteria**

- Multiple failed SSH authentication attempts
- Event correlation within 120 seconds
- Elevated severity level
- MITRE ATT&CK mapping applied

---

## MITRE ATT&CK Mapping

| Tactic | Technique | ID |
|----------|----------|----------|
| Credential Access | Brute Force | T1110 |

The detected activity was mapped to MITRE ATT&CK Technique T1110 (Brute Force), providing standardized threat classification and improved incident context.

---

## Automated Response

To enhance incident containment, Wazuh Active Response was configured using the `firewall-drop` script.

### Response Workflow

1. Multiple SSH authentication failures detected.
2. Custom brute-force detection rule triggered.
3. High-severity security alert generated.
4. Active Response executed automatically.
5. Source IP address blocked through iptables.
6. Endpoint protected from further unauthorized attempts.

---

## Investigation Process

The following workflow was performed during the investigation:

- Review SSH authentication logs.
- Analyze generated Wazuh alerts.
- Identify attacker IP address.
- Validate rule correlation and alert severity.
- Verify MITRE ATT&CK classification.
- Confirm Active Response execution.
- Validate firewall-based containment.

---

## Key Features

- SSH Brute Force Detection
- Custom Detection Engineering
- Event Correlation
- MITRE ATT&CK Integration
- Automated Incident Response
- Endpoint-Level Containment
- Firewall-Based IP Blocking
- SOC-Oriented Investigation Workflow

---

---

## Learning Outcomes

Through this project, the following skills and concepts were developed:

- Security event monitoring using Wazuh.
- Linux authentication log analysis.
- Detection engineering using custom Wazuh rules.
- Security alert correlation and prioritization.
- MITRE ATT&CK framework implementation.
- Incident investigation and threat analysis.
- Active Response configuration and validation.
- Firewall-based attack containment.
- Security Operations Center (SOC) workflow understanding.
- Real-world brute-force attack detection and response techniques.

---

## Conclusion

This project demonstrates a practical SOC use case for detecting and responding to SSH brute-force attacks using Wazuh. By combining custom detection logic, MITRE ATT&CK mapping, automated response capabilities, and endpoint-level containment, the solution provides an effective approach for identifying and mitigating unauthorized access attempts in a Linux environment.

The implementation reflects key responsibilities commonly performed by SOC Analysts, including monitoring, detection, investigation, threat classification, and incident response.
