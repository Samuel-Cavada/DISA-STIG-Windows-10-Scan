<p align="center">
  <a href="https://github.com/Samuel-Cavada" target="_blank">
    <img src="https://img.shields.io/badge/Back_to_Main_Page-000000?style=for-the-badge&logo=github&logoColor=white" alt="Back to Main Page"/>
  </a>
</p>

<h1 align="center">Windows 10 DISA STIG Scan with Tenable</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Local%20VM-0078D4?style=for-the-badge&logo=microsoft&logoColor=white" alt="Cloud Platform" />
  <img src="https://img.shields.io/badge/OS-Windows%2010-0078D6?style=for-the-badge&logo=windows&logoColor=white" alt="OS" />
  <img src="https://img.shields.io/badge/Tool-Tenable.io-00B388?style=for-the-badge&logo=tenable&logoColor=white" alt="Tool" />
  <img src="https://img.shields.io/badge/Focus-Vulnerability%20Scanning-orange?style=for-the-badge" alt="Focus Area" />
</p>

---

## Project Objective
> This project demonstrates how to run a DISA STIG compliance scan on a Windows 10 virtual machine using Tenable.io. It simulates a real-world credentialed scan, reveals misconfigurations, and ensures federal security compliance standards are tested in a controlled environment.

---

## Tools & Technologies
- **Platform:** Local Virtual Machine
- **OS:** Windows 10
- **Tools:** Tenable.io
- **Languages/Scripts:** None

---

## Skills Gained / Focus Areas
- Configured and launched a DISA STIG Tenable.io scan
- Created vulnerabilities by misconfiguring local accounts
- Managed Windows Firewall settings and user group permissions
- Interpreted compliance scan results

---

## Environment Setup
> A Windows 10 virtual machine was used as the scan target. The system was intentionally misconfigured by enabling guest accounts, creating insecure admin credentials, and disabling firewall protections to simulate real-world vulnerabilities detectable through a DISA STIG compliance scan.

![Environment Setup](assets/images/setup.jpg)

---

## Walkthrough
1. [Step 1: Initial Setup](#step-1-initial-setup)
2. [Step 2: Configure the Environment](#step-2-configure-the-environment)
3. [Step 3: Execute the Scan](#step-3-execute-the-scan)
4. [Step 4: Analyze Results](#step-4-analyze-results)

---

### Step 1: Initial Setup
> Disabled the Windows Firewall to expose the host and created vulnerable accounts:
- Disabled the Windows Defender Firewall through 'wf.msc'. [See full provisioning steps ↗](https://github.com/Samuel-Cavada/Disable-the-Firewall-Windows) (Ctrl+Click to open in a new tab).
- Created a user named "administrator" with a weak password
- Enabled the Guest account and added it to the Administrators group

![Step 1](assets/images/step1.jpg)

---

### Step 2: Configure the Environment
> Misconfigurations to simulate vulnerable endpoints:
- Set "password never expires" and disabled password change prompts
- Guest account added to the admin group
- Firewall turned off for all profiles

![Step 2](assets/images/step2.jpg)

---

### Step 3: Execute the Scan
> Created and launched a DISA STIG scan template:
- Enabled options for registry, server service, and plugin discovery
- Added Windows credentials and DISA STIG compliance checks
- Launched the scan using an internal scanner with pre-configured credentials

![Step 3](assets/images/step3.jpg)

---

### Step 4: Analyze Results
> Interpreted compliance scan findings:
- Confirmed identification of policy violations and misconfigurations
- Reviewed detailed results on user accounts, firewall, and service settings

![Step 4](assets/images/step4.jpg)

---

## Outcomes and Lessons Learned
- **Technical Insight:** DISA STIG scans provide high-value insights on government-level compliance and highlight deeper system misconfigurations often missed in standard scans.
- **Configuration Skills:** Practiced detailed scan configuration and compliance plugin tuning within Tenable.io.
- **Troubleshooting:** Resolved scan credential issues by pre-setting credentials in the scan template instead of per scan.
- **Takeaway:** Using credentialed scans aligned with DISA STIG standards ensures accurate policy-level auditing crucial for government or DoD environments.

---

## References
- [Tenable.io Documentation](https://docs.tenable.com/)
- [DISA STIG for Windows 10](https://public.cyber.mil/stigs/)
- [Microsoft Defender Firewall Settings](https://learn.microsoft.com/en-us/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security)
