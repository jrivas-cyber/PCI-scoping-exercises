# Scoping your CDE

---

Scoping can be defined as the identification and tracking of people, processes, and technologies that directly interact with account data or could impact the security of account data in your environment.

Key items of consider:
- Scoping exercises hould be performed on an annual basis (at minimum)
- Should include validation of people, processes and technologies that handle account data in your cardholder data environment (CDE)
- Should include the identification of current and new payment channels

---

To identify systems that would be in-scope vs out-of-scope, there are two questions to consider:
1. Does this system 
<img width="1089" height="760" alt="Screenshot 2026-01-09 063146" src="https://github.com/user-attachments/assets/21d06ebc-c5f2-4568-97ac-e3b0db28ca40" />

_**Inception State:**_ organization has no existing policy or vulnerability management practices in place.

_**Completion State:**_ formal policies and standards are enacted, stakeholders are bought-in, and a full cycle of organization-wide vulnerability remediation is successfully completed.

---

<img width="1000" alt="image" src="https://github.com/user-attachments/assets/cfc5dbcf-3fcb-4a71-9c13-2a49f8bab3e6">

# Technology Utilized
- Tenable (enterprise vulnerability management platform)
- Azure Virtual Machines (Nessus scan engine + scan targets)
- PowerShell & BASH (remediation scripts)

---


# Table of Contents

- [Vulnerability Management Policy Draft Creation](#step-1-vulnerability-management-policy-draft-creation)
- [Meeting: Policy Buy-In with Stakeholders](#step-2-meeting-policy-buy-in-with-stakeholders)
- [Policy Finalization and Senior Leadership Sign-Off](#step-3-policy-finalization-and-senior-leadership-sign-off)
- [Meeting: Initial Scan Permission with Server Team](#step-4-meeting-initial-scan-permission-with-server-team)
- [Initial Scan of Server Team Assets](#step-5-initial-scan-of-server-team-assets)
- [Vulnerability Assessment and Prioritization](#step-6-vulnerability-assessment-and-prioritization)
- [Distributing Remediations to Remediation Teams](#step-7-distributing-remediations-to-remediation-teams)
- [Meeting: Post-Initial Discovery Scan with Server Team](#step-8-meeting-post-initial-discovery-scan-with-server-team)
- [CAB Meeting: Implementing Remediations](#step-9-cab-meeting-implementing-remediations)
- [Remediation Round 1: Outdated Wireshark Removal](#remediation-round-1-outdated-wireshark-removal)
- [Remediation Round 2: Insecure Protocols and Ciphers](#remediation-round-2-insecure-protocols-and-ciphers)
- [Remediation Round 3: Guest Account Group Membership](#remediation-round-3-guest-account-group-membership)
- [Remediation Round 4: Windows OS Updates](#remediation-round-4-windows-os-updates)
- [First Cycle Remediation Effort Summary](#first-cycle-remediation-effort-summary)

---

### Step 1) Vulnerability Management Policy Draft Creation

We focus on drafting a Vulnerability Management Policy as a starting point for stakeholder engagement. The initial draft outlines scope, responsibilities, and remediation timelines using industry standards. The policy may be adjusted based on feedback from relevant departments to ensure practical implementation before final approval by upper management.  

[Draft Policy](https://docs.google.com/document/d/1NIJcHuu7JS4RkvU-Sj8XanXyNtd-UBqU11MaUamSW0E/edit?usp=sharing)

---

### Step 2) Meeting: Policy Buy-In with Stakeholders

In this phase, we meet with the server team to introduce the policy draft and assess their capability to meet remediation timelines. Feedback leads to adjustments, like extending the critical remediation window, ensuring collaborative implementation.

🟦 General Check-in
- Introductions with server team.

📄 Policy Draft Feedback
- Review the policy draft and discuss scope.
- Open discussion on any concerns the server team may have about the policy (i.e., remediation timelines too aggressive given current staffing levels).

🔄 Proposed Adjustment  
- Discuss adjustments to allow for compromise.
- Adjust remediation timelines as needed (consider asset criticality and vulnerability severity).

⏳ Onboarding Flexibility  
- Allow for some leeway during the initial months to adapt to the new process.
- Determine start date based on onboarding discussions.

✅ Collaboration & Appreciation  
- Stakeholders will appreciate being included in the decision-making process, which makes them feel involved.
- Emphasize that vulnerability management is a team effort and requires collaboration.

👋 Closing  
- Express appreciation for the meeting and wrap things up on a friendly note.

---

### Step 3) Policy Finalization and Senior Leadership Sign-Off

After gathering feedback from the server team, the policy is revised, deciding on appropriate remediation timelines. With final approval from upper management, the policy now guides the program, ensuring compliance and reference for pushback resolution.  

[Finalized Policy](https://docs.google.com/document/d/1EXuSNtwU5OwCU5paVAHqEYHX2I8VUxWZjJ3tc6AnnRc/edit?usp=sharing)

<div style="text-align: center;">
    <img src="https://github.com/user-attachments/assets/9afcdbc1-0493-4af2-9287-1cb9b8f59b40" alt="image" width="400">
</div>

---

### Step 4) Meeting: Initial Scan Permission with Server Team

The cyber team collaborates with the server team to initiate scheduled credential scans. A compromise is reached to scan a single server first, monitoring resource impact, and using just-in-time AD credentials for secure, controlled access.

🟢 Kick-off & Context  
- Inform server team that you are ready to start scheduled credentialed scans now that the policy is in place.
- Review scan cadence outlined in policy.

🖥️ Scan Details  
- Review scan duration and scope of scan (# of assets being scanned).
- Remind server team that admin credentials are required for in-depth checks.

⚠️ Concerns Raised  
- Review and discuss possible concerns (i.e., resource utilization, potential server impact, security risk with providing admin credentials, etc.)

🔍 Provide Clarification  
- Explain how the scan works: scan sends traffic to check for vulnerabilities (i.e., out-of-date software, insecure protocols); credentials are needed for authenticated scans to access registry data and detect deeper issues; scans will not take servers offline.

✅ Agreement & Risk Mitigation  
- Agreement to start by scanning just one server first to monitor performance and resource impact.
- Suggestion to use AD credentials with a just-in-time access approach.
- Have the IAM team create the AD account for you ahead of time.
- Enable the account only during scans.
- Disable or deprovision upon scan completion.

📌 Next Steps  
- Server team agrees and will ask IAM team to begin automating the account provisioning process.
- IAM team will follow up once credentials are set up.

---

### Step 5) Initial Scan of Server Team Assets

In this phase, an insecure Windows Server is provisioned to simulate the server team's environment. After creating vulnerabilities, an authenticated scan is performed, and results are exported for future remediation.  

![image](https://github.com/user-attachments/assets/78e52eaf-e38b-4f1f-ae60-4831b7b15c9a)

[Scan 1 - Initial Scan](https://drive.google.com/file/d/1JUsP_pGbzpN9YhSVA8BwgEecgvfxRn7x/view?usp=sharing)




---

### Step 6) Vulnerability Assessment and Prioritization

We assessed vulnerabilities and established a remediation prioritization strategy based on ease of remediation and impact. The following priorities were set:

1. Third Party Software Removal (Wireshark)
2. Windows OS Secure Configuration (Protocols & Ciphers)
3. Windows OS Secure Configuration (Guest Account Group Membership)
4. Windows OS Updates

---

### Step 7) Distributing Remediations to Remediation Teams

We created remediation scripts and pulled scan results, then sent them to the server team to address key vulnerabilities. This streamlined their efforts and prepared them for a follow-up review.  

<img width="635" alt="image" src="https://github.com/user-attachments/assets/bbf9478f-e1d1-4898-846e-b510ec8c6f72">

[Remediation Email](https://github.com/jrivas-cyber/vulnerability-management-program/blob/main/communication/powershell-remediation-email.md)

---

### Step 8) Meeting: Post-Initial Discovery Scan with Server Team

Server team reviewed the scan results, identifying outdated software, insecure accounts, and deprecated protocols. The remediation packages were prepared for submission to the Change Advisory Board (CAB). 

🔍 Scan Summary  
- The scan completed successfully with no outages or resource overutilization.
- The scan was mostly undetectable, except for some open connections.
- Ongoing monitoring will continue, but no performance issues are expected.

🛡️ Vulnerability Findings  
- Outdated Wireshark installations found across target systems.
- The local guest account on servers is incorrectly a member of the local admin group.
- Presence of deprecated TLS protocols (1.0 & 1.1) and medium-strength cipher suites.
- Some vulnerabilities (e.g. MS Edge Chromium) may be resolved via Windows Updates.
- Self-signed certificates noted, but not considered a risk.

🛠️ Remediation Plan  
- Remove outdated Wireshark installations.
- Remove local guest account from the local admin group.
- Disable deprecated cipher suites and TLS protocols.
- No known issues anticipated with remediation steps.
- All changes will be submitted to the CAB team prior to implementation.

🧰 Tools and Support  
- A patch management system is in place, so Windows updates are expected to resolve certain issues automatically by next week.
- Remediation packages will be prepared to streamline the fix process.
- Uniform vulnerabilities across servers will make remediation more efficient.

✅ Next Steps  
- One party will begin remediation package development.
- Further research on remediation will be done.
- Follow-up will occur before the next CAB meeting.

---

### Step 9) CAB Meeting: Implementing Remediations

The CAB team reviewed and approved the plan to remove insecure protocols and cipher suites. The plan included a rollback script and a tiered deployment approach.  

🛠️ Remediation Overview  
- Two main vulnerability remediations for the server team: removal of insecure protocols & removal of insecure cipher suites

👥 Team Responsibilities  
- Risk Department leads the technical solution discussion.
- Infrastructure Team supports implementation discussion.

🔧 Technical Approach  
- Insecure protocols and cipher suites can still be used if enabled in the system, even if they’re deprecated.
- These are controlled via Windows registry settings.
- A PowerShell script was developed to disable insecure protocols/ciphers and enable secure, current standards.

🔁 Rollback Plan:
A tiered deployment will be used:
- Pilot group (small set of systems)
- Pre-production
- Full production rollout
- An automated rollback script is in place to restore original registry settings if issues occur.

✅ Outcome & Confidence  
- The fix is straightforward and low-risk (just registry updates).
- No major concerns raised by the team.
- The meeting concludes with no further questions.

---
### Step 10 ) Remediation Effort

#### Remediation Round 1: Outdated Wireshark Removal

The server team used a PowerShell script created by the cyber team to remove outdated Wireshark. A follow-up scan verified successful remediation.  
[Wireshark Removal Script](https://github.com/jrivas-cyber/vulnerability-management-program/blob/main/powershell-scripts/remediate-wireshark-uninstall.ps1)  

![image](https://github.com/user-attachments/assets/ce705278-e4ba-42e6-b718-7d54a38bc29d)

[Scan 2 - Third Party Software Removal](https://drive.google.com/file/d/1_oGQj16AiZgsLB7CGT_I94eAmxFHe8XL/view?usp=sharing)


#### Remediation Round 2: Insecure Protocols and Ciphers

The server team used PowerShell scripts created by the cyber team to remediate insecure protocols and cipher suites. A follow-up scan verified successful remediation, and results were saved for reference.  
[Insecure Protocols Remediation](https://github.com/jrivas-cyber/vulnerability-management-program/blob/main/powershell-scripts/remediate-insecure-protocols.ps1) 
  
[Insecure Ciphers Remediation](https://github.com/jrivas-cyber/vulnerability-management-program/blob/main/powershell-scripts/remediate-insecure-cipher-suites.ps1)

![image](https://github.com/user-attachments/assets/3160d617-c492-43fe-8f32-971ba2500b45)

[Scan 3 - Ciphersuites and Protocols](https://drive.google.com/file/d/1yj5jAPVQ3h8jJnw5xoOa1fCNGJ0tRoxK/view?usp=sharing)


#### Remediation Round 3: Guest Account Group Membership

The server team removed the guest account from the admin group. A follow-up scan confirmed remediation, and results were exported for comparison.  
[Guest Account Group Membership Remediation](https://github.com/jrivas-cyber/vulnerability-management-program/blob/main/powershell-scripts/remediate-guest-local-admins.ps1)  

![image](https://github.com/user-attachments/assets/0889b57a-6144-4418-a371-c9adb0e4f5ba)

[Scan 4 - Guest Account Group Removal](https://drive.google.com/file/d/1N7-RlUvyArSpLa1WlagMQHnLUFGEgwxt/view?usp=sharing)


#### Remediation Round 4: Windows OS Updates

Windows updates were re-enabled and applied until the system was fully up to date. A follow-up scan verified the changes.  

![image](https://github.com/user-attachments/assets/6feebc0c-9efe-4dbd-8a19-9406b3800b4c)

[Scan 5 - Post Windows Updates](https://drive.google.com/file/d/16-XbJBG33GoFv0Lm--NuMlvQVBn7Bp9R/view?usp=sharing)

---

### First Cycle Remediation Effort Summary

The remediation process reduced overall vulnerabilities by 76% (from 29 down to 7). All critical vulnerabilities were resolved by the second scan, and high vulnerabilities reduced by 89%. Mediums were reduced by 71%. In an actual production environment, asset criticality would further guide future remediation efforts.  

![image](https://github.com/user-attachments/assets/83facde2-a732-4782-b789-2abfc8ddf5d9)

[Remediation Data](https://docs.google.com/spreadsheets/d/1HndcP28THgzvhUwi_IykTSRy4fcNGFAb0gr4jXUoGhU/edit?usp=sharing)

---

### On-going Vulnerability Management (Maintenance Mode)

After completing the initial remediation cycle, the vulnerability management program transitions into **Maintenance Mode**. This phase ensures that vulnerabilities continue to be managed proactively, keeping systems secure over time. Regular scans, continuous monitoring, and timely remediation are crucial components of this phase. (See [finalized policy](https://docs.google.com/document/d/1EXuSNtwU5OwCU5paVAHqEYHX2I8VUxWZjJ3tc6AnnRc/edit?usp=sharing) for scanning and remediation cadence requirements.)

Key activities in Maintenance Mode include:
- **Scheduled Vulnerability Scans**: Perform regular scans (e.g., weekly or monthly) to detect new vulnerabilities as systems evolve.
- **Patch Management**: Continuously apply security patches and updates, ensuring no critical vulnerabilities remain unpatched.
- **Remediation Follow-ups**: Address newly identified vulnerabilities promptly, prioritizing based on risk and impact.
- **Policy Review and Updates**: Periodically review the Vulnerability Management Policy to ensure it aligns with the latest security best practices and organizational needs.
- **Audit and Compliance**: Conduct internal audits to ensure compliance with the vulnerability management policy and external regulations.
- **Ongoing Communication with Stakeholders**: Maintain open communication with stakeholders for remediation, ensuring efficient coordination.

By maintaining an active vulnerability management process, organizations can stay ahead of emerging threats and ensure long-term security resilience.
