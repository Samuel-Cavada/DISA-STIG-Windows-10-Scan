<p align="center">
  <a href="https://github.com/Samuel-Cavada" target="_blank">
    <img src="https://img.shields.io/badge/Back_to_Main_Page-000000?style=for-the-badge&logo=github&logoColor=white" alt="Back to Main Page"/>
  </a>
</p>



<h1 align="center">Windows Vulnerability Scanning: Authenticated vs. Unauthenticated</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Azure-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white" alt="Azure" />
  <img src="https://img.shields.io/badge/OS-Windows%2010-0078D6?style=for-the-badge&logo=windows&logoColor=white" alt="Windows 10" />
  <img src="https://img.shields.io/badge/Tool-Tenable.io-00B388?style=for-the-badge&logo=tenable&logoColor=white" alt="Tenable.io" />
  <img src="https://img.shields.io/badge/Focus-Vulnerability%20Scanning-orange?style=for-the-badge" alt="Vulnerability Scanning" />
</p>


## Project Objective
This project demonstrates the difference between authenticated and unauthenticated vulnerability scanning on a Windows 10 virtual machine. The goal was to highlight how access level impacts the visibility of security vulnerabilities, emphasizing the importance of credentialed scans in cybersecurity assessments.

## Tools & Technologies
- Microsoft Azure (VM deployment)
- Windows 10 (Virtual Machine)
- Windows Defender Firewall (Configuration management)
- Tenable Vulnerability Scanner (Cloud-based scanning)

## Skills Gained / Focus Areas
- Vulnerability scanning methodologies
- Windows Firewall configuration and management
- Azure Network Security Group (NSG) configuration
- Conducting authenticated vs. unauthenticated scans
- Security assessment and report analysis

## Environment Setup
The lab environment was built using Microsoft Azure.  
A Windows 10 VM was configured with modified firewall and network security group settings to allow external scanning activities, simulating real-world scenarios for vulnerability assessments.

## Walkthrough

### Setup

#### Step 1: Create a Windows 10 Virtual Machine
Deploy a Windows 10 VM from the Azure Marketplace.

#### Step 2: Log in to the VM
Access the Windows VM via Remote Desktop Protocol (RDP).

#### Step 3: Open Windows Firewall Settings
- Open the Run box and type `wf.msc`, then press Enter.
- Navigate to **Windows Defender Firewall Properties**.

#### Step 4: Disable the Firewall
- In the **Domain Profile**, **Private Profile**, and **Public Profile** tabs:
  - Set the firewall state to **Off**.
  - Click **Apply**.

#### Step 5: Update Network Security Group (NSG)
- In Azure, navigate to the VM's Networking settings.
- Locate the **Network Security Group** (NSG) attached to the VM's virtual network or subnet.
- Under **Inbound Security Rules**, create a new rule:
  - Allow **All Incoming Ports**.
  - Assign a lower priority number to make the rule take effect immediately.
  - Provide a clear name for the rule.

#### Step 6: Verify Connectivity
- Open Command Prompt (cmd).
- Ping the VM’s Public IP Address to verify accessibility.

### Unauthenticated Vulnerability Scan

#### Step 7: Set Up a Vulnerability Scan in Tenable
- Log in to Tenable.io.
- Navigate to **Scans** and click **Create New Scan**.
- Choose **Basic Network Scan**.

#### Step 8: Configure the Scan
- **Basic Tab**:
  - Name the scan appropriately.
  - Select the scanner type as **External Scanner** (cloud-based).
  - Target the VM’s Public IP Address.
- **Discovery Tab**:
  - Set **Scan Type** to **Custom**.
  - Enable **Ping Remote Host**.
  - Use **Fast Network Discovery**.
- **Credentials Tab**:
  - Leave credentials blank for an unauthenticated scan.

#### Step 9: Run the Scan
- Start the scan.
- After completion, export the results as an **Executive Report**.

### Authenticated Vulnerability Scan

#### Step 10: Configure Authenticated Scan
- Edit the previous scan or create a new one.
- In the **Credentials Tab**, add valid administrator login credentials for the Windows VM.

#### Step 11: Run the Authenticated Scan
- Start the scan using the newly added credentials.

### Analyze and Compare Results

#### Step 12: Review Findings
- Compare the unauthenticated and authenticated scan reports.
- Document key differences:
  - Number of vulnerabilities detected
  - Severity ratings
  - Additional system information revealed during authenticated scans

---

## Outcomes and Lessons Learned
- Authenticated scans provide significantly deeper insights into system vulnerabilities.
- Unauthenticated scans, while useful, often miss critical internal vulnerabilities.
- Gained practical experience in configuring firewall settings, securing Azure environments, and setting up vulnerability scans with and without credentials.
- Understood the value of credentialed access for thorough security assessments.
