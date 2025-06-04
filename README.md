<p align="center">
  <a href="https://github.com/Samuel-Cavada" target="_blank">
    <img src="https://img.shields.io/badge/Back_to_Main_Page-000000?style=for-the-badge&logo=github&logoColor=white" alt="Back to Main Page"/>
  </a>
</p>

<!-- Mascots Section (optional)
<p align="center">
  <img src="https://github.com/user-attachments/assets/your-mascot-id.png" alt="PatchPal" width="100">
</p>
-->

<h1 align="center">Windows 10 VM Scan Using Custom Template (Tenable + DISA STIG)</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Azure-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white" alt="Azure" />
  <img src="https://img.shields.io/badge/OS-Windows%2010-0078D6?style=for-the-badge&logo=windows&logoColor=white" alt="Windows 10" />
  <img src="https://img.shields.io/badge/Tool-Tenable.io-00B388?style=for-the-badge&logo=tenable&logoColor=white" alt="Tenable.io" />
  <img src="https://img.shields.io/badge/Focus-Compliance%20Scanning-orange?style=for-the-badge" alt="Compliance Scanning" />
</p>

---

## Project Objective
This project demonstrates how to use a custom Tenable scan template to identify vulnerabilities and DISA STIG compliance issues on a Windows 10 virtual machine in Azure. The scan is configured to simulate risky misconfigurations and test Tenable’s compliance plugin effectiveness.

---

## Tools & Technologies
- Microsoft Azure – VM provisioning and NSG configuration
- Windows 10 – Target system for vulnerability assessment
- Tenable.io – Advanced Network Scan with DISA STIG compliance checks
- Remote Desktop Protocol (RDP) – VM access
- Command Prompt / Ping – Connectivity verification

---

## Skills Gained / Focus Areas
- Tenable.io scan template creation and customization
- Windows misconfiguration and vulnerability simulation
- DISA STIG compliance auditing
- Network Security Group (NSG) management in Azure
- Risk identification and remediation tracking

---

## Environment Setup
- Provision a Windows 10 VM in Microsoft Azure.
- Disable Windows Firewall.
- Fully open the NSG to allow all inbound traffic (for testing purposes only).
- Create and configure accounts to intentionally introduce vulnerabilities.

---

## Walkthrough

### Step 1: Create a Windows 10 VM
Provisioned a Windows 10 VM from the Azure Marketplace. [See full provisioning steps ↗](https://github.com/Samuel-Cavada/Azure-VM-Build) (Ctrl+Click to open in a new tab).


---

### Step 2: Simulate Vulnerabilities
Introduce intentionally insecure configurations.

- Disabled the Windows Defender Firewall through 'wf.msc'. [See full steps ↗](https://github.com/Samuel-Cavada/Disable-the-Firewall-Windows) (Ctrl+Click to open in a new tab).

- Create a new local admin account:
  - Username: `administrator`
  - Password: `password` (no expiration)
- Enable and promote the `Guest` account to the Administrators group.

---

### Step 3: Open Network Access
Ensure all external connections are permitted for scanning.

- Edit NSG inbound rules to allow all traffic.
- From your local machine, test:
  ```bash
  ping [Your_VM_Public_IP]
  ```

---

### Step 4: Create a Scan Template in Tenable.io
Configure an Advanced Network Scan template.

**Basic Tab**
- Name: `Win-10-compliance-test`
- Start Remote Registry service during scan [✔]
- Enable administrative shares during scan [✔]
- Start Server service during scan [✔]

**Discovery Tab**
- Ping remote host [✔]
- Use fast network discovery [✔]
- Network Port Scanners: TCP [✔]

**Assessment Tab**
- Perform thorough tests [✔]
- Only use user-provided credentials [ ] (unchecked)

**Credentials Tab**
- Use the admin account created earlier (`administrator / password`)

**Compliance Tab**
- Add DISA Microsoft Windows 10 STIG audit or similar

---

### Step 5: Launch a Scan with Your Template
Create a new scan using the saved template.

- Use the custom template
- Enter your VM's public IP
- Input your admin credentials
- Launch the scan

---

### Step 6: Review Results
Analyze output in the following sections:

- Vulnerabilities by Plugin  
- Compliance Findings  
- Suggested Remediations  

---

### Step 7: Cleanup
After verifying the results:

- Delete the Azure VM (double check it’s the correct one)

---

## Outcomes and Lessons Learned
- Learned to simulate real-world vulnerabilities through misconfigurations
- Built a reusable custom scan template in Tenable.io
- Identified DISA STIG violations and security flaws effectively
- Practiced secure provisioning and teardown of Azure resources
- Understood the impact of authentication and service access on vulnerability visibility

---

## References
- [Tenable Advanced Scan Guide](https://docs.tenable.com/tenableio/Content/Scans/CreateScan.htm)
- [DISA Windows 10 STIG](https://public.cyber.mil/stigs/downloads/)
- [Azure NSG Rules](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview)
