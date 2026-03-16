# Cybersecurity Project Portfolio

This repository documents my experience working in enterprise Security Operations and Security Control Administration (SCA). It highlights practical work across multiple security platforms including Data Loss Prevention, Threat Hunting, SOAR automation, Vulnerability Management, SIEM administration, and enterprise security tools.

The objective of this repository is to provide an overview of real-world cybersecurity operations, security platform administration, compliance verification, and incident investigation activities performed in an enterprise environment.

## Table of Contents

1. [Data Loss Prevention (Forcepoint DLP)](#1-data-loss-prevention-forcepoint-dlp)
2. [Threat Hunting](#2-threat-hunting)
3. [SOAR Automation](#3-soar-automation)
4. [Vulnerability Management](#4-vulnerability-management)
5. [Security Control Administration](#5-security-control-administration)

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


---

## 3. SOAR Automation

### Overview

As part of Security Operations, I independently designed and implemented multiple incident response playbooks within the **D3 Security SOAR platform**. These playbooks automated key steps in incident triage, enrichment, investigation, and response to improve response time and standardize investigation workflows.

Each playbook incorporated automation for:

- Capturing incident timestamps to measure **TTD (Time to Detect)** and **TTR (Time to Respond)**
- Extracting indicators of compromise (IoCs)
- Performing threat intelligence enrichment
- Gathering contextual information from enterprise systems
- Supporting analyst decision-making for remediation and incident closure

The automation significantly improved investigation efficiency while maintaining consistency across different security incident types.

---

### Cyber Fraud Investigation Playbook

This playbook was designed to investigate incidents related to **cyber fraud and brand abuse** affecting the organization.

Key investigation steps included:

- Capturing incident timestamps for TTD and TTR metrics.
- Classifying incidents into categories such as:
  - Phishing attempts
  - Spoofed profiles
  - Malicious mobile applications
  - Brand misuse
- Identifying threat vectors such as:
  - Impersonating domains
  - Spoofed social media profiles
  - Email-based attacks
  - Malicious mobile applications
- Enriching investigation data using:
  - Active Directory (AD)
  - WHOIS records
  - VirusTotal intelligence
- Determining whether incidents represented **true positives or false positives**.
- Initiating remediation actions either manually or through automation depending on tool capabilities.
- Documenting findings and closing the incident ticket.

---

### DDoS Investigation Playbook

A dedicated playbook was created to support automated investigation of **Distributed Denial-of-Service (DDoS) alerts**.

The workflow included:

- Capturing TTD and TTR metrics.
- Extracting indicators of compromise such as:
  - Source IP addresses
  - Destination IP addresses
  - Company public IP ranges
- Enriching indicators using **AbuseIPDB** and other threat intelligence sources.
- Determining whether alerts originated from monitoring platforms such as:
  - Akamai priority alerts
  - LogicMonitor DoS alerts
- Assessing whether business services were impacted.
- Supporting remediation actions including:
  - Blocking malicious traffic
  - Investigating additional mitigation strategies if traffic blocking was insufficient.

---

### Malware Investigation Playbook

This playbook automated initial triage and investigation of malware-related alerts.

Key activities included:

- Identifying the **alert source and context**.
- Enriching investigation data using OSINT sources such as VirusTotal.
- Retrieving **Active Directory user details** associated with the affected system.
- Collecting **process activity and system behavior** data from endpoints.
- Correlating related alerts from security platforms including:
  - Microsoft ATP
  - Microsoft 365 security alerts
- Executing **Microsoft 365 hunting queries** to retrieve endpoint activity.
- Exporting investigation results and attaching them to incident records for documentation.
- Categorizing the activity as:
  - Malicious
  - Suspicious
  - Potentially unwanted process execution
- Checking whether related activity was associated with existing **service requests in ServiceNow** to identify legitimate operational activity.
- If malicious activity was confirmed:
  - Identifying whether sensitive data may have been involved.
  - Conducting further investigation through sandbox dynamic analysis.
  - Performing deeper analysis using a forensic investigation workstation.

---

### DLP Investigation Playbook

A dedicated playbook was created to automate investigations related to **Data Loss Prevention incidents**.

The workflow included:

- Integrating with **Forcepoint Security Manager (FSM)** to retrieve event details.
- Collecting contextual information about suspected data transfer attempts.
- Categorizing the method of attempted data transfer such as:
  - Email
  - Web browser
  - USB storage
  - Cloud applications
  - Chat platforms
  - Printing activity
- Determining whether data transfer attempts were **blocked or successful**.
- Assigning incident priority based on risk level.
- Supporting remediation actions including **policy adjustments or enforcement verification**.

---

### Additional Playbooks Implemented

In addition to the core playbooks above, several other automated investigation workflows were developed to support security operations, including:

- Unusual behavior investigation
- Potential hacking activity alerts
- Data leakage incidents
- Phishing investigations
- Zero-day incident response workflows

These playbooks helped standardize incident response processes across multiple security scenarios.

---

### Custom Automation Scripts

To support these playbooks, multiple custom scripts were developed within the SOAR platform to automate enrichment and data processing tasks.

Examples of automation capabilities included:

- Identifying whether users belonged to specific **Active Directory groups**.
- Summarizing **AD sign-in events** based on:
  - Application
  - Logon type
  - Device name
  - Operating system
  - Authentication method
  - Source IP address
  - Geographic location
- Retrieving the **last password change timestamp** for user accounts.
- Identifying **critical vulnerabilities present on assets**.
- Retrieving process activity data from endpoint systems.
- Summarizing **device file activity events**.
- Extracting unique values from structured data fields.
- Searching email activity based on:
  - Sender
  - Recipient
  - Subject
- Parsing URLs and extracting relevant indicators using string processing techniques.

These automation scripts significantly enhanced the efficiency of the investigation workflows by reducing manual analysis effort and enabling faster incident triage.

---

### Outcome

The implementation of these SOAR playbooks helped achieve:

- Faster incident triage and investigation.
- Standardized investigation procedures across different incident types.
- Improved efficiency in enrichment and threat intelligence correlation.
- Reduced manual effort for security analysts.
- Better documentation and tracking of incident response activities.


---

## 4. Vulnerability Management

### Overview

As part of Security Operations, I was responsible for supporting the vulnerability management process across enterprise systems. The objective of this process was to continuously identify security weaknesses in infrastructure and coordinate remediation before they could be exploited.

Vulnerability discovery and analysis were performed using **Tenable Nessus**, with separate scanning platforms used for **cloud environments and on-premise infrastructure**.

The vulnerability management process followed a lifecycle approach consisting of:

- Discovery
- Assessment
- Prioritization
- Remediation coordination
- Verification

This ensured that vulnerabilities across the enterprise environment were continuously monitored and addressed in a structured manner.

---

### Vulnerability Discovery and Scan Management

Regular vulnerability scans were scheduled across multiple asset categories to ensure complete coverage of enterprise systems.

Different device categories had **different scan schedules and time windows** depending on operational impact and maintenance requirements. These included:

- Windows servers
- Linux servers
- Employee workstations
- Network infrastructure devices (firewalls, routers, load balancers)
- Public-facing systems
- Cloud infrastructure

After each scan cycle, the Tenable Nessus dashboard was reviewed to confirm:

- Whether the scan completed successfully
- If authentication worked correctly for agent-based scans
- Whether all assets were scanned as expected
- Whether any new vulnerabilities were discovered

If a scan failed or did not complete successfully, the issue was investigated and the scan was rescheduled to ensure full coverage.

---

### Vulnerability Assessment and Prioritisation

Once vulnerabilities were detected, they were analysed and prioritised based on several factors:

- Vulnerability severity score
- Exposure level of the asset (public vs internal)
- Business criticality of the system
- Threat intelligence indicating active exploitation

Critical vulnerabilities were prioritised for immediate remediation, while lower severity vulnerabilities were handled during the normal patching cycle.

The Tenable **Vulnerability Priority Rating (VPR)** was also considered when determining the urgency of remediation.

---

### Coordination with Remediation Teams

Once validated, vulnerabilities were communicated to the appropriate infrastructure teams responsible for remediation.

This typically required coordination with teams such as:

- Network operations team
- Server infrastructure teams
- Microsoft services team
- Platform engineering teams

Remediation actions could include:

- Applying vendor security patches
- Upgrading or replacing vulnerable software
- Modifying system configurations
- Removing unsupported or outdated software

Weekly vulnerability review meetings were conducted to track remediation progress and discuss newly identified high-risk vulnerabilities.

---

### Example: Microsoft Outlook Zero-Day Vulnerability

During one vulnerability monitoring cycle, a critical vulnerability related to **Microsoft Outlook** was identified through the Tenable Nessus dashboard.

The vulnerability was detected using **Nessus Plugin ID 187315**, associated with **CVE-2023-23397**, a Microsoft Outlook vulnerability that could allow attackers to exploit authentication mechanisms and potentially gain unauthorized access.

Due to its severity and the fact that it was being actively discussed as a zero-day vulnerability at the time, the issue was treated as a **Priority 1 (P1) vulnerability event**.

The investigation involved:

- Reviewing vulnerability scan results across enterprise assets
- Identifying systems potentially affected by the vulnerability
- Coordinating with the **Microsoft infrastructure team**
- Monitoring vendor advisories and security patch releases

After validation, it was confirmed that **no enterprise assets were vulnerable**, but the Microsoft team ensured that the appropriate patches were applied as part of the security update cycle.

This proactive monitoring ensured that the environment remained protected from a high-risk vulnerability even though no systems were directly impacted.

---

### Example: Firewall Vulnerability Identified via Nessus

During a routine vulnerability scan, Tenable Nessus identified a vulnerability affecting a **network firewall device**.

The vulnerability detection plugin indicated that the firewall firmware version contained known security weaknesses.

The investigation process included:

- Reviewing vulnerability details and affected devices in the Nessus dashboard
- Validating the vulnerability against the deployed firewall firmware
- Coordinating with the **network operations team**

The networking team performed remediation by upgrading the firewall firmware and applying the recommended configuration updates.

A follow-up vulnerability scan confirmed that the issue was successfully resolved and the vulnerability was no longer detected.

---

### Verification

Once remediation actions were completed, affected systems were rescanned to confirm that vulnerabilities had been successfully resolved.

If a vulnerability continued to appear in subsequent scans, further investigation was performed and additional remediation steps were coordinated with the relevant teams.

This verification step ensured that remediation actions were effective and that vulnerabilities were fully eliminated from the environment.

---

### Outcome

The vulnerability management process helped ensure that:

- Security weaknesses across enterprise systems were continuously monitored
- Critical vulnerabilities were prioritised and remediated quickly
- Cross-team coordination improved remediation efficiency
- Regular scanning and verification maintained a strong security posture across both cloud and on-premise infrastructure
