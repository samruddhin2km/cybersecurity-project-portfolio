# Cybersecurity Project Portfolio

This repository documents my experience working in enterprise Security Operations and Security Control Administration (SCA). It highlights practical work across multiple security platforms including Data Loss Prevention, Threat Hunting, SOAR automation, Vulnerability Management, SIEM administration, and enterprise security tools.

The objective of this repository is to provide an overview of real-world cybersecurity operations, security platform administration, compliance verification, and incident investigation activities performed in an enterprise environment.

## Table of Contents

1. [Data Loss Prevention (Forcepoint DLP)](#1-data-loss-prevention-forcepoint-dlp)
2. [Threat Hunting](#2-threat-hunting)
3. [SOAR Automation](#3-soar-automation)
4. [Vulnerability Management](#4-vulnerability-management)
5. [SIEM Administration](#5-siem-administration)
6. [Security Control Administration](#6-security-control-administration)

## 1. Data Loss Prevention (Forcepoint DLP)

### Overview
As part of the Security Control Administration (SCA) function, I was responsible for the administration, monitoring, and operational management of the Forcepoint Data Loss Prevention (DLP) platform. The role involved policy governance, infrastructure monitoring, and ensuring that enterprise data protection policies were enforced effectively across endpoints and network channels.

The responsibilities included both day-to-day operational security tasks as well as platform lifecycle management activities such as compliance reviews, incident investigations, and upgrade validations.

---

### Security Policy Administration

A key responsibility involved managing and governing DLP policies based on requests escalated through the enterprise service management system.

Typical activities included:

- Evaluating requests for **policy creation, modification, or removal**.
- Configuring policies for specific **users, groups, or business units** based on business requirements.
- Ensuring all policy implementations aligned with:
  - Enterprise security architecture guidelines
  - Regulatory and compliance requirements
  - Organizational data classification standards

Each request required careful evaluation to ensure that any changes did not introduce **potential data exfiltration risks or security gaps**.

---

### Operational Monitoring and Incident Investigation

The Forcepoint Security Manager (FSM) dashboard was continuously monitored to ensure that all DLP components were functioning properly.

Operational monitoring included:

- Reviewing the status of DLP components such as protectors, policy engines, and endpoint communication.
- Investigating component failures or service interruptions through system alerts and logs.
- Referring to vendor documentation and knowledge base resources for troubleshooting.
- Performing remediation actions when required, including upgrades of DLP protectors within the FSM infrastructure.

---

### Platform Compliance and Policy Integrity Review

Periodic governance checks were conducted to ensure that the DLP platform maintained proper policy enforcement and compliance alignment.

These reviews included:

- Verifying that **all active DLP rules and policies were correctly configured and justified**.
- Reviewing **temporary policy exceptions** created through service requests.
- Ensuring that temporary access rules were **removed after their intended purpose was fulfilled**.
- Analyzing **firewall and policy enforcement logs** to identify potential unauthorized bypass attempts.

Because certain temporary policy exceptions do not automatically expire within the platform, manual verification and log review were required to ensure that no unnecessary rules remained active.

---

### Forcepoint Platform Upgrade Validation

Before performing upgrades to the Forcepoint Security Manager platform, a structured validation process was performed to ensure that existing policies and integrations would continue functioning correctly after the upgrade.

Validation testing included:

- Testing DLP policies against sensitive data patterns to confirm proper rule triggering.
- Validating policy enforcement on **Windows endpoint agents**.
- Verifying compatibility and policy behavior on **macOS endpoints**.
- Simulating policy enforcement across various data channels including:
  - Email attachments
  - Web uploads
  - Removable media
  - Cloud-based file transfers
- Confirming that violations generated proper **security incidents and alerts** within the system.

These validation steps ensured that platform upgrades could be performed safely without disrupting existing data protection mechanisms.

---

### Endpoint Agent Deployment and Upgrade Management

As part of platform lifecycle management, endpoint agent upgrades were also coordinated across enterprise systems.

Key activities included:

- Scheduling deployment activities through the **enterprise change management process**.
- Planning upgrade timelines to minimize operational impact on end users.
- Executing enterprise-wide deployment of updated **Forcepoint DLP endpoint agents**.
- Monitoring deployment progress and verifying successful installation across systems.
- Ensuring endpoint agents maintained proper communication with the **Forcepoint Security Manager (FSM)** after the upgrade.
- Performing post-deployment validation to confirm continued **policy enforcement and incident generation**.

These activities ensured that the enterprise DLP infrastructure remained **stable, up-to-date, and compliant with organizational security standards**.


---

## 2. Threat Hunting

### Overview
As part of proactive security operations, I performed targeted threat hunting exercises to identify potential indicators of compromise (IoCs) and adversary techniques within the enterprise environment. These hunts were designed to proactively detect malicious activity that may bypass traditional alerting mechanisms.

The threat hunting methodology used was **TAHITI (Targeted Hunting Integrated Threat Intelligence)**, which combines threat intelligence with targeted log analysis and adversary behavior mapping.

Threat hunts focused on adversaries that are known to target financial and fintech organizations, including ransomware operators and financially motivated cybercrime groups.

Two notable threat hunting exercises conducted were based on **FIN7** and **Akira ransomware** activity patterns.

---

### FIN7 Threat Hunt

FIN7 is a financially motivated cybercrime group known for targeting financial institutions and organizations handling sensitive financial data. Due to the relevance of this threat actor to fintech environments, a dedicated threat hunt was conducted.

Activities included:

- Mapping relevant **MITRE ATT&CK techniques** associated with FIN7 activity.
- Developing multiple hunting use cases based on known attacker behaviors.
- Querying enterprise logs to identify potential indicators of compromise.
- Reviewing authentication events, process executions, and network activity associated with the mapped techniques.
- Correlating findings with available threat intelligence.

The analysis did not reveal any suspicious activity related to FIN7 techniques in the monitored environment.

Although no malicious indicators were found, these proactive hunts are critical for validating the effectiveness of existing security controls and ensuring that the environment remains resilient against emerging threats.

All findings and methodologies were documented for future reference and threat monitoring improvements.

---

### Akira Ransomware Threat Hunt

Akira ransomware is a threat actor known for targeting enterprise environments and leveraging various tools and techniques for initial access, lateral movement, and data exfiltration.

A targeted hunt was performed to evaluate whether any behaviors associated with Akira activity were present within the environment.

During the investigation:

- System and network logs were analyzed to identify suspicious behaviors aligned with known Akira tactics.
- Particular focus was placed on tools commonly used for remote access and file transfer.

The investigation identified several systems where remote access tools such as **AnyDesk** and **TeamViewer** were installed. These applications can potentially enable features such as automated VPN connectivity and network tunneling, which could be abused for unauthorized access or data exfiltration.

Although no systems were compromised, these findings highlighted a **potential risk surface** within the environment.

Additional observations included the presence of **file transfer utilities** such as:

- FileZilla
- WinSCP

These tools can be used for encrypted file transfers and therefore require monitoring to prevent unauthorized data movement.

---

### Security Improvements and Alerting Enhancements

Based on the findings from the Akira threat hunt, several security monitoring improvements were proposed and implemented:

- Creation of alerting mechanisms for **network events involving remote access tools communicating with suspicious or malicious IP addresses**.
- Monitoring for potential **command-and-control (C2) communication patterns** involving AnyDesk and TeamViewer.
- Implementation of monitoring controls for **encrypted file transfers using FileZilla** to detect potential data exfiltration activity.

These improvements strengthened the organization’s ability to detect suspicious activity related to ransomware operations and unauthorized data transfer attempts.

---

### Outcome

The threat hunting exercises confirmed that:

- No systems were compromised by FIN7 or Akira-related activity.
- Existing security controls were effective in preventing known attack patterns.
- Additional monitoring controls could further enhance early detection capabilities.

Proactive threat hunting plays a critical role in validating security posture, identifying potential attack surfaces, and improving defensive monitoring capabilities even when no immediate indicators of compromise are detected.
