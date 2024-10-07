# SOC NSG Flow Logs and VM Log Collection Lab

![Screenshot 2024-10-07 153847](https://github.com/user-attachments/assets/3f2e2b48-af7d-4b84-893e-9d89849c1db3)



In this lab, I set up and configured logging for both Network Security Groups (NSGs) and virtual machines (VMs) within a SOC environment. I created an Azure Storage Account for NSG Flow Logs, enabled flow logs for the NSGs, and routed them to a centralized Log Analytics Workspace. Additionally, I configured Data Collection Rules (DCRs) for Windows and Linux VMs to capture key security events and syslog data. The lab demonstrates my ability to configure comprehensive cloud logging and monitoring, ensuring logs from VMs and NSGs are collected and analyzed in Microsoft Sentinel.




<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Microsoft Sentinel
- Log Analytic Workspace
- Network Security Groups


<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)
- Ubuntu 22

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1 - Create an Azure Storage Account (sacyberlab0x, name needs to be unique)
- Step 2 - Enable Flow logs for both both Network Security Groups (NSGs)
- Step 3 - Configure Data Collection Rules for our VMs within Microsoft Sentinel
- Step 4 - Go to Sentinel -> Your Log Analytics Instance -> Content Hub
- Step 5 - DCR-Windows
- Step 6 - DCR-Linux
- Step 7 - Check under VM -> Settings -> Extensions Applications for both the Windows and Linux VM and ensure the agent is installed with “Provisioning succeeded”
- Step 8 - Begin querying Log Analytics for logs from the VMs and NSGs; do not move on from this lab until you see logs from all three sources, or at least the linux/windows logs:






<h2>Deployment and Configuration Steps</h2>

- Create an Azure Storage Account (sacyberlab0x, name needs to be unique)
- MUST be in the same region as VMs
- This will be used to store the NSG Flow Logs which we are about to create
![Screenshot 2024-10-07 155130](https://github.com/user-attachments/assets/1a447da5-18cb-4dba-bbfd-8de67d40a758)

- Enable Flow logs for both both Network Security Groups (NSGs)
- Make sure to send to our Log Analytics Workspace
- If there is no storage account listed, it means it’s in a different region from your VMs, so you’ll need to create another storage account in the same region
![Screenshot 2024-10-07 160145](https://github.com/user-attachments/assets/3a774d56-0f95-41cd-9268-abb956f542c2)

- Configure Data Collection Rules for our VMs within Microsoft Sentinel
- Turn on VMs if they aren’t already on
- Go to Sentinel -> Your Log Analytics Instance -> Content Hub
- Search for “Windows Security Events” and Install it
![Screenshot 2024-10-07 161131](https://github.com/user-attachments/assets/28ec18ed-65bd-4979-8805-97e4225fa99b)

-DCR-Windows:
- Select appropriate VM
- Configure Windows Data Sources: Security (All)
![Screenshot 2024-10-07 162715](https://github.com/user-attachments/assets/eda953fa-90e3-42ed-960e-ab8234892876)

- Go to Sentinel -> Your Log Analytics Instance -> Content Hub
- Search for “Syslog” and Install it
![Screenshot 2024-10-07 163149](https://github.com/user-attachments/assets/227df4c8-b88a-48ad-a3de-c9d7a323c024)

- DCR-Linux
- Configure Linux Data Sources (Auth: Debug only)
- Linux-vm-logs
![Screenshot 2024-10-07 163658](https://github.com/user-attachments/assets/821ac11f-13d1-4d47-8ce8-2dbffd3ad634)

- Check under VM -> Settings -> Extensions Applications for both the Windows and Linux VM and ensure the agent is installed with “Provisioning succeeded”
![Screenshot 2024-10-07 164519](https://github.com/user-attachments/assets/2433649c-3fe2-42d7-acbe-207478cf4538)

- Begin querying Log Analytics for logs from the VMs and NSGs; do not move on from this lab until you see logs from all three sources, or at least the linux/windows logs:
- Syslog (linux):
- SecurityEvent (windows)
- AzureNetworkAnalytics_CL (Network Security Groups/NSGs)
![Screenshot 2024-10-07 165534](https://github.com/user-attachments/assets/f3af8045-760c-4c4b-8685-1a97f427c4a8)
![Screenshot 2024-10-07 165658](https://github.com/user-attachments/assets/ab52280c-77b7-461b-aac2-ba39531965db)
![Screenshot 2024-10-07 170700](https://github.com/user-attachments/assets/8e91283e-8c1b-464e-a1e2-8a31ed8a212c)



















